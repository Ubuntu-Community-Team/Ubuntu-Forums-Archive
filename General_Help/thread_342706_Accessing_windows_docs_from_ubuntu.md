---
title: "Accessing windows docs from ubuntu"
date: 2007-01-20
forum: General Help
---

### Post by mrwooster on 2007-01-20
Hi,

I am using a dual boot drapper - winXP system - but want to keep most of my documents such as pics, music and work in the my documents folder on the windows partition so I can still access it when I run windows XP.

Currently, it seems that only the root user can modify files on the windows partition - what is the best way of getting round this? I am slightly worried about running chmod -R 777 /windows in case it screws up my win installation.

What I want to be able to do is create a link on my desctop to my documents, and be able to edit all the files as my default user.

Any ideas?

Thanks

Guy

---

### Post by haiku99 on 2007-01-20
a very simple way would be to keep the stuff you want to share on a USB flash drive, IME this works well, XP and Ubuntu read and write to it no problem, just remember to eject it before removing and that Ubuntu sends deleted files to a hidden trash folder...

---

### Post by mrwooster on 2007-01-20
Thanks for the suggestion but I need something a bit more permanent, i.e. I want to be able to edit files which are already in my documents. I also have a large amout of files (approx 5GB).

---

### Post by dexter on 2007-01-20
What file type are you using on your windows disk, FAT32 or NTFS ?

---

### Post by mrwooster on 2007-01-20
Ntfs

---

### Post by dexter on 2007-01-21
Ubuntu cannot write ntfs partitions by default. You'll have to install the ntfs-3g driver. Here's a manual i found: [http://doc.gwos.org/index.php/NTFS-3g](http://doc.gwos.org/index.php/NTFS-3g)

---

### Post by JonRohan on 2007-01-21
> **dexter said:**
> Ubuntu cannot write ntfs partitions by default. You'll have to install the ntfs-3g driver. Here's a manual i found: [http://doc.gwos.org/index.php/NTFS-3g](http://doc.gwos.org/index.php/NTFS-3g)

I didn't think NTFS write support in Linux was complete? Isn't it still in beta and not recommended for live systems?

---

### Post by dexter on 2007-01-21
> **JonRohan said:**
> I didn't think NTFS write support in Linux was complete? Isn't it still in beta and not recommended for live systems?

The old implementations were indeed not very stable. ntfs-3g is a new implementation, I don't use it myself but I haven't heard any complains about it.

---

### Post by heinkel_111 on 2007-01-21
The other alternative of course is to switch the partition where your windows documents are installed from NTFS to VFAT. This would not be to cumbersome if you had a third partition where you could back all the documents up to. 

Upgrading from VFAT to NTFS in windows is a click on a button and some waiting (MS has a solution for this), going the other way is manual work: you must backup the content of the NTFS drive (to anoter partition), then reformat the NTFS partition as a VFAT partition, finally restore your backed up documents on the VFAT partition.

It's not an awful lot of fun, but it can be done!

---

### Post by grfd703 on 2007-01-21
I feel your pain, but a word of advice.  Try to keep data that you're not willing to lose off of your OS partition.  Personally, I keep all of my personal data, (music, pictures, office files etc. ) on an external HDD (usb).  I formatted it in FAT32 so that it could be modified by ubuntu as well as windows.  This really is the easiest way to store your data.  External HDD's have come down so far in price that it really is a viable alternative and one that I recommend highly. 

Jim

---

