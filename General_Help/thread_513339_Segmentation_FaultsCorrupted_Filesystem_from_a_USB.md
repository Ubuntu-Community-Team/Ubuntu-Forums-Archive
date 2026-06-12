---
title: "Segmentation Faults/Corrupted Filesystem from a USB drive?"
date: 2007-07-30
forum: General Help
---

### Post by PiGeek31415 on 2007-07-30
Semi-important background info:
- Running Ubuntu Feisty on a Dell Dimension 2400
- I'm using four hard drives on this computer: two internally and two using usb connections.

The two internal drives are formatted as NTFS and dedicated to my Windows XP installation.
The first external drive, the one I installed Feisty to, worked perfectly with GRUB through several reboots, software installed perfectly, and everything was generally working well.
The second external drive remained unattached to the computer.

Well, I finally decide that it's time to try accessing the second USB drive, so I plugged it in.

Since it's formatted as NTFS as well, I used ```
sudo apt-get install ntfs-config
``` to get the tools to mount it.

It got as far as "(Reading databases..." before it froze.

Several minutes later, I unplugged the second USB drive; as soon as I did, the command completed (unsuccessfully), listing several errors about dpkg failing.

Unfortunately, from then on, every program I attempted to start (through either the applications menu or the terminal) generated a "Segmentation fault (core dumped)" message, even attempts to read man pages.

Thinking that it would help the problem, I restarted my system, only to be greeted with an "Error 17" in GRUB. Supposedly, that means that GRUB doesn't recognize one of the filesystems it's supposed to work with (I obviously know very little about GRUB, so bear with me here).

Since I can't get into XP or Feisty, I boot up the Feisty livecd. I ran gParted, and it's saying that the filesystem for the ubuntu installation is of "unknown" type.

Is there any way to rescue the system, even though I can't boot into it?

Or, if that's not possible, is there any way to prevent a failure like this in the future (aside from just not plugging in the second USB drive)?

Any and all help is appreciated.

Thanks, 
-PiGeek31415

---

