---
title: "Parition nightmare / SSD questions"
date: 2014-05-31
forum: General Help
---

### Post by psykatog on 2014-05-31
So, I bought a used windows 8 laptop, and things went downhill from there.  It's a Samsung np900x3c, and the only disk is a 128gb SSD.  

Here's a screenshot of the current partitions on my ssd - when I bought it, I reinstalled windows 8, and it would appear that it created an extra recovery drive.[ATTACH=CONFIG]253632[/ATTACH][ATTACH=CONFIG]253632[/ATTACH]

I attempted to create a partition for dual-booting linux, but when I installed it it looks like it split itself into a 9 and 30gb drive.  I also have around 6gb of unallocated space.

Honestly, I'm a little baffled at this point, so I apologize if I haven't given a good summary of what changes I've made, but I could use some advice on returning to a normal, less wasteful setup.
Here's what I *think* it needs to be
-sda1 should be a windows boot partition.  I think it's currently my sda4, the 128MB partition that's labeled "reserved".
-I need the EFI partition to keep using windows 8.  This *should be* sda2 I think.
-Windows RE tools - I believe I need to keep this in case I need to troubleshoot or reinstall windows.
-My C: Windows partition
-Linux partition

I know I'm asking about windows 8 on a ubuntu forum, but does anyone know if it's essential to have a recovery partition aside from the RE tools?  I tend to always keep data backed up on an external hard drive, so do I need those "Samsung_rec" partitions?  Can I back them up to an external drive using any linux software?  

Also, I've heard that **I must resize or allocate a partition for linux from within windows**, does anyone know if this is true?

Thanks, sorry that I'm a bit more ignorant and exasperated than usual.

---

### Post by oldfred on 2014-06-01
Windows seems to call everything a recovery partition. One is really Windows repair partition and one is the vendor image of your hard drive for total erase & restore to like new or as purchased.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

I normally suggest a full Windows backup including the efi partition. And a separate repair CD or flash drive. You may not always be able to boot into internal repair/recovery and then have to have a Windows way to boot.
And a full backup includes all the configuration changes & reboots you have done since you got system. Reinstall all that is not fun.

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

If you have good backups, the recovery partition may only be useful if you want to use it to restore system for resale. But it should offer a choice to create a set of DVDs to do that and then that partition has little value.

Generally better to use Windows to resize its own NTFS partition and reboot immediately. After any resize it has to run chkdsk. If hibernated and you try to resize from any outside tool that will cause issues. But many have used gparted and it has worked, just sometimes it may not and then the user blames Linux when often a different Windows issue. 
Do not create partitions with Windows internal disk tools, if often converts to dynamic partitions which does not work with Linux nor even some Windows tools.

---

### Post by psykatog on 2014-06-01
So, according to the markphelps thread, it is best to install linux into unallocated space?  When I was trying to install linux onto the designated partition (~45gb), as you can see in the screenshot it split it into two partitions.  Is this because I had formatted that 45gb partition first?   I think I had tried setting it up as ext4.

Also, if I went out and bought a windows 8 install disc, would I need to worry about keeping all of these recovery partitions?

---

### Post by oldfred on 2014-06-01
A full Windows install disk has its own license and you would not need any recovery partitions as the DVD would be that. That is what vendors did in not providing DVDs with new systems. Saves a few pennies and prevents installs to other systems.

I always partition in advance with gparted and use Something else to choose partition. Or I am overinstalling an old install.

---

