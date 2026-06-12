---
title: "totem-gstreamer error crashing synaptic"
date: 2007-02-17
forum: General Help
---

### Post by u-ben-tu on 2007-02-17
totem-gstreamer is causing errors when I'm installing certain packages.

I dutifully pasted the error message into a text document, but after a reboot fsck ran automatically and found loads of problems on my /home partition and after repairing them the text document won't open [I've also lost a lot of my settings (keyboard, mouse, firefox bookmarks...)] . I'm a newbie, so I don't know where to find a log of the error.

I thought reinstalling or removing totem-gstreamer might work, but when I open synaptic and select totem-gstreamer it crashes synaptic, the cpu shoots up to 70-90% and I have to restart. There's definitely something seriously wrong somewhere because until fsck ran applications were taking forever to open (even though cpu was barely being used) whereas now things are running a lot better. 

Don't know what information to give to help diagnose this problem, but my machine has 3.4E ghz Intel Pentium 4 with 250GB harddrive, 1GB ram and ATI Radeon 9500 running Dapper with the 686-smp kernel and hyperthreading enabled, ati driver and beryl.

I'm enjoying using Ubuntu, but until I work out what's going wrong I'm not ready to migrate all my files over from my XP partition and wave Microsoft goodbye. Can anyone help?

---

### Post by Muzik83 on 2007-02-17
What is the output from the following commands (not all of it, anything that looks important and/or the last 50 lines or so):

dmesg 

sudo tail -25 /var/log/messages

tail -25 /var/log/dpkg.log

Hopefully these tell us something good :)

-sean

---

### Post by u-ben-tu on 2007-02-17
Thanks Sean. 

**Last few lines of Dmesg ...**

