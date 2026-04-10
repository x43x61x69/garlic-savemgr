# Garlic SaveMgr for PS5

PS5 save decrypt/encrypt/browse with embedded web UI.

## Usage

1. Send `garlic-savemgr.elf` to elfldr
2. Open `http://<ps5-ip>:8082` in your browser on your PC
3. Drag and drop files into the browse tab to add/replace files

## Building

Requires the [PS5 Payload SDK](https://github.com/ps5-payload-dev/sdk).

```sh
make PS5_PAYLOAD_SDK=/path/to/ps5-payload-sdk
```

#### Building on macOS 

For macOS, you need to install `gnu-sed` as the system built-in `sed` works differently than GNU version:

```sh
brew install gnu-sed
```

After installing `gnu-sed`, compile with the following commands (you should already have `llvm-config` installed during the SDK setup):

```sh
make PS5_PAYLOAD_SDK=/opt/ps5-payload-sdk LLVM_CONFIG=/opt/homebrew/opt/llvm@18/bin/llvm-config PATH="$HOMEBREW_PREFIX/opt/gnu-sed/libexec/gnubin:$PATH"
```

If there are errors regarding `src_ui_html`, replace the

```
unsigned char src__ui_tmp_html[]
```

to

```
unsigned char src_ui_html[]
```

and

```
unsigned int src__ui_tmp_html_len
```

to

```
unsigned int src_ui_html_len
```