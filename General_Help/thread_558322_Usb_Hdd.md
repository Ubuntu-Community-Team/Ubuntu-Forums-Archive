---
title: "Usb Hdd"
date: 2007-09-23
forum: General Help
---

### Post by djwhiplash on 2007-09-23
Hi,
I've just installed Ubuntu, it looks pretty nice I have to say, the only thing bothering me is that I have plugged in my UsB HDD and it is owned by Root, so I can't put anything on it.  How do I take   ownership of the drive.
Is it done using the CHMOD command and if so I need to be walked through the procedure as I am new to Linux.

Help appreciated.
Thanks.:(

Edit:

I should say that this is a new NTFS formatted drive.

---

### Post by Happy_Man on 2007-09-23
Hmmm... try the command ```
sudo chmod 1000 <mount point of drive>
```

---

### Post by djwhiplash on 2007-09-23
Cheers for the quick reply.
Tried that and it spat

chmod: changing permissions of `/media/Documents': Read-only file system

back at me and still unable to create folder etc..

---

### Post by MegaSvensk on 2007-09-23
Have you installed NTFS-3g? You need that to be able to write to a NTFS partition.

---

### Post by djwhiplash on 2007-09-23
Yeah,

Used the packet manager to install 3g and conf, can only see ntfs_conf in the system tools menu.  So I ran that and ticked the selection to enable writing.

no joy tho.

---

### Post by Happy_Man on 2007-09-23
Hmm... could you post the contents of your /etc/fstab here please? I'm getting a bit uneasy now....

---

### Post by djwhiplash on 2007-09-23
My FSTAB follows,

I have just tried removing the drive and plugging it back in and now it isn't recognised at all.

There are no files on the drive so this isn't a recovery situation, but I want to eventually share this drive on my network and it will have all my media/documents when I'm finished.

FSTAB:
[FONT="Courier New"][COLOR="Blue"][SIZE="4"]
proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=2b0a1b89-8843-4c56-8cca-d0c0099e37db / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=cbcda2e3-572c-4404-87fd-8317aa92174b none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0[/SIZE][/COLOR][/FONT]

---

### Post by djwhiplash on 2007-09-24
All sorted now, just had to reformat it in XP, plugged it back in again and hey presto there it is under /media/new volume.
It still says that it belongs to root but I am now able to create items within it.

Cheers for your help guys.

---

