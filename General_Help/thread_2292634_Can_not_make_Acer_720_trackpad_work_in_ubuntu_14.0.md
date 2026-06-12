---
title: "Can not make Acer 720 trackpad work in ubuntu 14.04 LTS"
date: 2015-08-29
forum: General Help
---

### Post by woodyhappyou on 2015-08-29
[SIZE=4]Hey guys, 

I installed ubuntu 14.04 on Acer c720 chromebook. The trackpad is not responding. I read a few previous posts and manage to update my kernel to the lastest version 3.19 but the trackpad still does not work at all even after the update of kernel. I felt discouraged and wanna some of you can help me go through this problem. 

Thx. [/SIZE]

---

### Post by TheFu on 2015-08-29
Well, if you stay with the stock kernel, this will work: [http://blog.jdpfu.com/2014/04/18/easy-acer-c720-ubuntu-14-04](http://blog.jdpfu.com/2014/04/18/easy-acer-c720-ubuntu-14-04)
I'm on 3.16.0-46-generic today, but was on 3.13.xxxx previously.

Please stay with the default fonts here.

---

### Post by woodyhappyou on 2015-08-29
Thanks for replying, TheFu, 

I tried the steps for the link. In the first step, when I ran the scripts in terminal, there is an error saying:

" 2015-08-29 19:50:26 (93.0 MB/s) - written to stdout [1330]

can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/i2c/busses/i2c-designware-pcidrv.c b/drivers/i2c/busses/i2c-designware-pcidrv.c
|index f6ed06c..816cbd1 100644
|--- a/drivers/i2c/busses/i2c-designware-pcidrv.c
|+++ b/drivers/i2c/busses/i2c-designware-pcidrv.c
--------------------------
File to patch: "

I don't know how to deal with this. 

Also, I checked the file "[COLOR=#000000][FONT=lucida grande] /etc/modules", it is lacking these lines 

"[/FONT][/COLOR][COLOR=#63FF00][FONT=bitstream vera sans mono]chromeos_laptop[/FONT][/COLOR]

i2c-designware-core

i2c-designware-pci
 [COLOR=#63FF00][FONT=bitstream vera sans mono]i2c-designware-platform[/FONT][/COLOR][COLOR=#000000][FONT=lucida grande]"
Should I add them manually into the file "/etc/modules" ?

Hope for your reply. [/FONT][/COLOR]

---

### Post by TheFu on 2015-08-30
You should add the lines manually.

Don't know about the other stuff. Sorry. It works here and has since 14.04 was released. I re-run it every time there is a new kernel released.

---

