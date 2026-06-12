---
title: "copying mp3 files to my xp drive"
date: 2006-10-08
forum: General Help
---

### Post by howardepgco on 2006-10-08
I want to copy a bunch of mp3 music I have in Ubuntu to my XP drive.Can I do that? If so how?

---

### Post by marianom on 2006-10-08
Is it a dual boot machine? Is it networked?

---

### Post by LORD_PoLvO on 2006-10-08
if its duel boot just mount ur xp drive if its networked just set up a samba file sharing network

---

### Post by howardepgco on 2006-10-08
How do I set up a Samba network? I have not heard of Samba.

---

### Post by Medieval_Creations on 2006-10-08
One option to is to use ntfs-3g to mount your XP drive with read/write capabilities...

Link to HOWTO:  [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

that's how I copy all mine over...

---

### Post by spvo on 2006-10-09
I would not recommed writing to your XP drive from linux.  Writing to NTFS (the windows file structure) is not perfected in linux.  You can create a fat partition, which both linux and windows can read or write to.  However, I think the easier solution is to install [fs-driver.org]("http://www.fs-driver.org/index.html").  It allows you to mount a linux partition from inside XP.  That way you can boot up windows and have complete access to your linux partition.

---

### Post by jalm111 on 2006-10-09
Writing to NTFS from Linux = Bad Idea. Go with what spvo said.

---

### Post by howardepgco on 2006-10-09
O.k I installed the software and I can now see the drive, however, when I click on the drive it tells me that the drive is not formatted do I wish to format it now.I can't get any further than this.What do I do next?

---

### Post by Jongi on 2006-10-09
Post the output of:

1. fdisk -l
2. cat /etc/fstab

---

### Post by givré on 2006-10-09
> **jalm111 said:**
> Writing to NTFS from Linux = Bad Idea. Go with what spvo said.
Did you guys ever tried ntfs-3g? You would be surprise.

---

### Post by Medieval_Creations on 2006-10-09
ntfs-3g has come along way... I've been using it for over 6 months now and I've never had a problem with loosing or corrupting data.

I move DVD ISOs back and forth between my windows and ext3 drives so a shared fat partition doesn't work.  I had to find a way around so I could use an ntfs partition.

Also if I can do it in Linux and avoid winblows I will...

---

### Post by Medieval_Creations on 2006-10-09
> **howardepgco said:**
> O.k I installed the software and I can now see the drive, however, when I click on the drive it tells me that the drive is not formatted do I wish to format it now.I can't get any further than this.What do I do next?

Which software did you install?

---

### Post by howardepgco on 2006-10-09
Ok Jongi here is the results you asked for.

howardepgco@desktop:~$ fdisk -l
howardepgco@desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1 /media/windows ntfs umask=0222 0 0
howardepgco@desktop:~$
Beats me what it all means. I assume you know:p

---

### Post by howardepgco on 2006-10-09
Medieval_ Creations,

I installed the fs-driver.org software.

---

### Post by Medieval_Creations on 2006-10-09
Where you in the fs-driver program (opened through the Control Panel)?  Because when I open it on my PC it just has me set the drive letters for the linux partitions and after a few seconds they show up under my computer and I can do things as usual from there.

I'm not sure why it would be asking you to format the drive.

Also try sudo fdisk -l...
the output should look something like this
```

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1912    15358108+  83  Linux
/dev/hdb2            1913        3187    10241437+  83  Linux
/dev/hdb3            3188        3569     3068415   83  Linux
/dev/hdb4            3570       19929   131411700    5  Extended
/dev/hdb5            3570        3824     2048256   82  Linux swap / Solaris
/dev/hdb6            3825       19929   129363381    7  HPFS/NTFS

```

---

### Post by taelatus on 2006-10-09
Greetings all.  Thanks to the person who posted the link to [http://www.fs-driver.org/](http://www.fs-driver.org/).  I was wondering if this type of solution was available in Windows.  I have one question before I download however.  Can I be certain that the fs-driver won't hose my XP installation and/or my Ubuntu installation?

---

### Post by Medieval_Creations on 2006-10-09
> **taelatus said:**
> Greetings all.  Thanks to the person who posted the link to [http://www.fs-driver.org/](http://www.fs-driver.org/).  I was wondering if this type of solution was available in Windows.  I have one question before I download however.  Can I be certain that the fs-driver won't hose my XP installation and/or my Ubuntu installation?

I haven't had any problems with using it.  That's not to say something can't happen.

I still recommend ntfs-3g, but I do use fs-driver when I am in windows and it gets the job done.

---

### Post by howardepgco on 2006-10-09
Thanks Medieval,you were right on.I had no idea that the program was accessed through control panel.When I checked in there I had the linux drive letter set to the same as my camera usb drive.I simply moved the drive letter up and bingo it worked like a charm. Hey to everyone that posted, thanks so much for your time and sharing your experience.

---

### Post by Medieval_Creations on 2006-10-09
> **howardepgco said:**
> Thanks Medieval,you were right on.I had no idea that the program was accessed through control panel.When I checked in there I had the linux drive letter set to the same as my camera usb drive.I simply moved the drive letter up and bingo it worked like a charm. Hey to everyone that posted, thanks so much for your time and sharing your experience.

No Worries... :D

---

