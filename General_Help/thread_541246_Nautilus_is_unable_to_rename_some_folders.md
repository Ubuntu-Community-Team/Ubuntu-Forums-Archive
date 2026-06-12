---
title: "Nautilus is unable to rename some folders"
date: 2007-09-02
forum: General Help
---

### Post by Robbyx on 2007-09-02
I assume the problem is to do with permissions. The drive with the problem is hdb5. I do not know what is wrong, but the rename option on a right click of the folder is greyed out. Another problem is that I tried to create the new folder in a sub directory and instead of it appearing in it in was created in the main directory ie

My docs
  \clients
       \john
            \papers
opened papers and tried to create new folder. It did not appear in papers but did get created in john. I cut and pasted the new folder into papers and tried to rename it. I could not do so. It was greyed out.


editing fstab produced this:

robin@robin-desktop:~$ gksudo gedit /etc/fstab
(gedit:26200): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Fstab did open as follows:

proc /proc proc defaults 0 0
tmpfs /dev/shm tmpfs defaults,ro 0 0
# entry to make vmware player see usb devices. See
# [http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=2&docTypeID=DT_KB_1_1&dialogID=8803212&stateId=0%200%208801226](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=2&docTypeID=DT_KB_1_1&dialogID=8803212&stateId=0%200%208801226)
usbfs  /proc/bus/usb  usbfs  auto  0  0

# Entry for /dev/hda1 :
UUID=221d448e-c456-4e67-b1f4-675a654e16c8 / ext3 defaults,errors=remount-ro,data=writeback,noatime 0
# Entry for /dev/hda5 :
UUID=5abbef3f-03f4-4927-868f-93ec33fe1a6f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
# /dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb1 /media/hdb1 vfat iocharset=utf8,umask=000 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb5 /media/hdb5 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb6 /media/hdb6 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb7 /media/hdb7 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdd1 /media/hdd1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdd5 /media/win2k4msi ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0


Robin

---

### Post by Robbyx on 2007-09-06
I would like to work out why I am having this problem. Would it be possible for someone to make some suggestions.

---

### Post by merlinus on 2007-09-06
Do you have this problem with your other ntfs partitions?

You might try adding

umask=0002 0 2

after utf8.

-merlin

---

### Post by Robbyx on 2007-09-06
Before I change it do you mean this?

```
/dev/hdb1 /media/hdb1 vfat iocharset=utf8,umask=000 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb5 /media/hdb5 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8, unmask=0002 0 2
/dev/hdb6 /media/hdb6 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8, unmask=0002 0 2
/dev/hdb7 /media/hdb7 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdd1 /media/hdd1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdd5 /media/win2k4msi ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
```

---

### Post by merlinus on 2007-09-06
It is umask, not unmask, and no space after the comma preceding.

-merlin

---

### Post by vanadium on 2007-09-06
umask probably makes no sense on ntfs-3g partitions because ntfs-3g does not support unix permissions. Does creating folders and files work on the command line (just to see whether or not it is a nautilus specific problem)? Is the drive not full?

---

### Post by merlinus on 2007-09-06
IIRC, it can be used on any POSIX system, which includes various flavors of windows.

-merlin

---

### Post by Robbyx on 2007-09-06
I made the changes and it was not a success. Having not backed up my Hard disk it was pleasant to find that the two drives had nothing on them. I went to media and clicked on the two drives. No contents appeared. I went back and restored the settings to what they had been, as above, and restarted the machine. The dirives are back so at least I have the contents there. 

I would still  like to create sub folders, so I  do not want to give up on this permission setting but it does appear that the settings suggested do not work.

---

### Post by merlinus on 2007-09-06
You might try running **sudo ntfs-config** again, and see if the correct boxes are ticked.

Other than that, you can use **gksudo nautilu**s to open the file manager as root, navigate to the partitions in /media, and see if you can change the permissions.

FWIW, here is the applicable line from my /etc/fstab.  It makes me the owner with full read-write permissions on everything within it, including creating subfolders and files:

# Entry for /dev/sda1 :
UUID=1EB88F62B88F36F5 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8,uid=1000,gid=1000,umask=0002 0 2

-merlin

---

### Post by Robbyx on 2007-09-06
> **merlinus said:**
> You might try running **sudo ntfs-config** again, and see if the correct boxes are ticked.

Other than that, you can use **gksudo nautilu**s to open the file manager as root, navigate to the partitions in /media, and see if you can change the permissions.

FWIW, here is the applicable line from my /etc/fstab.  It makes me the owner with full read-write permissions on everything within it, including creating subfolders and files:

# Entry for /dev/sda1 :
UUID=1EB88F62B88F36F5 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8,uid=1000,gid=1000,umask=0002 0 2

-merlin

I used the nautilus approach it I seem to be able to create sub directories. It was a bit scarry to see all my docs disappear but it is now working properly. I do not know why your change to the fstab did not work for me. Thanks for the help in getting it to work.

---

### Post by merlinus on 2007-09-06
Glad it worked.

I just noticed, however, that your /etc/fstab line is different from mine, in terms of the order in which the parameters are listed.

Don't know if that will make a difference, but you never can tell....

-merlin

---

