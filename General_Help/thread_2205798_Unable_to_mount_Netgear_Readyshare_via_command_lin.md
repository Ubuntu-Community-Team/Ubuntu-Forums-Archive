---
title: "Unable to mount Netgear Readyshare via command line"
date: 2014-02-16
forum: General Help
---

### Post by CaptainSchnitz on 2014-02-16
Hi - I have just bought a Netgear N300, which can connect to an external USB hard drive. I can access the USB drive via Nautilus at: 

[HTML]smb://192.168.3.1/usb_storage[/HTML]

It will then show up in Nautilus, mounted at ~/.gvfs with read/write access.

However, mounting via the command line so far eluded me. I want to mount the drive to the directory /media/MEDIA - when I try to do so via any of:

```
sudo mount -t smbfs //192.168.3.1/usb_storage /media/MEDIA -o sec=none
sudo mount -t cifs //192.168.3.1/usb_storage /media/MEDIA -o sec=none
sudo smbmount //192.168.3.1/usb_storage /media/MEDIA -o sec=none
```

I get the following:
```
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I tried gvfs-mount to see what would happen:
```
gvfs-mount smb://192.168.3.1/usb_storage /media/MEDIA/

Error mounting location: volume doesn't implement mount
Error mounting location: volume doesn't implement mount
```

Any suggestions? I am running Ubuntu 12.04 LTS; the USB drive is formatted FAT. I want ultimately to be able to mount via /etc/fstab - this machine usually runs headless.

---

### Post by wiremoons on 2014-02-16
Hi CaptainSchnitz

There is a Netgear forum that has a posts from others trying to mount their devices in Ubuntu - you could give it a look in case it helps?

Mounting CIFS share on Ubuntu: [http://www.readynas.com/forum/viewtopic.php?f=23&t=69765](http://www.readynas.com/forum/viewtopic.php?f=23&t=69765)

and there is the thread below on the Ubuntu forms, that is similar issue that someone else was having with their N300 too:

Mount usb drive attached to N300 wireless N netgear router: [http://ubuntuforums.org/showthread.php?t=1651160](http://ubuntuforums.org/showthread.php?t=1651160)

Hope they help!

---

### Post by CaptainSchnitz on 2014-02-17
Thanks for the reply. Unfortunately the linked forums didn't have what I was after, but following a bit (several hours :sad:) more Googling, I found a similar-ish issue that the user of another distro seemed to be having. The technical content was a bit above my newb-ish head, but it seems to be an issue with kernels of version 3.8 and above needing to be manually directed back to an older form of security for cheapo SMB solutions like Readyshare.

For the benefit of posterity and for any others having similar problems, the trick was adding [FONT=Lucida Console]**sec=ntlm**[/FONT] to the mount command. The following resulted in a successful mount:

```
sudo mount -t cifs //192.168.31/usb_storage /media/MEDIA -o sec=ntlm
```

Equivalent settings in /etc/fstab also worked, which is making me very happy. Was worried that I was going to have to leave it booted into Gnome and access via ~/.gvfs, which seemed a decidedly inferior sort of solution.

---

### Post by Keith_Watson on 2014-06-12
Perfect, many thanks CaptainSchnitz, just what I was looking for. :D

---

