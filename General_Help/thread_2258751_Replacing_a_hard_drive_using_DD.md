---
title: "Replacing a hard drive using DD"
date: 2014-12-30
forum: General Help
---

### Post by CaptainMark on 2014-12-30
I've never replaced my hard drive before but my current one is full and I've a replacement on order from Amazon. I'm familiar with the use of dd and I have a backup external drive which is large enough to contain a complete copy of my current hard drive, best I can figure these are the correct steps to use but can someone with more experience give a quick critique of this method before I even start
1. dd the current hard drive /dev/sda onto the backup drive as an .img file /media/passport/current.IMG
2. Power down the PC and replace the old drive with the new drive
3. Boot up a live CD, mount the external drive and the new hard drive
4. dd the .img file to the new hard drive
5. Still using the live CD edit the new hard drives /etc/fstab to refer the the new drives uuid
6. Expand the unmounted partition on the new hard drive using gparted
7. Reboot

If anyone has better/easier methods please feel free to comment
Any toughts?
Regards
Mark

---

### Post by sudodus on 2014-12-30
***dd*** is nicknamed 'disk destroyer' because there is no safety. A mistaken drive letter or a typing error, and you wipe your family pictures. But it is very powerful and can certainly do the job you want to do.

***Clonezilla ***is a tool with reasonable safety. It will ask questions: 'Do you really want to ...' so it gives you a second chance to find mistakes. And there is a wizard, that will help beginners. Actually, I still prefer the beginner mode after using it several years.

Get the current stable version (an iso file for a live system) :-)

Furthermore, Clonezilla does not copy unused blocks, so it is much faster than dd, particularly if there is a lot of unused space on the source drive.

You can either make a compressed image (actually a number of files in a directory in the target drive), or you can clone directly.

Advantages with the compressed image:
- In your case you will get a full backup 'automatically' as a by-product.
- Generally, for backup purposes, it will be much smaller than than a cloned copy.

---

### Post by pqwoerituytrueiwoq on 2014-12-30
if you connect both HDDs at the same time you can do [FONT=courier new]dd if=/dev/sda of=/dev/sdb[/FONT]
instead of updating UUIDs in /boot/grub/grub.cfg and /etc/fstab you can use tunefs to change the UUID to the UUID you had (does not work on swap last time i tried)
DD will clone your UUIDs
this post also covers how to clone using gparted and cp
[http://ubuntuforums.org/showthread.php?t=2257603&p=13191459#post13191459](http://ubuntuforums.org/showthread.php?t=2257603&p=13191459#post13191459)

---

### Post by oldfred on 2014-12-30
I am still a fan of new install and restore /home.

DD is for same size to same size drive copy. You new drive will then be the same size as your old drive and you have the issue of moving data on drive with gparted. Moving a lot of data around will take a long while and has some risk. Best to do that before any changes in case you have to redo things.

Also with new install you automatically house clean out all the cruft. You should do that anyway before copying data just to avoid copying data that is not important.
 Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

How large is new drive. If over 2TB, it has to be gpt and you cannot use dd to copy from MBR(msdos) to gpt partitioned drive.

---

### Post by CaptainMark on 2014-12-31
Thanks for the input so far

@sudodus so there is a quicker way but I'll stick with dd because as I mention, I'm familiar with it, I'm confident that I won't make such a mistake like erase a drive, I've used dd a lot before so I know the risks but all my data files are always backed up triplicate just in case

@pqwoerituytrueiwoq I haven't got an extra sata cable but I may invest in one to save me the time of dd'ing twice

@oldfred Normally I would do a fresh install but right now I'm really happy with my system setup and could do without the hassle of a new system, we've all done it before I expect and there is always always one little thing which you forget to copy, even if you have it scripted there's always some little hidden directory somewhere which you didn't have last time you used that script and you don't find out until 3 months down the line you go to play that little indie game you like and realise you've not copied the save file over, grrrrr. It's my backup option if the plan A doesn't work.

The new drive is a 2TB drive, I didn't know about the limit on MBR are there other advantages to using GPT, if so I may reconsider a re-install.

Regards
Mark

---

### Post by sudodus on 2014-12-31
MBR (alias MSDOS partition table) works up to and including 2 TB, so OK in your case. But GPT (alias GUID partition table) is more modern and can do more, not only manage larger disks, also it is not limited to four (primary) partitions, so you need not fiddle with extended (and logical) partitions. It is also necessary, if you want to boot into the drive in UEFI mode. *Oldfred* will probably add some more advantages ... and you can find more details via the internet (for example wikipedia).

[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by pqwoerituytrueiwoq on 2014-12-31
> **CaptainMark said:**
> 
@oldfred Normally I would do a fresh install but right now I'm really happy with my system setup and could do without the hassle of a new system, we've all done it before I expect and there is always always one little thing which you forget to copy, even if you have it scripted there's always some little hidden directory somewhere which you didn't have last time you used that script and you don't find out until 3 months down the line you go to play that little indie game you like and realise you've not copied the save file over, grrrrr. It's my backup option if the plan A doesn't work.

The new drive is a 2TB drive, I didn't know about the limit on MBR are there other advantages to using GPT, if so I may reconsider a re-install.

Regards
Mark
  youcan still clone from mbr to gpt, use gparted to copy partitions then fix grub
[FONT=Courier New]sudo grub-install --force --no-floppy --boot-directory=/media/NEW/boot /dev/sda[/FONT] (replace NEW and sda as necessary)
not sure if you can do that with windows (i no longer use windows at all)
i use it once and a while and don't bother to type the license key cause it is a pain, that should tell you how little i use it (still need it to oc my cpu and stress test)

---

### Post by oldfred on 2014-12-31
I started makeing all new drives gpt back with 10.10 as even then UEIF was just starting (Mac then) and I had planned an a new system in a year or two that would be UEFI. Just built it last month, for so much about plans.

Actually minor advantages for gpt, but if you may later move drive to a new system, then you should plan conversion now. If not for a couple of years then staying with MBR should be fine, as you would want new drives with new system anyway.

Drives can be converted from MBR to gpt or vice versa with gdisk, but there are some partition spacing requirements and reinstall of grub and adding bios_grub partition. Have not tried that as I kept old MBR drive as MBR until I converted and copied all its data to my new system.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

I do try to make my backups include everything I would need for a new install. And now only do clean installs, but keep old install, so I can go back and get anything I forgot, but then add that back into my list of things to backup.

---

### Post by CaptainMark on 2015-01-04
Thanks for all the tips guys, I have got my drive installed and am going to stick with MBR for the time being because everything just worked using DD, however my new backup drive I have done as GPT and there were no hassles there so when it's time for a new install of my desktop (16.04) I'll reformat with GPT.

---

