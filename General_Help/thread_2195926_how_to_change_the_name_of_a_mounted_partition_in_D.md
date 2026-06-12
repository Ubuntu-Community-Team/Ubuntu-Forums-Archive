---
title: "how to change the name of a mounted partition in Dash?"
date: 2013-12-27
forum: General Help
---

### Post by clearski on 2013-12-27
I was wondering if it's possible to change the name of a partition as it is shown by the Dash from it's default mount name ("160 GB Volume") to a customized string?

The partition is located on the hdd the machine boots from and is mounted via /etc/fstab for a specific user only.

Thank you.

---

### Post by mikewhatever on 2013-12-27
You have to assign it a label. For example, if it's a linux partition (ext4), you could use **tune2fs**, or Gparted and Gnome Disk Utility. The latter are more user friendly with point and click GUIs. The former goes like this:
```

sudo tune2fs -L <label> /dev/sdXY

```

What file system does it have?

---

### Post by clearski on 2013-12-27
Hi, mike.

Thanks for your time. 

That partition is NTFS.

/etc/fstab:

```
UUID=XXXXXXXXXXXXX /media/WIN    ntfs    defaults,umask=007,uid=1005,gid=1005    0    0
```

I am looking for an unfriendly way to accompish that for now, so I guess tune2fs is what I need.

Would tune2fs would change the label permanently or do I have to run the command every time the machine boots?

---

### Post by mikewhatever on 2013-12-27
No, tune2fs won't work on a Wndows partition (NTFS). Something called ntfslabel might work according to [the wiki]("https://help.ubuntu.com/community/RenameUSBDrive").

---

### Post by fantab on 2013-12-27
Use the utility 'Disks' to change the NTFS label.

---

### Post by JOHNNYG713 on 2013-12-27
I believe you can use "Disk Utility" if you prefer a GUI  !

---

### Post by clearski on 2013-12-28
Thank you, everyone.

Solved using *Disks*.

Basically, it only required a string to be added in /etc/fstab:

```
UUID=XXXXXXXXXXXXX /media/WIN    ntfs    defaults,umask=007,uid=1005,gid=1005,**x-gvfs-name=[COLOR=#ff0000]winfiles[/COLOR]**    0    0
```

where [COLOR=#ff0000]winfiles[/COLOR] is the name given to the partition to be displayed as.

Nice... :)

---

