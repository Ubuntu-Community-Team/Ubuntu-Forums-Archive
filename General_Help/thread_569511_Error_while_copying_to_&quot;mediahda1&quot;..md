---
title: "Error while copying to &quot;/media/hda1&quot;."
date: 2007-10-07
forum: General Help
---

### Post by oneloveone on 2007-10-07
I am trying to move some files to another hard drive in my computer put I get a pop up that says,

Error while copying to "/media/hda1". You do not have permissions to write to this folder.
can you please tell me how I can give my self permissions to write to this hard drive.

Thanks

---

### Post by 505 on 2007-10-07
What is the file system on that drive. If you dual boot with Windows, is that a windows drive. In that case it is probably NTFS, and you need NTFS drivers to write. These are called NTFS-3g (in the repositories). After installing, change the file /etc/fstab and change "ntfs" to "ntfs-3g" and reboot.

If it is a Linux drive (ext3), open a terminal, go to that directory (cd /media/hda1) and type:
sudo chown -R username:group
Change 'username' and 'group' to the appropriate values. In most cases they are the same, just you username with which you log on.

---

### Post by oneloveone on 2007-10-07
It is an NTFS hard drive that I have for storage pace.
Is there a program I can use to to get  permissions to to copy and past files to this hard drive.

Thanks

---

### Post by 505 on 2007-10-07
Permissions is not the problem, NTFS drives are read-only. If you use the NTFS-3g driver you also get write access to a NTFS drive.

---

### Post by bodhi.zazen on 2007-10-07
The easy way to do this is with ntfs-config

```
sudo apt-get install ntfs-config
gksu ntfs-config
```

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

