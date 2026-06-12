---
title: "How transfer home and get package list from non bootable computer"
date: 2017-02-20
forum: General Help
---

### Post by captain_rob on 2017-02-20
Something went terribly wrong with upgrading and the computer is now not bootable anymore. I need to reinstall the OS. 

How can i transfer the home directory with all permissions etc with a USB with live ubuntu to a hd storage drive? And I like also to know how to get a package list from the non booting computer

---

### Post by Keith_Helms on 2017-02-20
That all depends on your setup.  It sounds like the computer will boot, just not from the Ubuntu install on the hard drive.  Do you have multiple hard drives in your PC?  Multiple partitions?  Once booted from a USB, you can copy the home directory somewhere, if you have a somewhere to put it other than the hard drive/partition you're about to reinstall onto.

By package list, do you mean a list of what you have installed?  You can get the package names out of /var/lib/dpkg/status.

---

### Post by captain_rob on 2017-02-21
No i have no multiple harddrives or partitions. I use a laptop. I have a separate WD harddisk storage. I think I need root to copy my home to that drive, but wouldn't it change my permissions etc? 

In /var/lib/dpkg/status I find indeed the package names thanks. Its a long list. Is there a way to extract only the package names?

---

### Post by Impavidus on 2017-02-21
> **captain_rob said:**
> No i have no multiple harddrives or partitions. I use a laptop. I have a separate WD harddisk storage. I think I need root to copy my home to that drive, but wouldn't it change my permissions etc?

Use rsync as root with the -a option:```
sudo rsync -a /path/to/old/home/ /path/to/backup/home/
```

---

### Post by Keith_Helms on 2017-02-21
> **captain_rob said:**
> No i have no multiple harddrives or partitions. I use a laptop. I have a separate WD harddisk storage. I think I need root to copy my home to that drive, but wouldn't it change my permissions etc? 

In /var/lib/dpkg/status I find indeed the package names thanks. Its a long list. Is there a way to extract only the package names?

Yes, to get just the package names, run this
```
grep "Package:" /var/lib/dpkg/status | cut -d' ' -f2 | sort
```

---

### Post by captain_rob on 2017-02-22
Thanks guys that did the job :KS

---

