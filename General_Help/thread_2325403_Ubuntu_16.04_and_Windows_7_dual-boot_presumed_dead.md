---
title: "Ubuntu 16.04 and Windows 7 dual-boot presumed dead"
date: 2016-05-22
forum: General Help
---

### Post by tapasray on 2016-05-22
I have been dual-booting Ubuntu (installed by me) and Windows 7 (originally loaded) on my VAIO notebook. Ubuntu is updated to 16.04. yesterday I noticed that the cursor had become laggy and what I'd like to call trembly. I restarted the machine twice but the problem persisted. Then I got into 'advanced' mode from the boot menu. As the process remained stuck at one point for a long time ... indefinitely, it seemed to me ... I powered off. Since then powering on doesn't bring up the boot menu 99% of the time. Nothing happens - the screen remains black. Even when the boot menu came up and I loaded Ubuntu, the machine soon froze. This happened a little while after I had started Luckybackup to sync some folders between the machine and a USB stick. It was frozen solid and there was no way I could shut down, so I powered off. Now when I power on again, I am left with the black screen again.

Please help!

---

### Post by oldfred on 2016-05-22
Power off is last thing you should do, that can corrupt drive and create another problem that has to be resolved before you can fix original issue.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/) 
    
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 
    
After fsck, then run this to see if it shows anything. More for boot issues, so may not show whatever your issue was.
       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by tapasray on 2016-05-22
Thanks, @oldfred! That is very detailed and I'm not sure I understood everything right away. It's late ... will try to absorb the whole thing tomorrow morning, implement it and report back. 

Thanks again for giving so much time for this.

---

