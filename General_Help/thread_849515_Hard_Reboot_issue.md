---
title: "Hard Reboot issue"
date: 2008-07-04
forum: General Help
---

### Post by d3drocks on 2008-07-04
ok,
when im in windows, i tend to get frusterated. it locks up at least once a week, and forces me to hard reboot. 
every time i do it, it f**ks up Wubi's ubuntu install and goes to busybox. it doesnt not do it sometimes, EVERY time i hard reboot it does this. getting annoying, cause if i cant get it to boot up, this will be the 3rd time ill have to install Ubuntu. (though ill probably switch to kubuntu this time).

EDIT: i got it working.
i also forgot to mention, that when i hard reboot Ubuntu, it still boots up ok the next time. this only happens when i have to hard reboot windows.

---

### Post by ago on 2008-07-04
We cannot fix the windows filesystem from within Ubuntu (yet). If it is marked as dirty you will have to clean it up using windows first or you will not be able to boot Ubuntu.

---

### Post by d3drocks on 2008-07-05
> **ago said:**
> We cannot fix the windows filesystem from within Ubuntu (yet). If it is marked as dirty you will have to clean it up using windows first or you will not be able to boot Ubuntu.

ok, i may not have explained well enough.
windows will still boot fine after a hard reboot. Ubuntu wont.

---

### Post by ago on 2008-07-05
> **d3drocks said:**
> ok, i may not have explained well enough.
windows will still boot fine after a hard reboot. Ubuntu wont.

Because windows runs a program that automatically cleans the filesystem at boot, we do not have an equivalent on the linux side (yet), not least because ms doesn't release the filesystem specs.

---

### Post by jmszr on 2008-07-05
This is from the Wubi Wiki- the 1st one should fix you up-works for me.

The Ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

Try The Following Solutions : 1) Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.

    *

      Select the "Tools" tab and click "check now" under error checking( On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using ubuntu now.

2) Reboot and hit Esc when prompted to enter the boot menu. Hit 'e' to edit the first line. Next select the second line and hit 'e' again. Input 'irqpoll' towards the end of the bootline. Then hit 'enter' and then 'b' to boot.

---

