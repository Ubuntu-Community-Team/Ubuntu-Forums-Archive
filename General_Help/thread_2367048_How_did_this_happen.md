---
title: "How did this happen?"
date: 2017-07-25
forum: General Help
---

### Post by Autodave on 2017-07-25
I am posting this to try and find out how this happened, but even more so to let some of the experts in dual booting Ubuntu and Win10 have something to wonder about.

I recently replaced my primary machine with a new one. New machine came with Win10 on it. UEFI enabled.  My old machine was running Xubuntu 16.04 only. This was installed via legacy boot.

New machine has an external SATA HD bay. To try it, I removed the SSD HD from old machine and mounted it in the external bay. I then went into the BIOS and shut off "fast boot". Nothing else! (The reason for that was to use part of the 1 terabyte spinning HD for storage of music and pictures: I used Win10 to repartition the spinning HD.)  In the BIOS, I made the boot order: 1. DVD, 2. external bay, 3. internal HD. Since I rarely use Win 10, this worked great. Machine booted to external bay's SSD directly. When I did want to use Win10, I would shut down machine, remove the external drive, and turn machine back on and it would boot normally right into Win10. This worked for about 2 months.

A few days ago, a friend called asking for help in locating something in Win10. Not knowing from memory where it was exactly, I powered down and removed my external HD and rebooted. I got a message saying that there was no HD found! I tried rebooting again: same thing. Not knowing what else to do, I plugged the external SSD back in to see if I could access the WIN10 HD. After about 10 seconds, I was presented with the GRUB menu! I chose Win10 and it booted into Win10 just fine. It will also boot into Xubuntu 16.04 just fine.

I have several dual boot machines and the menu is exactly what I would expect to see on one of them. But how did this happen? I did not install GRUB. Plus, one HD is UEFI and the other is legacy!

---

### Post by yancek on 2017-07-25
If I understand your situation, you had Xubuntu on an SSD on your old machine with a Legacy install, got the new machine with a pre-installed windows on the internal drive and you have a data only external drive, correct?  If I understand, when you set the windows only drive to boot first and it failed, probably something wrong with the EFI partition or something else in windows.  As far as Grub, you must have had it installed on the SSD to boot Xubuntu so that is where it came from.  I'm not familiar enough with EFI to explain the situation but I would not expect a Legacy Grub to boot an EFI install of another OS.  Having a Legacy install on one drive and an EFI on another is not a problem although you have the inconvenience of having to make a selection in the BIOS on boot.  Hopefully an EFI expert will post.  You might try running boot repair just to get the bootinfoscript to review or post here.

---

### Post by Autodave on 2017-07-25
No. External drive had the fully functioning Xubuntu 16.04 on it which was created in legacy mode on the first machine.  This machine did not have Windows on it. I get new machine and left it in UEFI mode and simply plugged the drive in and it booted to it and ran. It was the second in the boot sequence. When I wanted to use Win10, I simply removed the external drive and booted the machine. Win 10 came up just like it normally would if it were the only OS on machine. (It did take longer than normal because I had shut off Fast Boot so that I could use part of that drive for storage.) I did this probably 15 times or more. When I wanted Xubuntu, that SSD was plugged back in, machine booted, and Xubuntu came up like it was the only OS on the machine.

Then one day, Win10 would not boot: all I got was an error message saying that the HD was not found. I plugged the external drive back in and when booting up, I had GRUB installed and and could chose either OS.

I never installed GRUB. And even if I had wanted to, I figured it wouldn't work since one drive was UEFI and the other was legacy.

---

### Post by Autodave on 2017-07-29
bump

---

