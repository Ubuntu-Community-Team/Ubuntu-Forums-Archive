---
title: "Acer Aspire One Recovery Partition After Installing Ubuntu 12.04 / Grub2"
date: 2014-02-10
forum: General Help
---

### Post by propofolboy on 2014-02-10
Ok so this is something I searched the forums for and it seems it has caused grief for many people with no obvious solution.

Older Acer Aspire One netbooks (mine is an AOA150) came with a Windows XP Recovery Partition called PQService.  To access it you press ALT-F10 at boot, and you can restore your system to factory.  There are no recovery CD's with my computer.  Furthermore Acer Canada will not sell them to Canadian customers.  So if your hard drive goes, you are pretty much screwed.

To further complicate this, when you install Ubuntu, GRUB will overwrite the MBR.  This makes accessing the recovery partition impossible via ALT-F10.  There is no obvious way to put back to the recovery partition to restore the computer.

There is one solution I came across, [http://ezinearticles.com/?How-To-Repair-The-Acer-D2D-Recovery&id=794500](http://ezinearticles.com/?How-To-Repair-The-Acer-D2D-Recovery&id=794500)
but this involves restoring the MBR, so then you can't use Ubuntu.

There MUST be a way to add a grub entry to boot to the PQService recovery partition.  I tried to do it today, by editing 40_custom, but I just couldn't get sudo update-grub to add anything. 

Is there some Grub guru who can help out...
Thanks!

---

### Post by oldfred on 2014-02-10
I do not know if they modify MBR to boot that partition?

You can always make a backup of the MBR.
       [https://help.ubuntu.com/community/WindowsDualBoot#Master](https://help.ubuntu.com/community/WindowsDualBoot#Master) Boot Record backup and re-replacement
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1

Use only 446 as partition table may change and restore would restore old partition table.

You probably should just back up Windows. That often is better than a restore anyway as with restore you have to reinstall, update, & reconfigure everything.

      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Post this to see if it gives any clues:
      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by propofolboy on 2014-02-10
Thanks for reply.

I totally agree, backing up windows is probably better option.

However, if say you wanted to resell your acer aspire one you may want to restore to factory after zeroing the partitions you were using.  It would be nice to be able to boot to it.

---

