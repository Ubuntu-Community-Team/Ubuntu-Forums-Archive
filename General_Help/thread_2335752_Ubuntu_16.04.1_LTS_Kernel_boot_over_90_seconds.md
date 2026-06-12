---
title: "Ubuntu 16.04.1 LTS Kernel boot over 90 seconds"
date: 2016-08-31
forum: General Help
---

### Post by anthonyf-9 on 2016-08-31
I have detailed the issue on askubuntu.com however after 3 days and 79 views I still am no closer to an answer.

If desired I can try to reproduce the issue here (on the forums) however unless asked for I will just link to my issue (hope that is okay).

Any an all help is greatly appreciated.

[http://askubuntu.com/questions/817876/ubuntu-16-04-1-lts-kernel-boot-over-90-seconds](http://askubuntu.com/questions/817876/ubuntu-16-04-1-lts-kernel-boot-over-90-seconds)

---

### Post by carl4926 on 2016-09-01
Are you employing fstrim in any way?

---

### Post by anthonyf-9 on 2016-09-01
Not sure what [COLOR=#000000]fstrim is, if it is not on by default then I probably am not using it. My primary is an SSD drive however, root / is stored on a normal HDD.

Would it matter if its a Dual boot system with Windows 10?

I have a laptop with an SSD windows 10 / 16.04 dual boot that doesn't have this issue. Only difference is laptop has slightly different processor, only has the one ssd drive and nvidia graphics instead of amd - ati.

Thank you for the help, was starting to give up hope.


[/COLOR]

---

### Post by anthonyf-9 on 2016-09-02
I have done some additional testing:

I have unplugged every usb header, unplugged all HDD and the issue still happens (even with live usb).

I have this motherboard:

[http://www.intel.com/content/www/us/en/support/boards-and-kits/desktop-boards/intel-desktop-boards-with-intel-z77-express-chipset/intel-desktop-board-dz77ga-70k.html](http://www.intel.com/content/www/us/en/support/boards-and-kits/desktop-boards/intel-desktop-boards-with-intel-z77-express-chipset/intel-desktop-board-dz77ga-70k.html)

I am thinking it has to be something with the motherboard, perhaps the secondary SATA controller?

Anyone have any suggestions?

---

### Post by Doug S on 2016-09-02
Your "systemd-analyze blame" list is incomplete. Your "systemd-analyze plot" is unreadable. Give us some useful information to work with so we can try to help.

---

### Post by #&amp;thj^% on 2016-09-02
There is also a way to create a .svg file to view or attach it here
```
systemd-analyze plot > graph1.svg
```
it will save it in your Home Directory and will show all.

---

### Post by anthonyf-9 on 2016-09-05
> **Doug S said:**
> Your "systemd-analyze blame" list is incomplete. Your "systemd-analyze plot" is unreadable. Give us some useful information to work with so we can try to help.

okay I will attempt to attach everything here. Thank you for taking the time to help.

---

### Post by anthonyf-9 on 2016-09-05
Is there anything else I could try? This couldn't be related to UEFI could it? I have tested the same Live USB on multiple computers and this is the only one with any type of issues. Thinking of just running it on one of my other computers and abandoning it on this one even though this is the best computer I have currently. Does anyone have the motherboard I have (Intel® Desktop Board DZ77GA-70K) without these issues?

---

### Post by autocrat on 2016-09-05
I did a bit of web browsing. Seems the MB should be okay with Ubuntu. Is the firmware up to date on it?

---

### Post by Doug S on 2016-09-05
Your blame stuff seems pretty normal. The other day, I thought a bunch must be missing because so much time was not accounted for.
Your issue seems to be in the kernel load portion of your boot, (which, I see you already figured out on your askubuntu.com question) as it is taking more than 10 times as long as what might be considered normal or typical. I don't know why.

---

### Post by anthonyf-9 on 2016-09-05
> **autocrat said:**
> I did a bit of web browsing. Seems the MB should be okay with Ubuntu. Is the firmware up to date on it?

Yea the firmware is .86 which should be the latest.

> **Doug S said:**
> Your blame stuff seems pretty normal. The other day, I thought a bunch must be missing because so much time was not accounted for.
Your issue seems to be in the kernel load portion of your boot, (which, I see you already figured out on your askubuntu.com question) as it is taking more than 10 times as long as what might be considered normal or typical. I don't know why.

Maybe my overclock is messing stuff up but I did try to disable the OC and it still didn't boot properly. I will probably just use a different computer for Ubuntu as 100s of people have looked at my question and I have very little to go on.

I thank you very much for the help though. Just wish I could say for 100% certainty that it is my mobo or whatever. I was very tempted to get a new mobo using the same processor, ram, etc (just different mobo) and see if it worked. 

The motherboards for my processor (LGA 1155 and having a PCI Express 3.0) though have not gone down much in price so I will not be doing that. Specially since I have no issues with windows.

If anyone thinks of anything to try please let me know, I also wanted to throw out there that this was not an issue with version 14 of Ubuntu.

---

