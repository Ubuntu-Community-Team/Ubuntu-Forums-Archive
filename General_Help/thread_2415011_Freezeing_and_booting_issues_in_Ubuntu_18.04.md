---
title: "Freezeing and booting issues in Ubuntu 18.04"
date: 2019-03-18
forum: General Help
---

### Post by ls8_ on 2019-03-18
I'm running Ubuntu 18.04.2 LTS on an intel nuc6cayh with 8gb memory and a 500gb hard drive, installed using a usb stick. Ubuntu is the sole OS installed, all hardware is new, I have not used Ubuntu or Linux for years. I have been having two issues:


First: Strange boot behaviour. Sometimes when turning on the PC, the power button turns blue and there are normal noises a running PC makes, but there is never any video output, a login screen is never reached. This is normally 'solved' by hard resetting and rebooting several times. I am using UEFI boot.


Second: Random freezing, this is the real headache. During normal use Ubuntu will run fine for hours but will unexpectedly totally freeze, sometimes when the computer is locked with no programs running, requiring a hard reset.     I have only tried the magic reboot sequence on one later freeze but it didn't appear to do anything.


I've attempted several solutions from web results without success, among them are editing the grub file ([link]("https://askubuntu.com/questions/971477/ubuntu-17-10-keeps-locking-up-and-freezing-mouse-and-keyboard-input-doesnt-wor"), first post), using an older kernel ([link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1798961/comments/26")), and changing display managers to lightdm ([link]("https://askubuntu.com/questions/971477/ubuntu-17-10-keeps-locking-up-and-freezing-mouse-and-keyboard-input-doesnt-wor") 2nd post,). I have also ran the gsmartcontrol tool with no issues, oddly there is no memtest option in the grub menu so I haven't run that. Having tried all of this I have no idea what to do next, perhaps the older kernel solution didn't work because I could find the exact one referenced in the link (closest I could find was 'v4.15.0-041500.201802011154', they used '4.15.0-43-generic'). Attached are the results of running ''dmesg -T' and 'journalctl -b '.
[ATTACH]282817[/ATTACH]
[ATTACH]282818[/ATTACH]

---

### Post by Autodave on 2019-03-19
I am wondering why memtest isn't there.  Perhaps you either have a bad download of the install or perhaps a bad burn to the USB. 

Your issue instantly makes me think that it could be a memory issue, so I would really like to see what memtest would tell you.  IF you just installed this, I would recommend getting a fresh download and trying again.

---

