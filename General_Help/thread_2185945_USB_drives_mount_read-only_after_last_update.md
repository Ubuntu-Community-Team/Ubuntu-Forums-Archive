---
title: "USB drives mount read-only after last update"
date: 2013-11-05
forum: General Help
---

### Post by DrScum on 2013-11-05
With one of the last updates a problem with usb drives was introduced to my system. I am running a 12.04 LTS system. Yesterday I recognized that all USB-drives mount with a read-only file system and can't be written to even if I start nautilus with gksudo from the terminal or if I start Gnome Commander as root.

The drives I was testing work normally on a Lubuntu 13.10 box (i.e. they are automounted and can be written to by a standard user).

Does anybody know how to fix this?

---

### Post by DrScum on 2013-11-05
I seem to have the same problem as dxgrimm

output of my mount command:
/dev/sdb1 on /media/DrSCUM type vfat (ro,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

as you see, its ro

I'd like to mention that I didn't have problems with the usb drives until a few days ago, so I assume this problem was introduced with a recent update.

here the output of ls -l /media
drwxrwxrwx 3 DrSCUM root  4096 Nov  4 21:41 sdb1

here I have to explain that I tried to change owndership using the chmod command to fix the problem thus ownership could be messed up by that

here the output of getfacl -tn /media/sdb1
getfacl: Removing leading '/' from absolute path names
# file: media/sdb1
USER   1000      rwx     
GROUP  0         rwx     
other            rwx

---

### Post by coffeecat on 2013-11-05
I've moved your post to its own thread. Please start your own threads. Yours is a different problem seeing as your drive is being mounted read only.

Have you installed any "helper" applications for mounting usb drives?

Is this the only device that is being mounted read only?

---

### Post by DrScum on 2013-11-05
I didn't install any "helper" applications between the time when usb drives mounted "normally" and now and every single usb drive I insert shows the same behavior. I just found out, when I open nautilus from the terminal with the sudo command the drive behaves normally. Thus the problem seems to be related to permissions

---

### Post by SeijiSensei on 2013-11-05
Linux will not mount a device as writable if it has file system errors.  Unmount the device and run "fsck -t vfat /dev/sdb1" to run a check.  If you have a Windows machine available, I'd use Windows chkdsk instead.

---

### Post by DrScum on 2013-11-05
Right after I discovered the problem I tried to reformat the USB drive using G-parted. I deleted all partitions and created new ones. I created linux partions followed by fat16, fat32 and ntsf the problem persisted. Besides, the drives work well with a Lubuntu 13.10 box.

---

### Post by oldfred on 2013-11-05
I have 12.04 and it is up to date. I just plugged in a flash drive with FAT32 partition. It is rw:

/dev/sde1 on /media/C0CC-4E19 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

If you did format with Linux then you would have to set ownership & permissions, but with FAT or NTFS you only have the defaults.

---

### Post by oldfred on 2013-11-05
Merged duplicate thread.

---

### Post by DrScum on 2013-11-06
@oldfred Question 1: what does "merged duplicate thread imply?" I was already "moved" by coffeecat! Did I do something wrong here?

Question 2: What do you mean by "I have 12.04 and it is up to date. I just plugged in a flash drive with FAT32 partition. It is rw:" 

the output of MY mount command (as already posted above):
/dev/sdb1 on /media/DrSCUM type vfat (ro,nosuid,nodev,uid=1000,gid=1000,shortname=mixed ,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

this seems to be identical with yours! However, in my system I can't write to the drive I get the message: "read only file system"

---

### Post by coffeecat on 2013-11-06
> **DrScum said:**
> @oldfred Question 1: what does "merged duplicate thread imply?" I was already "moved" by coffeecat! Did I do something wrong here?

You started your own thread and hijacked someone else's thread a few hours later. That's called cross-posting, and is frowned on in all forums. When I moved your post out into its own thread, I didn't notice your separate thread otherwise I would have moved your post into your thread, as oldfred has now done.

---

### Post by oldfred on 2013-11-06
I do not know enough about the inner workings of Nautilus and how it auto mounts a flash drive. I was just posting that is does work for me, so I do not think it is a major bug, but something unique to your configuration. 

I think it is udisks and it has a command to output drive data. With several drives & many partitions it scrolled off my terminal, so I had to output to text file.

udisks --dump > diskdump

Not sure if that will help or not, hopefully someone that knows more about flash drive mounting will chime in.

---

### Post by DrScum on 2013-11-07
@coffecat: afaik I didn't start my own thread before I posted to dxgrimms thread (post 12840199), if I did anyway, it was unintentionally and definitely not to "highjack" or to to do any other kind of harm. The Problem of newly mounted drives being read only as you can imagine is pretty serious, since it also affected network shares they too were mounted readonly. That's why I was kind of desperate to find a solution since normal work wan't possible anymore.

In the meantime I found out what happened: the ownership of the folder /media apparently was changed and I am pretty shure that this happened during one of the recent upgrades since the symptom occured on two machines both running Ubuntu 12.04 LTS and both having been updated recently. 

The fix simply was to change ownership of /media. Since I don't know better I used the command chmod -R /media 777 which I think gives total access to everyone to the directory /media and all files and folder included in /media. Definitely the usb drives and the network shares are mounted writeable now.

For clarification, afaik: newly mounted drives are mounted to /media/<newdrive> Thus if the user doesn't have write access to /media he can't have write access to folders included in /media.

---

### Post by TonyWallace64 on 2014-04-16
I have had the same experience and followed the advice above.  After doing the chmod +R 777 /media, dismounting and reinserting the USB drive still could not write to USB via Nautilus.  However command line access was working.   Using the command line I completed the task I was attempting, but it does point the finger towards Nautilus.

---

