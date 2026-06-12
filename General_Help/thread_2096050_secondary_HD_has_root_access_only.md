---
title: "secondary HD has root access only?"
date: 2012-12-18
forum: General Help
---

### Post by Heeter on 2012-12-18
Hi all,

I installed a 500GIG HD as a secondary HD in my 12.10 64bit machine.

Ubuntu does recognize it, but only root has privileges for it.

How can I change so that I have read/write privileges on it?

Thanks

Heeter

---

### Post by TOMBSTONEV2 on 2012-12-19
sudo chown "user name" /media/drive name          or
sudo chmod 777 /media/drive name

That should get it going.

---

### Post by mastablasta on 2012-12-19
or open nautilus with root privileges 
 
gksu nautilus
 
and then right click on drive and change it's ownership at propperties.

---

### Post by oldfred on 2012-12-19
Is this a permanently installed drive or external drive?

What format is partition(s)? 

If NTFS TOMBSTONEV2's suggestion will not work, but otherwise should work.

But generally better to permanently mount with fstab if permanently installed drive.

       Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

    
Copy template into fstab and edit with your UUID & mount point.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6


More details & Understanding fstab
[       ]("https://help.ubuntu.com/community/Fstab")
 [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

---

### Post by Heeter on 2012-12-19
Sorry about that,

This is a EXT4 formatted, internally SATA installed 500GIG HD.

Thanks for all your responses


Heeter

---

### Post by rnerwein on 2012-12-19
> **TOMBSTONEV2 said:**
> sudo chown "user name" /media/drive name          or
sudo chmod 777 /media/drive name

That should get it going.
hi
never ever use 777 by chmod  use 755 or may be 775 it's ok. 777 is for the world !!
cheers

---

### Post by TOMBSTONEV2 on 2012-12-19
777 does not allow some random joe from the internet to access your drive, it just allows everyone who logs onto the computer to have access to the drive. So if you have multiple accounts and users than that may pose a security risk. 

If this was for a web server than yeah, 755 that sucker. But hey do whatever feels best for you. That's the nice thing about Linux.

---

