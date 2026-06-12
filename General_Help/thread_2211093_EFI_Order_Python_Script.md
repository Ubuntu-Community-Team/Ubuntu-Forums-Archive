---
title: "EFI Order: Python Script"
date: 2014-03-14
forum: General Help
---

### Post by slooksterpsv on 2014-03-14
Hey all,

I've created a Python Script that will allow you to change the boot order on EFI systems if for example, after you installed Ubuntu on a dual-boot system, it only boots to Ubuntu and won't to Windows.

It's all textual, I'm going to use QT to create a Qt version were you can move options up and down and add or remove options.

Attached is the python file. Any suggestions would be great.

I'm going to try to look up how to get this on my own ppa and in launchpad.

---

### Post by slooksterpsv on 2014-03-15
Here's the QT Version of EFIBootOrder.
[ATTACH]251186[/ATTACH][ATTACH=CONFIG]251187[/ATTACH]

---

### Post by slooksterpsv on 2014-03-15
Finally made a deb package of it. Wow that took some effort!

YAY! =D

Requires 64-bit machine running saucy or later =D

Now i need to figure out how to upload it to a PPA:

[https://drive.google.com/file/d/0BzvZWf6CGx93bXlTMUdxT0dhdVE/edit?usp=sharing](https://drive.google.com/file/d/0BzvZWf6CGx93bXlTMUdxT0dhdVE/edit?usp=sharing)

[https://launchpad.net/~slooksterpsv/+archive/efibootorder](https://launchpad.net/~slooksterpsv/+archive/efibootorder)

PPA there for the QT version.

The issue was I wasn't structuring the directories correctly. instead of debian/efibootorder/usr/.... I was doing /debian/usr/share....

---

