---
title: "Problem with grub2"
date: 2013-10-12
forum: General Help
---

### Post by xeddog on 2013-10-12
I have a Ubuntu_GNOME 13.04 system called G-man that I can no longer boot.  It was running fine until I came across a directory that I was having problems with.  This directory was a mountpoint for a filesystem that had been setup for autofs.  I made some changes to the /etc/exports file on the remote system (Stealth), and that caused problems everywhere so I changed them back and rebooted Stealth.  But now the /media/Stealth directory on G-man has some problems.  If I go to /media and do an "ls" command I see Stealth listed.  If I then try to "cd Stealth", I get a spinning ball cursor and it hangs there seemingly forever.   I opened a terminal and ran "sudo rmdir Stealth" and got an error message saying no such directory.  So I decided to boot to the recovery console and try to delete the directory from there.

This is where the problems really began.  Normally when I boot the machine I do not see the grub menu at all.  So I held the ctrl key and after a couple of attempts I got the grub menu like I wanted.  But now the problem is that the keyboard is dead.  Completely.  So I cannot move the cursor to select the advanced options, nor can I even just press enter to continue.  I am stuck at the grub menu.  Any and all subsequent boot attempts show the grub menu and then leave me stuck.  How do I get passed this one?????


Thanks,

X

Edit:  I found my liveCD and I have the same problem with it.  When the initial menu comes up to select the language, the keyboard and mouse are dysfunctional.  But the liveCD will eventually continue on and boot.  Once the system is up, the keyboard and mouse function normally.  Weird.

---

### Post by Bashing-om on 2013-10-12
xeddog; Hi !

My thoughts; check bios settings for usb devices.
ps2 keyboard/mouse, set in bios usb devices to "legacy"
USB keyboard and/or mouse , not legacy and also plug n play is enabled in bios.

Mouse/keyboard not responding at the grub menu is generally found to be a bios setting. - The operating system is not loaded at that time.

[INDENT][INDENT]in the process of booting
[/INDENT][/INDENT]

---

### Post by xeddog on 2013-10-13
Not meaning to argue with you, but if the bios settings were off, wouldn't the keyboard and mouse also be disabled when attempting to access the computer bios???  I have no problems with that, but I will double check them the next time I boot.

I did get a work-around though.  I booted with the liveCD, got a copy of boot repair, and ran that.  Now when the grub menu comes up it has the 10 second countdown timer and when it expires the system boots again.


Thanks,

X

---

### Post by Bashing-om on 2013-10-13
xeddog; Not an argument at all. Nor do I imply that I know all things.
This is the way the boot process is supposed to work, and providing the drivers are available for the hardware at each stage;
Bios fires up and checks the hardware out .. it has simple hardware drivers for basic stuff, at the appropriate time bios hands off to grub with the settings it is aware at that time, grub also has some simple drivers and stuff, enough to start the boot process and get the kernel loaded into ram to start the initramfs boot, now the kernel will probably load the advanced drivers for the hardware.

If the settings are not correct for the hardware, then when it does hand off to grub and those drivers are either incompatible or non-existent, there is no response from that related hardware until the kernel loads the required drivers. I have seen -rare- cases where there are no appropriate drivers available until the kernel is loaded. A real bummer as then you have no access to grub in those initial stages !

It all starts with bios configurations as to what you have told bios. 

I am spending my live learning the why and how ->
[INDENT][INDENT][INDENT][INDENT]it is all a process
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by xeddog on 2013-10-15
Well this one turns out to be one of those "aw crap!" things.  I had the PS2 keyboard plugged into the ps2 mouse port.  As soon as I switched it everything is fine.

X

---

### Post by Bashing-om on 2013-10-15
xeddog; Great !

The simplest of things can bite the deepest.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

