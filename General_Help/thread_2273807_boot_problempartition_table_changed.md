---
title: "boot problem/partition table changed"
date: 2015-04-15
forum: General Help
---

### Post by jacky6 on 2015-04-15
hello,
i had dual boot for ubuntu and windows, it worked ok.  i had 3 partions, one for ubuntu and two for windows. i wanted to shrink one of the ntfs partition and enlarge the second one under windows. it definitely changed something becouse after restart it does not started and grub rescue promt was showed. after that i tried [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) - i clicked on recommended repair (boot-info result is here [http://paste.ubuntu.com/10830048/](http://paste.ubuntu.com/10830048/) ). grub is now showed, but there is just ubuntu distribution which work,but i cant boot to windows. gparted also dont show partitions - declare it as unallocated. i have access to one ntfs through file explorer in ubuntu (its 12.04). i gues it is a partition table issue but i have no idea how to fix it. i found some similar posts here, but i done a lot of damage already and dont want to get it even worse...
i would appreciate any help how to fix it or at least save files from ntfs disks.

---

### Post by QDR06VV9 on 2015-04-15
Hi jacky6 when you boot to Ubuntu try opening a terminal and update grub
```
sudo update-grub
```
Or this looks promising [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)
A little around half way down the page where it installs Windows Loader.
If that fails after a reboot to show your windows partitions then insert your boot-repair disk or thumb drive.
and try reinstalling Grub to all partitions if memory severs me it is in the advanced options tab.
Post back Regards

---

### Post by jacky6 on 2015-04-15
tried update it. now i see win at grub, but it dont boot, just show win logo, no error statement, but it do nothing for several minutes. gparted still cant see any partition and in ubuntu i see second nfts (not the bootable one with windows themself)
i also tried fdisk and win should be on sda2, but at booting grub declare it on sda1.

---

### Post by jacky6 on 2015-04-15
i tried recovery with win7 disc, unfortunately it says that win on disc is not the same as is installed, even if they should be same.

---

### Post by oldfred on 2015-04-15
Try chkdsk.
Windows has to have the same start & size info in the partition boot sector as the partition table. Chkdsk from Windows will update that info. And you should be able to use any newer version to run just the chkdsk fix.

---

### Post by QDR06VV9 on 2015-04-15
@oldfred Do you think this link might be better for OP 
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)
Hope I am not stepping on toes here
Respectfully

---

### Post by jacky6 on 2015-04-15
i will try chkdsk, i had problem between steps 5 and 6 in this tutorial [https://kb.wisc.edu/page.php?id=6565#CD](https://kb.wisc.edu/page.php?id=6565#CD) when i wanted to recover from disk so im not sure if i will be able to run it. i will try it with newer version. 
i tried rescue data with gparted but it still running.

---

### Post by oldfred on 2015-04-15
Sometimes the full set of repairs is needed. And runrickus' link is also a good one. And Windows command prompt (terminal) is often better than the auto fix. The autofix also has to be run 3 times.

And sometimes you have to run chkdsk until no errors, for it to fully correct everything.

---

### Post by jacky6 on 2015-04-15
gparted finished right now but with no result, so im going to try chkdsk. my priority is not to load win, but first of all rescue files. i can see partition which i want to rescue with fdisk command, it is a hidden ntfs. isnt there a way how to mount it to backup files? and then i would format whole disk and create clean instalation.

---

### Post by oldfred on 2015-04-16
Does Ubuntu file manager Nautilus mount it?
If damaged can you force mount read only?
Or can you see files with testdisk and copy them to another drive?

       mkdir /media/win
sudo ntfs-3g -o ro /dev/sda1 /media/win
# remount read only This worked for my mp3 player that default mount would not write to
# sudo mount ntfs-3g /media/PEARL -o remount,rw,noatime


 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Testdisk is in repository, so easy to add to Ubuntu live installer.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
      
 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by jacky6 on 2015-04-16
great, testdisk see partitions and is able to backup files. thank you very much:) after files will be copied to external hdd i try the step by step manual to repair partition table as you posted. if it not work i probably try to do clean instalation. i am grateful for files backup, if it would boot as before it would be a bonus

edit: after i writed partition table and restart computer, this statements appeared: reboot and select proper boot device or insert boot media in selected boot device and press a key. when i boot from live cd i see all partitions, so maybe upgrade/instal grub should fix it?

---

### Post by QDR06VV9 on 2015-04-16
Good Job jacky6;) Looks like you learned something new! Thats always a good thing!
I rarely suggest a new install but in your case with 2 broken windows partitions(?)  and a ubuntu partition
that might be the best way to insure a clean OS and bootable drives. 
Good News you got your data recovered.
Regards

---

### Post by jacky6 on 2015-04-16
i know it seemed to be hopeless, but i againd tried boot-info and i think problem should be with ubuntus grub - here is output from boot-info [http://paste.ubuntu.com/10833755/](http://paste.ubuntu.com/10833755/). previously also gparted did not recognized partitions, now it is ok - but there is and exclamation mark in sda3 line. i also see partitions in explorer - i can acces two ntfs partitions, ext4 partition is visible but it say this when i try to open it: 

Error mounting /dev/sda3 at /media/lubuntu/ubuntu: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda3" "/media/lubuntu/ubuntu"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

i know that im pain in ass:) im sorry for that

---

### Post by oldfred on 2015-04-16
Normally you do not install grub to a partition, it really does not fit, and converts to blocklists which are unreliable.

Did you convert sda to gpt, your installs are BIOS and Windows only boots from MBR(msdos) with BIOS boot mode.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

Did you have an abnormal shutdown in Ubuntu? Power failure or forced shutdown? That often causes corruption and fsck then required to repair damage.  Never force reboot without remembering the elephants. 

      
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

      
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by jacky6 on 2015-04-17
Well thanks you guys, i was never to linux stuffs and i admire your knowledge, thats really something...in the end i rather made new instalation, everything is going fine. thanks you again

---

### Post by oldfred on 2015-04-17
If you have good backups of your data, list of installed apps and not much configuration, then a re-install often is a quicker way to 'fix' things.

---

