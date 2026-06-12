---
title: "Installing on a USB2 Drive (Intel Mac Mini)"
date: 2007-02-08
forum: General Help
---

### Post by DaveGee on 2007-02-08
Really simple question but as I search and search I can't seem to find any current (working) solutions....

The short of it:

Mac Mini, 1GB RAM, Intel Dual Core CPU, External USB2 Drive

I currently have:

Internal Drive (Mac OS - On a mac partition)
Internal Drive (WinXP - On an NTFS partition)
(refit)

Refit sees both OS's and boots each properly....

What I want:

Ubuntu installed on an External USB2 hard drive.

1 - Downloaded and burned the latest release
2 - Plugged in USB2 Drive
3 - Inserted Ubuntu Install CD (this is the 'regular one' (not the 'alt version')
4 - Rebooted

refit sees the CD and allows me to boot from it!!

5 - Answer all the questions
6 - Select Manual when we get to Parted (disk partitioning)

Parted starts out showing me the internal drive - I change it to display the USB2 external drive.

7 - Create an Ext3 partition and flag it as boot
8 - Create a 3GB swap-partition and flag as such
9 - Exit Parted and answer yes the the proceed question

At this point I remember something about selecting mount points and such...

10 - I choose the main (boot) partition and have it mount to /
11 - Similar process for swap

Oh also somewhere in that process it asked about GRUB?? and where to install it... It's default was DISK0 but I didn't think I should use that and was afraid if I did I'd kill my MacOS and WinXP drives (and working without a net..... yea yea yea I know I know)

Anyway.... I changed that from DISK0 to DISK1

Intermission for install process... get soda and/or snacks as needed... :)

Finished.... reboot....

refit pops up and shows MacOS Logo (as usual) - WinXP Logo (as usual) & Penguin (NEW!)

Tried to boot Linux....

Screen goes blank (black) and (I'm using an Apple Display) the screen powers light goes dark/off it will blink back on for a moment if you wait long enough but the display is still black (not even a cursor).

Note: USB Drive show no activity...

Searched around and saw messages about going into refits partition manager but it didn't say anything about it needing to update anything **and** it only shows the partitions on the INTERNAL drive.

Search some more and rebooted with CD and got back to Parted - the partition on the external drive is still EXT3 and set for mounting on / and is flagged as boot.

What could or should I do now?

Help me Obi-Wan I'm a total dope! :lolflag: 

Dave

---

### Post by DaveGee on 2007-02-08
Anybody?

---

