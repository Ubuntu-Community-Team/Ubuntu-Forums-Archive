---
title: "How to write files to a Windows harddrive using Ubuntu running from USB"
date: 2017-09-19
forum: General Help
---

### Post by gawardnz on 2017-09-19
Hi,
apologies if this is answered elsewhere, but I have had a thorough search on the web and this forum and cannot find an answer to this question.

This is something I have had trouble with a few times before and it's really frustrating when I am so close to fixing a problem at work. We have a number of industrial machines running XP and windows 7. Using a bootable USB stick with Ubuntu 16.04, I can see the (mounted) Windows drive and access the files etc. At the moment I have a corrupted font file (believe it or not) that needs to be deleted and replaced with a known good copy (which I have). However (and I think this is due to excessive file access restrictions on the part of Ubuntu) although I can see the file, I can neither copy over it, or delete it. I have tried changing the permissions for the entire hard drive (IE right click on the mounted drive, select properties and then try to change permissions) however this does not work. Doesn't come up with any errors, Ubuntu just rolls around for about a minute, and then reverts back to the original permissions. Likewise if I go to the folder or the file in question and try to change its permissions, same story. IE Ubuntu refuses to let me access any files on the windows volume, apart from seeing/reading them.

So basically, how do I change the permissions so I can freely modify the Windows files/folders when booted from USB using Ubuntu 16.04? Short of throwing the whole drive away and just starting again!

---

### Post by sotiris2 on 2017-09-20
How do you mount the drive? That affects who "owns" the drive since Linux-style ownership and permissions can't be set on NTFS. Which is why you can't change permissions.

If you just want to copy the file and since NTFS won't retain any owner/permissions data you can do it as root. I.E. ```
sudo cp /path/good/copy/font.tff /windowsdrivemounpoint/path
```

It is also possible that it is not a permission issue but Ubuntu cannot mount the filesystem because of Win7 fast startup which leaves it in a semi-hibernation state. Run mount while the disk is mounted and check if it's rw (read write) or ro (read only). In which case you will need to disable fast boot and shut down (not reboot) Win7.

---

### Post by Mark Phelps on 2017-09-20
First off, it's NOT "fast boot" as that is a UEFI option, not Windows.

Second, it's "Fast Startup" and that is NOT enabled by default in Windows 7.

---

### Post by gawardnz on 2017-09-20
Hi Guys,
thanks for the response. Firstly, the drive is already mounted when the USB stick (with a bootable version of Ubuntu 16.04 running on it) boots up the machine. I can see the drive there in the file view in the GUI. Furthermore, I can navigate the whole drive (including the Windows folder) and see everything there. Finally, in a terminal window I can see/navigate everything too. However trying to copy a file into a protected folder is impossible, as is deleting a file in a protected folder. I have had this same problem before, where I have tried to use Ubuntu to fix a broken Windows installation and where I can see the files/folders but not change anything. I'm not trying anything unusual, and in fact I'm certain anybody could replicate what I have done. IE boot your computer using a stock standard USB stick (Ubuntu 16.04 bootable) install, navigate to your Windows hard drive and try to delete a file from a protected folder, or try to change permissions for said folder or entire drive. No hassle reading from it, I can copy files freely, just no writing to the disk whatsoever.

Finally, the windows install is Windows XP (yes we really do have a number of industrial computers around our site running Win XP which for technical reasons cannot be upgraded...). Perhaps it has something to do with this.

---

### Post by mastablasta on 2017-09-21
are you running the file manager as root?

gksudo on ubuntu to run the file manager as root with full and all privileges.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

alternatively pkexec can be used: [http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html](http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html)

---

