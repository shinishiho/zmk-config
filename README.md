# My Corne 5 columns layout config
## TL;DR - Firmware only
1. Clone my repo.
2. Check out the [ZMK documentation](https://zmk.dev/docs) or [Quick Start](#firmware---quick-start).
3. Make some changes to the [keymap file](./config/corne.keymap) and [config file](./config/corne.conf).
4. Wait a few minute to build the firmware and it should be available at the release section.
## Introduction
As usual, everyone including I started the journey with the computers on the "default" keyboard. It
- Is staggered
- Is in QWERTY layout (almost, assuming English language)
- Has a lot of keys

After some times, I became pretty much familiar with it (and so does everyone else). My typing speed is not so great, but is usable on those keyboards. My best record on Monkeytype in 15-sec was around 80-ish WPM.

Before, I've always heard about different keyboard layouts, different keyboard types, etc. but I didn't care too much about them. I'd always thought why would I need to make a change on the keyboard that I was so used to? I built my first mechanical keyboard, which was great with 68 keys and Akko Sakura switches. It sounded nice, felt amazing when typing with it, and I thought that would be the last thing to do with a keyboard.

But some day, I came across some videos on YouTube about the problem of QWERTY and about the alternative layout, something like that, again. And I realized, there have always been some problems with my keyboard. I dig deeper and deeper, until I came to the state that I am in right now: ergonomic matrix keyboard and Colemak DH layout.
## Parts
This is the 5 column, 36 keys Corne wireless keyboard. Here is the list of part I used:
- The board (ordered on [Typeractive](typeractive.xyz))
- NRF52840 Pro Micro (2 pcs, ordered on Shopee)
- Kailh Choc v1 Red Switches (1pack-35pcs, ordered on Lazada)
- A blue switch for the space key for no reason.
- 400mAh LiPo batt (2 pcs)
- 3D printed keycaps [(not my design, credit to the OG)]()
- Some rubber pieces glued on the back to avoid slipping

Sadly, I didn't have any intention with the aesthetic aspect, since I have no screen, no light, no case and just blank keycaps. You can refer to ZMK documentation [here](https://zmk.dev/docs/) to add other functionalities. I just need a keyboard that really works. So, even though the documentation on [Typeractive](docs.typeractive.xyz) recommended a 110mAh (to place a screen on top), I place my batteries on top of the controllers instead and enjoy a much longer battery life.
## Assemble
One thing I love about the board from Typeractive is that it comes with diodes and hotswap sockets pre-soldered, so the only thing left to do is to solder the controller to the board. Which would be easy enough, I guess. I spent two weeks to solder 2 controllers into the boards thanks to my skill issue.
Besides that, the batteries is placed on top, the switches and keycaps is easily assembled.
## Firmware - Quick Start
My current layout is [Colemak DH Matrix.](https://colemakmods.github.io/mod-dh/keyboards.html#matrix-keyboards)
1. First layer
	- Toggleable home row mod in GUI - Alt - Shift - Ctrl order (and mirrored on the right side)
	- 6 thumb keys: `LOWER | Del | Enter || Space | Backspace | RAISE`
	- Mods on the `LOWER` key:

| Action | Tap once | Hold                 |
|--------|----------|----------------------|
| Output | TAB key  | Activate LOWER layer |
- Mods on the `RAISE` key:
 
| Action | Tap once | Tap twice           | Hold                 |
|--------|----------|---------------------|----------------------|
| Output | ESC key  | Toggle home row mod | Activate RAISE layer |

2. Raise layer
	- First row: Num row 1-9 and 0 with Auto Shift. (more on that below)
	- Second row: ``~ | AS(-) | AS(=) | { | [ | ] | } | AS(') | AS(\) | ` `` (AS stands for Auto Shift)
	- Third row: Function keys from F1 to F10
	- F11 and F12 are in two middle thumb keys
3. Lower layer
	- Two middle top row keys: `OUT_USB` and `OUT_BLE`
	- Second row: Select Bluetooth profile 1 to 5 + Vim navigation + Bluetooth clear current profile
	- `sys_reset | bootloader || bootloader | sys_reset`
## Firmware - More Details
- Every other position that is not mentioned in the layers is `transparent`, which means hitting those keys will do the action those of the last layer.
- Home row mod: using `mod_tap`, `tap-preferred` flavor.
- Auto Shift: quick tap produces the normal character, hold for a short period before release produces the shifted character.
- Raise key `tap_dance_mod_tap`: tap dance for toggling the home row mod layer, mixed with layer tap.
- `OUT_USB` and `OUT_BLE`: decide whether to send signal via USB when connected, or keep Bluetooth connection. More info [here.](https://zmk.dev/docs/behaviors/outputs)
- `sys_reset` and `bootloader`: quickly reset or jump into bootloader mode to flash new firmware. More info [here.](https://zmk.dev/docs/behaviors/reset)
- Bluetooth profile management: the keyboard will always connect to paired devices. Select profile numbered 1 to 5 to switch focus to that device or pair new one if the profile is empty. Hit the clear profile key to forget the device in the current profile. More info [here.](https://zmk.dev/docs/behaviors/bluetooth)
## Gallery
![Image 1](./img1.png)
![Image 2](./img2.png)
