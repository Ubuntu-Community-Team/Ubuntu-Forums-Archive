---
title: "Accessing Windows Disk"
date: 2006-12-21
forum: General Help
---

### Post by griffo on 2006-12-21
Hi im wondering how I can access the windows disk or what ever its called from a live kubuntu disk.  I need to pull off a program off windows because i can't get on windows because I will get a blue screen of death :mad: :mad: :mad: .  Any suggestions:confused: 

Thanks, Griff.

---

### Post by taurus on 2006-12-21
You need to mount it from a terminal...

```
sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hda1 /mnt/windows
sudo ls -la /mnt/windows
```
(assuming /dev/hda1 is what you want to mount...)

---

### Post by gunnar123 on 2007-01-07
I've been able to rescue the contents off a Windows XP Home disk using Ubuntu.
It was a case where the XP registry became corrupt and only a full reinstall (and drive reformat) was the option left for cleaning up XP. But first I wanted to rescue all the user files.

I attached an external (DOS formatted) USB hard disk to the machine and booted from the Ubuntu CD.  Ubuntu finds and mounts the USB hard disk automatically but usually not the Windows hard disk. 
It seems you need to do that manually.
The external USB drive needs to be in DOS format (not NTFS) in order for Ubuntu to mount it in writeable mode but the Windows drive may be NTFS (and will be read only).

The following worked for me :

sudo mkdir /mnt/windows
sudo mount -t ntfs /dev/hda1 /mnt/windows -o rw,nosuid,iocharset=utf8,uid=999,gid=999,umask=077

You can then (as a non-root Ubuntu user) use the ordinary Ubunty File Manager to browse /mnt/windows and then do copy/paste between the windows drive and the external hard drive. This worked just fine after I settled for the above described mount parameters.

In my case (XP Home) it was also possible to rescue the content of the files under My Documents for all users, I seem to have noticed on XP Professional the file system may prevent access to those folders.

/gunnar

---

