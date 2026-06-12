---
title: "Is it possible to copy or backup Grub2?"
date: 2013-06-26
forum: General Help
---

### Post by virgodave61 on 2013-06-26
I have had many problems with Grub2 becomeing corrupt, possibly because my 3D printer locks-up the computer and terminal and have to force shutdown. Boot-repair never seams to do the trick. Is it possible to copy/backup Grub and restore it with a live CD?

---

### Post by TheFu on 2013-06-26
I would be surprised if any program or system lockup after boot and not while the boot sector is being written can cause corruption. Surprised.

It is likely that you have other issues which need to be resolved. A failing disk controller perhaps or loose SATA cables or failing HDD?

What do the log files show?  Any warnings or errors?

---

### Post by oldfred on 2013-06-26
Is it grub2 or just not rebooting as file system gets corrupted by system crash. Systems almost always need fsck after shutdown while system is running.

Best to remember elephants if you have to reboot.
       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

And if it does not boot then  fsck from liveCD.
      
 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by virgodave61 on 2013-06-30
Thanks, for your input. I will dismantle the computer clean and deoxit sata cables to be on the safe side. Is there any recomended graphical based software for testing the HD. What log files do I need to keep an eye on? Sorry but I'm a noob.

---

### Post by grahammechanical on 2013-06-30
> **virgodave61 said:**
> Thanks, for your input. I will dismantle the computer clean and deoxit sata cables to be on the safe side. Is there any recomended graphical based software for testing the HD. What log files do I need to keep an eye on? Sorry but I'm a noob.

It all depends on what version of Ubuntu you are using. Later versions have a utility called Disks that reads the smart data off of a hard disk if the disk collects smart data.

A description of what happens when you reboot would help identify where the problem lies. As regards the 3D printer why is that causing the OS to crash? you might want to install System Load indicator. That will monitor CPU, Memory, swap, and other usages. It might help fix why the OS is crashing. Printer requiring lots of memory? Not enough swap? Stuff like that.

Regards.

---

### Post by virgodave61 on 2013-07-01
I really appreciate all the reasponse to my messages. My 3-D printer interface software uses python. I keep getting in situations where I loose USB communication with my printer and the only way to get it going again is to shut everything down and restart/reboot, when I try to shut down the interface or terminal the screen turns dark and just sits there. Then I have to hold the power button down untill it shuts down. So I was kind of figuring this was causing my boot failures.

---

### Post by oldfred on 2013-07-01
Only use power button if REISUB does not work.

---