[INDENT][17179602.008000] ACPI: Power Button (FF) [PWRF]
[17179602.008000] ACPI: Power Button (CM) [PWRB]
[17179602.260000] ibm_acpi: ec object not found
[17179602.288000] pcc_acpi: loading...
[17179607.500000] eth0: no IPv6 routers present
[17179610.072000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179610.072000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[17179610.072000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0[17179610.332000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179610.736000] ppdev: user-space parallel port driver
[17179610.972000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179610.972000] apm: disabled - APM is not SMP safe.
[17179611.152000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179611.152000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179611.152000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[17179611.152000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179611.152000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179611.152000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179611.152000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179611.164000] [fglrx] total      GART = 67108864
[17179611.164000] [fglrx] free       GART = 51113984
[17179611.164000] [fglrx] max single GART = 51113984
[17179611.164000] [fglrx] total      LFB  = 126791680
[17179611.164000] [fglrx] free       LFB  = 116002816
[17179611.164000] [fglrx] max single LFB  = 116002816
[17179611.164000] [fglrx] total      Inv  = 134217728
[17179611.164000] [fglrx] free       Inv  = 134217728
[17179611.164000] [fglrx] max single Inv  = 134217728
[17179611.164000] [fglrx] total      TIM  = 0
[17179611.208000] Bluetooth: Core ver 2.8
[17179611.208000] NET: Registered protocol family 31
[17179611.208000] Bluetooth: HCI device and connection manager initialized
[17179611.208000] Bluetooth: HCI socket layer initialized
[17179611.232000] Bluetooth: L2CAP ver 2.8
[17179611.232000] Bluetooth: L2CAP socket layer initialized
[17179611.248000] Bluetooth: RFCOMM socket layer initialized
[17179611.248000] Bluetooth: RFCOMM TTY layer initialized
[17179611.248000] Bluetooth: RFCOMM ver 1.7[/INDENT]

**Output of sudo tail -25 /var/log/messages ...**
[INDENT]
Feb 17 15:59:16 localhost kernel: [17179611.164000] [fglrx] max single LFB  = 11 6002816
Feb 17 15:59:16 localhost kernel: [17179611.164000] [fglrx] total      Inv  = 13 4217728
Feb 17 15:59:16 localhost kernel: [17179611.164000] [fglrx] free       Inv  = 13 4217728
Feb 17 15:59:16 localhost kernel: [17179611.164000] [fglrx] max single Inv  = 13 4217728
Feb 17 15:59:16 localhost kernel: [17179611.164000] [fglrx] total      TIM  = 0
Feb 17 15:59:16 localhost kernel: [17179611.208000] Bluetooth: Core ver 2.8
Feb 17 15:59:16 localhost kernel: [17179611.208000] NET: Registered protocol fam ily 31
Feb 17 15:59:16 localhost kernel: [17179611.208000] Bluetooth: HCI device and co nnection manager initialized
Feb 17 15:59:16 localhost kernel: [17179611.208000] Bluetooth: HCI socket layer initialized
Feb 17 15:59:16 localhost kernel: [17179611.232000] Bluetooth: L2CAP ver 2.8
Feb 17 15:59:16 localhost kernel: [17179611.232000] Bluetooth: L2CAP socket laye r initialized
Feb 17 15:59:16 localhost kernel: [17179611.248000] Bluetooth: RFCOMM socket lay er initialized
Feb 17 15:59:16 localhost kernel: [17179611.248000] Bluetooth: RFCOMM TTY layer initialized
Feb 17 15:59:16 localhost kernel: [17179611.248000] Bluetooth: RFCOMM ver 1.7
Feb 17 15:59:30 localhost gconfd (ben-5281): starting (version 2.14.0), pid 5281  user 'ben'
Feb 17 15:59:30 localhost gconfd (ben-5281): Resolved address "xml:readonly:/etc /gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 17 15:59:30 localhost gconfd (ben-5281): Resolved address "xml:readwrite:/ho me/ben/.gconf" to a writable configuration source at position 1
Feb 17 15:59:30 localhost gconfd (ben-5281): Resolved address "xml:readonly:/etc /gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb 17 15:59:30 localhost gconfd (ben-5281): Resolved address "xml:readonly:/var /lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb 17 15:59:30 localhost gconfd (ben-5281): Resolved address "xml:readonly:/var /lib/gconf/defaults" to a read-only configuration source at position 4
Feb 17 15:59:40 localhost gconfd (ben-5281): Resolved address "xml:readwrite:/ho me/ben/.gconf" to a writable configuration source at position 0
Feb 17 16:19:08 localhost -- MARK --
Feb 17 16:39:08 localhost -- MARK --
Feb 17 16:59:08 localhost -- MARK --
Feb 17 17:19:09 localhost -- MARK --[/INDENT]

**Output of tail -25 /var/log/dpkg.log ...**
[INDENT]
2007-02-13 21:40:29 status installed totem 1.4.3-0ubuntu1
2007-02-13 21:40:29 remove totem 1.4.3-0ubuntu1 1.4.3-0ubuntu1
2007-02-13 21:40:29 status half-configured totem 1.4.3-0ubuntu1
2007-02-13 21:40:29 status half-installed totem 1.4.3-0ubuntu1
2007-02-13 21:40:29 status config-files totem 1.4.3-0ubuntu1
2007-02-13 21:40:29 status config-files totem 1.4.3-0ubuntu1
2007-02-13 21:40:29 status config-files totem 1.4.3-0ubuntu1
2007-02-13 21:40:29 status not-installed totem <none>
2007-02-13 21:40:29 status half-configured totem-gstreamer 1.4.3-0ubuntu1
2007-02-13 21:40:29 remove totem-gstreamer 1.4.3-0ubuntu1 1.4.3-0ubuntu1
2007-02-13 21:40:29 status half-configured totem-gstreamer 1.4.3-0ubuntu1
2007-02-13 21:41:35 status half-configured totem-gstreamer 1.4.3-0ubuntu1
2007-02-13 22:33:19 status half-configured totem-gstreamer 1.4.3-0ubuntu1
2007-02-16 08:53:14 upgrade libmagick9 6:6.2.4.5-0.6ubuntu0.4 6:6.2.4.5-0.6ubuntu0.5
2007-02-16 08:53:14 status half-configured libmagick9 6:6.2.4.5-0.6ubuntu0.4
2007-02-16 08:53:14 status unpacked libmagick9 6:6.2.4.5-0.6ubuntu0.4
2007-02-16 08:53:14 status half-installed libmagick9 6:6.2.4.5-0.6ubuntu0.4
2007-02-16 08:53:14 status half-installed libmagick9 6:6.2.4.5-0.6ubuntu0.4
2007-02-16 08:53:14 status unpacked libmagick9 6:6.2.4.5-0.6ubuntu0.5
2007-02-16 08:53:15 status unpacked libmagick9 6:6.2.4.5-0.6ubuntu0.5
2007-02-16 08:53:15 status half-configured totem-gstreamer 1.4.3-0ubuntu1
2007-02-16 08:53:15 status unpacked libmagick9 6:6.2.4.5-0.6ubuntu0.5
2007-02-16 08:53:15 status half-configured libmagick9 6:6.2.4.5-0.6ubuntu0.5
2007-02-17 15:55:41 status half-configured libmagick9 6:6.2.4.5-0.6ubuntu0.5
2007-02-17 15:55:52 status installed libmagick9 6:6.2.4.5-0.6ubuntu0.5
[/INDENT]

---

### Post by u-ben-tu on 2007-02-18
Not sure if this is connected, but I've lost sound when playing mp3s. I was using Banshee  about half an hour ago and everything was fine. Now there's no sound. I know I haven't lost sound completely as I just played a Youtube video with sound...

... OK, I just opened System > Preferences > Sound and tried to play the login and logout effects to see what would happen and they played fine, but Firefox crashed and now I can hear my mp3s on Banshee again.

Does anyone have any idea what's going on here?! :confused:

---

### Post by u-ben-tu on 2007-06-26
For the record...

The original problem was caused by a faulty hard drive which was creating all sorts of weird behaviour I couldn't account for. Now that I've got a new hard drive, I've been using Ubuntu without too much trouble (although I am having some [[COLOR="Red"]problems with Firefox[/COLOR]]("http://ubuntuforums.org/showthread.php?t=484279")) and have ditched Windows completely.

The sound bug seems to be unrelated to my hard drive problem. It's simply that I can't play audio from two sources at once. Still stuck on this despite trying a few things in the forum, e.g. tried installing pulse audio, but couldn't get it going. Think I'm going to wait until next release to see if this problem is sorted. Hopefully they'll add  pulse audio to Gutsy.

---

