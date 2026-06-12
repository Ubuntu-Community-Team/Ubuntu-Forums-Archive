---
title: "Install from CD: [firmware bug]: Failed to parse event in TPM final events log"
date: 2020-03-01
forum: General Help
---

### Post by crustymd on 2020-03-01
Dear Community,

[Introduction]I did not use Ubuntu for quite some time, and now I want to use it alongside windows for various reasons. Well to use Ubuntu as basic OS, and just when really needed will use windows.

I tried to install from USB and failed multiple times and the type of bugs I could never find online. So i tried now from CD. I boot from CD I choose "Install Ubuntu" and next thing is a black screen with this message "**[o.oooooo][Firmware Bug]: Failed to parse event in TPM Final Events Log**" - it seems like it does not like the tech, or it is not compatible I am not sure. (Also you can see the image attached)

I have an Alienware PC, I will also attach the specs. Could anyone help solve this issue? Or I will not be able to run it on this PC?

Thank you! 

See materials attached
[ATTACH=CONFIG]285116[/ATTACH][ATTACH=CONFIG]285117[/ATTACH][ATTACH=CONFIG]285118[/ATTACH]

---

### Post by guiverc on 2020-03-01
I don't know your box (hardware), nor do I know the message (that I think is just a message telling you your box may need a firmware upgrade) but did you
- verify your downloaded ISO to ensure it was perfect? and then
- verify your write to install media to ensure write was flawless?

[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0) 
[https://discourse.ubuntu.com/t/how-to-verify-your-ubuntu-download/14010](https://discourse.ubuntu.com/t/how-to-verify-your-ubuntu-download/14010)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)  (where CD refers to any media used, be it CD/DVD/HDD/SSD/thumb-drive or anything else).

These checks take seconds, but can save hours-days of diagnosing of problems.

*PS: I use `zsync` for my downloads which performs the ISO download verification for me, but will re-check if if it wasn't just downloaded..*

---

### Post by him610 on 2020-03-01
It looks like you have a fairly recent model CPU, and I assume a recent model computer. 
Which model of Alienware?
Which release of Ubuntu did you attempt to install?
Did you go into Bios/Euve to disable Fast Start and Secure Boot?
Can you boot into Ubuntu from the USB stick?

---

