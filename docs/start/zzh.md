# Quick Start for Open Source Home Automation Use

This page provides a 1-page overview of what you'll need to do to set up your stick to be used with the great collection of open-source home automation software.


## Step 1: Plug your stick in, install drivers if needed

zzh, zzhp and zzhp-lite all share the same common architecture:

![Radio sticks Block Diagram](/_assets/radio-sticks-block.png)

First step in getting your stick working is to ensure that your computer, server or Raspberry Pi recognises the device plugged in (specifically, the "USB to Serial Converter" chip) and installs the drivers needed. In most cases, you will not need to install drivers as most operating systems will take care of this for you but if needed, instructions for driver installation can be found [here](/drivers/).

Each stick is shipped with a test firmware that blinks the on-board LED, on and off continously. This is a "sanity check", to show that the device has survived its journey to you but it does not mean that it is ready for use. You will need to flash the correct firmware, once you've made sure that the stick is recognised by your operating system and drivers installed.


## Step 2: Download the correct firmware for your stick

Good news: As long as you use the correct firmware for your stick, you do not need an external debugger/programmer as the chips used have a built-in bootloader (BSL)! 

<p class="warn">⚠️ <b>WARNING:</b> It is crucial that you download the correct firmware for your stick as using the wrong firmware will disable the BSL and you will need an external debugger / programmer to flash your stick again. Instructions for that can be found <a href="/advanced/flash-jtag/">here</a>.</p>

There are two ways you can use your radio stick, either as a **coordinator** or a **router**.

**Coordinator:** This is the firmware you need if you're going to be using your stick with zigbee2mqtt, ZHA (Home Assistant) or any other ZNP-firmware-compliant software.  

You can find the coordinator firmware downloads under [`coordinator/Z-Stack_3.x.0/bin`](https://github.com/Koenkk/Z-Stack-firmware/tree/master/coordinator/Z-Stack_3.x.0/bin) in the [Z-Stack-firmware repository](https://github.com/Koenkk/Z-Stack-firmware). Pick the latest release available for your stick that matches the following template:

| Stick | Coordinator Firmware |
|--|--|
| zzh | CC2652R_coordinator_(YYYYMMDD) |
| zzhp, zzhp-lite and zoe2 | CC1352P2_CC2652P_other_coordinator_(YYYYMMDD) |


**Router:** If you're looking to extend the range of your network, flash your stick with the router firmware and plug it into a power source somewhere central in your home for stand-alone operation. Refer to the [README of the router firmware](https://github.com/Koenkk/Z-Stack-firmware/blob/master/router/Z-Stack_3.x.0/bin/README.md) for setup instructions.
 
You can find the router firmware downloads under [`router/Z-Stack_3.x.0/bin`](https://github.com/Koenkk/Z-Stack-firmware/tree/master/router/Z-Stack_3.x.0/bin) in the [Z-Stack-firmware repository](https://github.com/Koenkk/Z-Stack-firmware). Pick the latest release available for your stick that matches the following template:

| Stick | Router Firmware |
|--|--|
| zzh | CC2652R_router_(YYYYMMDD) |
| zzhp, zzhp-lite and zoe2 | CC1352P2_CC2652P_other_router_(YYYYMMDD) |


## Step 3: Flash the firmware on your stick

With the firmware of your choice downloaded and unzipped, you should end up with a single .hex file that will need to be flashed to your stick. Two options for that:

  - The beginner friendly, Windows-only option: [Flash firmware using TI's Flash Programmer 2](/flash/flash-ti-flash-prog/)
  - If you're comfortable running Python scripts, cross-platform option: [Flash firmware using cc2538-bsl](/flash/flash-cc-bsl/)

<p class="info">ℹ️ Please note that if you are a zigpy/ZHA user, you might want to take a backup of your NVRAM data before updating your stick. Information on this can be found on the <a href="https://github.com/zigpy/zigpy-znp/blob/dev/TOOLS.md#backup-and-restore">zigpy-znp documentation</a>.</p>

## Step 4: Setup zigbee2mqtt or ZHA

Next up: Configure your choice of software so that it can talk to your stick.

For zigbee2mqtt instructions: [click here](/software-config/zigbee2mqtt/) or for ZHA (Home Assistant): [here](/software-config/zha-home-assistant/).


## Step 5: Have fun!

With your stick flashed and the software of your choice configured, pair your devices with your newly set-up software and go forth and explore the world of open-source Home Automation!

Having problems? [This page](/faq) contains solutions to common issues.

A significant amount of effort goes to developing, maintaining and supporting the open source home automation ecosystem so if you can, please consider donating to the great software projects that are mentioned in these pages. A portion of each sale of Electrolama radio boards will be donated to [@Koenkk](https://github.com/Koenkk/) to support his work on [Zigbee2mqtt](https://github.com/Koenkk/zigbee2mqtt) and the [public firmware images](https://github.com/Koenkk/Z-Stack-firmware) used by zzh and many other projects.
