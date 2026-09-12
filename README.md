# Corne-ish Zen V2 Custom Configuration

![Corne-ish Zen Logo](img/Zen_R3_sticker.png)

This is a custom configuration for the Corne-ish Zen V2 low profile wireless mechanical keyboard. It builds against current ZMK from the `zmkfirmware/zmk` repository and uses GitHub Actions, so a local ZMK toolchain is not required.

If you are looking to dig deeper into ZMK and develop new functionality, it is recommended to follow the steps of installing ZMK as found on the official ZMK documentation site (linked below).

V2 PCBs were only used in the 3rd GB round (R3). To confirm which version you need, remove the bottom from the keyboard and look beside the Corne-ish Zen logo for a version number. Group Buy rounds 1 and 2 have V1 PCBs and R3 has V2 PCBs. (Also V2 PCBs have white power switches... V1 PCBs have black ones.)

## Resources

- The [official ZMK Firmware GitHub](https://github.com/zmkfirmware/zmk) repository. View the keymaps for other boards and shields as a starting point for your keymap.
- The [official ZMK Documentation](https://zmk.dev/docs) web site. Find the answers to many of your questions about ZMK Firmware.
- The [official ZMK Discord Server](https://discord.gg/8cfMkQksSB). Instant conversations with other ZMK developers and users. Great technical resource!

## Instructions

1. Edit `config/corneish_zen.keymap` to suit your needs.
2. Commit and push your changes to GitHub. GitHub Actions will build the firmware.
3. Download the `firmware` artifact from the completed **Build** workflow run.

### ZMK Studio

The left/central firmware is built with ZMK Studio support over USB. After flashing it, connect the left half to your Mac and open the ZMK Studio app or [zmk.studio](https://zmk.studio/).

The keymap has three layers:

- `QWERTY`: the normal typing layer.
- `CODE`: hold the Space thumb key for numbers and programming symbols. Tapping it still sends Space.
- `NAV/SYS`: hold the Escape thumb key for navigation, Divvy shortcuts, screenshots, media, Bluetooth selection, brightness, and Studio access. Tapping it still sends Escape.

To unlock Studio, hold the Escape thumb key to enter `NAV/SYS`, then tap the `V` key on the left half's bottom row. Studio changes are runtime changes stored on the keyboard; the checked-in keymap remains the build-time baseline.

The `NAV/SYS` screenshot shortcuts remain on the left half's bottom row. The leftmost key sends macOS `Control+Shift+Command+3` and the next key sends `Control+Shift+Command+4`, which copy the full screen or a selection to the clipboard.

The right side of `NAV/SYS` sends Divvy's global shortcuts: `Ctrl+1`, `Ctrl+2`, `Ctrl+3`, `Ctrl+4`, `Ctrl+6`, `Ctrl+7`, and `Ctrl+8`. The `Ctrl+2`/`Ctrl+3` pair and `Ctrl+6`/`Ctrl+7`/`Ctrl+8` group are kept physically close, while the arrow cluster remains available.

On the base layer, tap the rightmost bottom key for `"` and hold it for Right Shift. Apostrophe remains on the home row above it.

## Firmware Files

To locate your firmware files...

1. In GitHub, open **Actions**, select **Build**, and open the workflow run you want.
2. Download the `firmware` artifact and extract the two `.uf2` files. Use the file whose name identifies the left/central half for the left half, and the right-named file for the right half.
3. Connect one half by USB and double-tap its reset button. A bootloader drive will appear.
4. Drag the matching `.uf2` file onto that drive. The keyboard will reboot when flashing finishes.
5. Repeat for the other half with its matching file.

Flash the left/central file first when upgrading to this Studio-enabled build. A normal firmware update preserves Bluetooth pairing/settings; use a settings-reset firmware only if the halves actually fail to reconnect afterward.

Your keyboard is now ready to use.
