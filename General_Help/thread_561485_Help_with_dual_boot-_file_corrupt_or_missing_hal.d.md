---
title: "Help with dual boot- file corrupt or missing hal.dll"
date: 2007-09-27
forum: General Help
---

### Post by Eirikr88 on 2007-09-27
Hello there. I have already searched through the wubi forums looking for an answer to my problem but i have not been able to find anything of help. Thus, i broke down and am posting my problem. Currently my drive setup is as follows

Disk 1
-partition 1-C: Windows
-partition 2-D: Games
-partition 3-E: media

Disk 2 
-partition 1-F: Storage, and the location of my wubi Ubuntu install.

Now i have already changed the boot.ini to reflect the different drive and when i try to boot Ubuntu i get that hal.dll is missing or corrupt. Any help in this would be great. Thanks in advance!

---

### Post by simd on 2007-09-27
I've just installed Wubi and am getting the same error. I can boot into Windows ok, but when I select the Ubuntu option I get the error and the load stops. 

I did have Wubi installed a while ago, and removed it, so therefore this is a reinstallation. I don't know if that's related.

---

### Post by ago on 2007-09-27
run chkdsk /r from windows CD
if you do not have the windows CD use [http://www.tweakxp.com/article36941.aspx](http://www.tweakxp.com/article36941.aspx)

---

### Post by ago on 2007-09-27
> **Eirikr88 said:**
> Now i have already changed the boot.ini to reflect the different drive and when i try to boot Ubuntu i get that hal.dll is missing or corrupt. Any help in this would be great. Thanks in advance!
boot.ini entry for wubildr should always be "C:" whatever is the drive where wubi is installed

---

### Post by Eirikr88 on 2007-09-27
when i change it to c: it gives me the message
booting 'find wubi/boot/grub/menu.lst'
when i changed it to f: i got the
file missing or corrupt: hal.dll

---

### Post by Eirikr88 on 2007-09-27
ok, just an update.

Rank chkdsk /r and no erros.
Changed boot.ini back to 'C' instead of F and got the message, as described in my post right above. changed back to 'F' and got the corrupt or missing hal.dll message.

---

### Post by tinybit on 2007-09-28
This appears to be an unknown grub4dos bug.

Try to enter grub command line(e.g. by quickly pressing the c key at startup), and execute the following sequence:

debug 0x7FFFFFFF
geometry (hd0)
geometry (hd1)
geometry (hd2)
geometry (fd0)
geometry (cd)

and post the output debug info please.

If you cannot gain a command line, you may quickly press the Insert key at startup, and trace the boot process step-by-step. Then you may post the debug info on the screen. This will be very helpful for the developers.

---

### Post by Eirikr88 on 2007-09-28
So i uninstalled from 'F' drive and freed up space on my c and reinstalled
it now works fine. so if this helps any with troubleshooting, i would still like to run it on my extra hard drive just for my own personal reasons.

---

