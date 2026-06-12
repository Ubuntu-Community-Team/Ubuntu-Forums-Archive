---
title: "need help setting up cannon pixma ip1700 as a network printer"
date: 2007-08-11
forum: General Help
---

### Post by devin0 on 2007-08-11
i have been trying to set up my canon pixma 1p1700 printer, but when i am asked to choose the driver i can't because it is not in the list. can anyone tell me where i can get the driver and how to install it? thanks:)

---

### Post by TheExplorer on 2007-08-12
**Quick Steps:**
> sudo gedit /etc/apt/sources.list

**Add line:**
> deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

**Save, then run commands:**
> sudo apt-get update
sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
Configure your printer pasting the following address into your browser [http://127.0.0.1:631/](http://127.0.0.1:631/)

The working driver for Canon PIXMA iP1700 should be iP2200.

Taken from [here]("https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon").

---

### Post by dropwindoze on 2008-01-26
I did this and the printer installed but when I try to print, nothing prints, the printer doesn't even make a noise as if it received any input.

Any sugestions?

---

