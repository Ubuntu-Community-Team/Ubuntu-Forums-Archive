---
title: "I lost hard drive permissions!!!"
date: 2007-02-27
forum: General Help
---

### Post by Unoone on 2007-02-27
What the freak!!!!!!!!!! I lost my fat 32 hard drive permissions in the middle of a crucial all night website download/upload.  Earlier I had set screem to superuser "Exec=gksudo screem" after I installed Xampp. It was all going fine for an hour or so downloading and updating files to the web. I have done this many times in the past over the two years I've used Ubuntu. I left the office and came back in the morning to this disaster.

Can I trust UBuntu not automatically to kill my permissions to my hard drive like this? Without "my" permission?! Especially during import web work tasks? I'm using Xfce 4. This is scary and unusual for me in my Ubuntu experience. Talk about an OS having a mind of it's own. Can some tell what happened here? I'm using Ubuntu Edgy. Thanks. Wow!!!

I did the - 

> sudo chown -R user:user /media

and

> sudo chmod -R 755 /media

I still can't write to the hard drive.

---

### Post by Unoone on 2007-02-27
I restarted the system and I have my write permissions back. Then I deleted the superuser setting for screem. I still won't trust using this computer for my web work until I know what happened. Anyone have any ideas? Thanks.

---

### Post by Unoone on 2007-03-02
Arrrrrgggggggggh! It's back again. My fat32 hard drive loses it's write permissions sporadically when I'm backing up data. I am no longer the owner of my drive. I restart my system and everything is fine for a while them, bam! I'm in trouble again. Things have been running fine for months and now this. My system reports no errors.  I'm using Edgy BTW. Can someone help me out here? Please! This is driving me crazy.:mad:

---

### Post by taurus on 2007-03-02
Did you mount that fat32 partition with /etc/fstab?

```
cat /etc/fstab
```
Does it have to be fat32 filesystem?

---

### Post by Unoone on 2007-03-02
> **taurus said:**
> Did you mount that fat32 partition with /etc/fstab?

```
cat /etc/fstab
```
Does it have to be fat32 filesystem?

Yes. Yes. Thanks for your reply. I have used Ubuntu for two years. I always share a fat32 drive with my windows system on this PC. I never experienced this problem with my previous Ubuntu installs until Edgy.

> /drive/  vfat    iocharset=utf8,umask=000 0 0

---

### Post by taurus on 2007-03-02
```
**/drive/** vfat iocharset=utf8,umask=000 0 0
```
That is the strangest entry for vfat that I have ever seen in /etc/fstab!  Can you post the whole /etc/fstab and the output of this command as well?

```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by Unoone on 2007-03-02
> **taurus said:**
> ```
**/drive/** vfat iocharset=utf8,umask=000 0 0
```
That is the strangest entry for vfat that I have ever seen in /etc/fstab!  Can you post the whole /etc/fstab and the output of this command as well?

```
cat /etc/fstab
sudo fdisk -l
```

Sorry.

> /dev/hdb1      /media/hdb1     vfat    iocharset=utf8,umask=000 0 0

sudo fdisk -l output-
 
>  Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    b  W95 FAT32


My entire fstab-

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=fb7ec44d-96d7-430a-8188-bab5052a23a5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=10D86459D8643F5A /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=329C9CB39C9C72D9 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6 /media/hda6 vfat iocharset=utf8,umask=000 0 0
# /dev/hda7
UUID=a3c33130-8ccc-41ec-8ce3-c86c93870758 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

# /dev/hdb1

/dev/hdb1      /media/hdb1     vfat    iocharset=utf8,umask=000 0 0

---

### Post by Unoone on 2007-03-03
Any idea as to what's causing this problem? Thanks.

---

### Post by Unoone on 2007-03-03
Could it be my kernel upgrade to 2.6.17-11 that caused the problem? Everything seemed fine until then.

---

### Post by Unoone on 2007-03-03
I rebooted the system again. About 15min running and root automatically took over my drive permissions right before my eyes. If this were windows I would respond to this behavior with a virus scan. I don't know what to do. I checked out other forums, nothing.

---

### Post by Unoone on 2007-03-03
Ok, a new thing. I tried dragging a web document folder from the /home/user/desktop to the fat32 drive. I got this error in part "Error "Invalid parameters" and the folder won't copy most of the contents.  This same folder copied in tact fine while running a Knoppix Livecd. When I booted back into windows and used Explore2fs the folder exported without any problems from the Linux partition to the fat32 drive.  I'm not a Linux expert but I know that there's some screw up in my Ubuntu system. I'm about ready to shut it all down at this point. I'm not used to this kind of behavior from core system properties in Ubuntu. I mean, it's Ubuntu.

---

### Post by ridgeland on 2007-03-03
Interesting...
I haven't had trouble with my FAT32 drives.  In /etc/fstab I use:
/dev/hda1	/WinXP			vfat	auto,users,rw,umask=0	0 0
/dev/hdb2	/z_FAT32		vfat	auto,users,rw,umask=0	0 0

/WinXP is my Windows partition, XP SP-1 not SP-2 which demands NTFS
/z_FAT32 is a data partition I share with my wife's PC via NFS, mostly photos and music.

If something kicks in after about 15 minutes, what do you find in the logs around that time?
System -> Administration -> System Log

---

### Post by Unoone on 2007-03-03
I did some back tracking and digging around. I deleted this and that or whatever. I don't know what was crapping up the joint. I remembered installing ntfs-3g some time ago I uninstalled any remaining libraries connected with it.  I would bake a 1million layer cake for anyone who creates a feature for Ubuntu like Windows system restore points. Tracking down problems can be a bit like slave labor in linux at times. Way to time consuming if you ask me. 

I was going to shut it all down, erase the drives and reinstall Ubuntu clean. Can't do that right now due to my work an all. This system has only been running on Edgy for 4 months. I usually don't reinstall an Ubuntu system until the next rock solid system upgrade. I never had this kind of behavior from an Ubuntu system before.  I'm thinking that maybe Edgy is a bit "edgy" at some points.

I "once" even did a custom kernel build for a Dapper system flawlessly.  That's as far as I ever went in terms of messing with the core Ubuntu system properties.  In every other case I have just installed needed software apps with aptitude, apt-get or synaptic. I never experienced any serious system hiccups like this one. I'm not crazy enough to run stuff like Beryl on a stable Ubuntu system setup. I have learned that it's better not to fool around with a stable Linux system.

I stopped using Fedora and Mandrake because of insane unexplainable unstable system behavior. Those systems were worse than running Windows XP in my case.  Up till Edgy Ubuntu has been  a mostly blissful computing experience. 

Hopefully this problem will just go away. I've been running the system today and so far I'm not getting the permission errors.  We'll see....................... I haven't fired up Xampp yet.

---

### Post by ridgeland on 2007-03-03
I missed the Windows system backup-restore function.  Although XP did not install it by default I always did.  I used Windows backup just for system state, about 400MB each time, always backed up before any software install or update.
My solution in Linux has been a partition backup which is everything.  So full and clean you can reinstall it on a new partition and be up and running in minutes.  In fact I use a clone copy for testing new software.  I try it, if I like it I install it on the main partition, if the software is a dog, like beagle, then it hasn't hurt my main install.  
My monthly routine is to backup all the data drives (rdiff-backup to external hard drive) and partimage of Ubuntu partition (about 3.5GB).  Space is not yet an issue for me so I like the comfort of the full partition backup and easy recovery.
I installed ntfs-3g on my wife's laptop with Fedora Core 6 and WinXP.  She has never complained about any read-write issues.
If I had troubles with read-write permissions I would test several options in /etc/fstab.

---

