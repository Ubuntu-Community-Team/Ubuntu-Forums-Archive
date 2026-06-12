---
title: "Ext3 Usb Drive Permissions"
date: 2007-02-11
forum: General Help
---

### Post by bigyoy on 2007-02-11
Hi

I've just partitioned a usb drive as ext3 which I want to use to swap between windows and linux using fs driver. However, I can't write files to it. The permissions are:

drwx------ 2 root root 16384 2007-02-11 15:04 lost+found

I can't work out how to change the permissions to allow me to write to this drive.

can anyone help - I'm very new to linux so sorry if this is obvious stuff!

---

### Post by racmar on 2007-02-11
to answer your question, you would use the chown command like this:
```
sudo chown 777 /(mount point)/lost+found
```
Please note, however, that this will enable ANYONE to read/write lost+found.  So, please read up on chown using ```
man chown
```

Now, why not just format it as FAT32?  FAT32 can access file sizes up to 2GB, and is natively supported on windows and ubuntu.  Also, I'm not too familiar /w using ext3 on windows, I've seen projects that let us use ext2 and ext3 is possible, but not fully supported ( journaling? ).  However, maybe there has been some improvements WRT ext3 I'm not aware of.

---

### Post by bigyoy on 2007-02-12
thanks for that - chown has done the job.

As for why, well it's complicated but essentially:

I had 2 (full) hard drives in my system and want to use Ubuntu + Windows (windows had died btw so i had to reinstall it but wanted to save my data). My second drive (D:\) is NTFS and full of media and games. I wanted to share a drive between windows and linux so had to buy a third drive (with usb caddy) to archive it off. Installed ext3 on it and used Ubuntu to access my NTFS partitions to backup all my important stuff so now, all my important stuff is on the ext3 usb drive. 

Then I took out the second drive in my pc and replaced it with the ext3 drive. I Partitioned and formatted the c:\ drive so it is windows and linux and used fs-driver to allow windows to access the ext3 drive. So basically I now have a windows and linux partitioned hard disk and another hard disk which is ext3 used for media storage and archiving. This is shared between windows and linux. I also have a spare external drive which will always come in handy :)

---

### Post by racmar on 2007-02-12
oops, I meant **chmod 777 /(mount point)/lost+found**

chown = change owner
chmod = change permissions

---

