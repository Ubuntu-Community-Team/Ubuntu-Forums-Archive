---
title: "Changing name of Windows volume icon on desktop?"
date: 2007-10-30
forum: General Help
---

### Post by bg1256 on 2007-10-30
I am dual booting Gutsy and XP Media Center edition, and Gutsy is successfully mounting my Windows volume at startup.

However, it displays its name as: HP_PAVILION.

I would like to change this to Windows XP MCE, if possible.

How can I go about doing this?

---

### Post by Fidgel on 2007-10-30
Sounds to me like it is using the Windows Volume Name.  Don't know if you can do it from Linux, but boot Windows and change the volume name, then see if it changed in Linux.

---

### Post by nick_h on 2007-10-30
Create a directory called /media/Windows XP MCE
```
sudo mkdir "Windows XP MCE"
```
Then edit /etc/fstab
```
gksudo gedit /etc/fstab
```
and change the mount point to /media/Windows\040XP\040MCE

---

### Post by Fidgel on 2007-10-30
Hey nick_h was I completely wrong on the volume name bit?  Learn something new every day.  Mine just says "disk"

---

### Post by dcstar on 2007-10-31
> **bg1256 said:**
> I am dual booting Gutsy and XP Media Center edition, and Gutsy is successfully mounting my Windows volume at startup.

However, it displays its name as: HP_PAVILION.

I would like to change this to Windows XP MCE, if possible.

How can I go about doing this?

For DOS/FAT:
[http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)

For NTFS, install the** ntfsprogs** package and then use the **ntfslabel** utility that comes with it.

---

### Post by bg1256 on 2007-10-31
Thanks, dcstar.

---

### Post by bg1256 on 2007-10-31
Well, I've just dl'd and installed ntfsprogs, and it looks like there is some interesting stuff.

However, I can't figure out exactly how to get ntfslabel working for me.

I read the man pages [here]("http://man.linux-ntfs.org/ntfslabel.8.html").

The relevant information about my system would be here:

My windows volume is /media/sda1 and the label is HP_PAVILION.

---

### Post by nick_h on 2007-10-31
> **Fidgel said:**
> Hey nick_h was I completely wrong on the volume name bit?  Learn something new every day.  Mine just says "disk"

I think that the name is taken from the mount point and that mount points under /media are  displayed on the desktop and under "Places".  The volume label is probably used during installation to create the initial /etc/fstab file.  Changing the label is more useful for removable devices rather than fixed ones like a Windows partition.

I think that the OP will see a line in the fstab file similar to:
```
# /dev/sda1
UUID=????? /media/HP_PAVILION     ntfs    defaults,umask=007,gid=46 0       1
```

If this is the case then it is just a matter of creating a new mount point and editing this line.  The only complication is that you have to escape the space characters.

It might be a good idea to make a backup first with:
```
sudo cp /etc/fstab /etc/fstab.old
```

Then the partition can be unmounted using:
```
sudo umount /dev/sda1
```
and re-mounted using:
```
sudo mount /dev/sda1
```
no need for a reboot.

---

