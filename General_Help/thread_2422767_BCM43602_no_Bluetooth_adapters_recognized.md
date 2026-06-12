---
title: "BCM43602 no Bluetooth adapters recognized"
date: 2019-07-12
forum: General Help
---

### Post by paulp0523 on 2019-07-12
Hello i have a xps15 that blows speakers about every two weeks so im trying to connect some bluetooth speaks but ubuntu doesn't recognize any bluetooth adapter in ubuntu 18.04

---

### Post by nilandj-nilandsplace on 2019-07-30
I had a similar problem with Bluetooth over my wifi adapter card for Ubuntu-gmome 14.04. The old ateros card worked but the bluetooth co-existence was always poor. I had upgraded the wifi card and antennas to an Intel dual-AC 7260 card but could never get bluetooth to work in ununtu or win7 (-dual boot HP ProBook 440 G1). So the next Idea was to try a Broadcomm BCM4352 and I had the same problem.

After to weeks of chasing forms, links and support options I could not get my mouse to work!

In the terminal command line **$ bluetoothctl** it never would find the controller. **$ blueman-manager** would not work neither would **$ bluetooth-wizard.**
But then I ran **$ sudo bluetooth-wizard** and it found my mouse in less then a second. 
Some forums suggest it is a problem of permissions of RFcomm or hci0 but the answers are too convoluted and doing** $ sudo usermod -aG  plugdev users wheel lp** did not seam to work and was an answer for slackware64 anyway.

Only **$ sudo bluetooth-wizard** worked!!!

[B]Note:
[/B] Ubuntu will INSTALL the Brodcomm firmware drivers for BMC4252 under aditional drvivers, ($ /usr/bin/software-properties-gtk --open-tab=4) but will not install the needed bluetooth firmware driver for BCM20702A1.
You will need to hack this yourself and add it as /lib/firmware/brcm/BCM.hcd or /lib/firmware/brcm/BCM20702A1-0a5c-21fb.hcd. The secret is the octal code found by doing $ spci -knn | grep Net -A3; lsusb in Mine it came up as:

03:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Hewlett-Packard Company Device [xxx:xxxx]
    Kernel driver in use: wl
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f2:b3c8 Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 15d9:0a4e Trust International B.V. 
Bus 003 Device 004: ID 0a5c:21fb Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

...and the needed info is in the second to the last line "0a5c:21fb" that is the device and manufacturer code.
The hack was made from broadcom-sta-dkms_6.30.223.271-5_all.deb or windows DR_USB_BT400_1201710_Windows.zip, but you will need another program to convert the hex file to a .hcd file. The newer version did not work so I stuck with 6.30.223.271-5
I did a search for "Firmware for BCM20702A1 based devices" and found it. Don't expect to find it from Broadcomm as it seems they have hidden them, but I found them on a dell website.

Perhaps the Intel card would have worked if I had run **$ sudo bluetooth-wizard **as that card I did not need to do a hack for the drivers? Any one need some Intel PCIe half cards for a Laptop?
 -James

---

