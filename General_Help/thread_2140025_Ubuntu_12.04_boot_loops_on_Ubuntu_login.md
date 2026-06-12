---
title: "Ubuntu 12.04 boot loops on Ubuntu login"
date: 2013-04-28
forum: General Help
---

### Post by WUTANG4EVER on 2013-04-28
Can someone please help out. I had a frozen program and looked up how to kill the process and was in a rush and went 4 first solution i could find and pressed ctrl+alt+f2 then entered "TOP" and pressed exit and my computer rebooted. Well after restarting on login i entered my password and the screen flickers a couple times real fast and goes right back to log in. Can someone please help I love ubuntu but im new and this is the second time in a month since first using it and last time i had problem i had to repartiton my drives following someones bad command and i dont want to do again. THANKS

---

### Post by oldfred on 2013-04-28
It may be corrupted from the forced shutdown.

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Always best to remember the elephants before forcing a shutdown.


 Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by WUTANG4EVER on 2013-04-28
Ya high thanks 4 the reply. I tried the sudo e2fsck -CO -p -f -v /dev/sd1 and I got Invalid non-numeric argument to -C ("O") I dont no if im missing something as to me just not knowing as I am 3 weeks new into using Ubuntu and about 5 months into ever really using a computer. I appreciate all and any help i get because I am in a serious crash course trying to learn and this is my second major mistake that is costing some serious hours building my custom setup. I am not gonna let it get the best of me though and I no now to read more then the first article on what im trying to accomplish. Thanks

---

### Post by oldfred on 2013-04-28
If you used sd1, that would not be correct. It would be sda1, sda2, sdb1 etc.
Post this to see Linux partitions. it is -l or el, not one or eye. or just copy to your terminal.

sudo parted -l

---

