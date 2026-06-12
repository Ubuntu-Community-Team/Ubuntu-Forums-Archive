---
title: "Run fsck manually"
date: 2016-09-07
forum: General Help
---

### Post by Loknath_Banik on 2016-09-07
I don't open ubuntu it shows run fsck manually and the root filesystem on /dev/sda5 requires a manual fsck.what I do?

---

### Post by sudodus on 2016-09-07
Welcome to the Ubuntu Forums :-)

Boot the computer from a live drive with linux, for example the DVD or USB drive, that you used to install Ubuntu.

Open a terminal window. Type the following command line and start the action with the Enter key,

```
sudo e2fsck -f /dev/sda5
```

It may take long to check and fix things (depending on the size of the partition and read speed from the drive). Maybe you are asked questions, if you want to perform some action. You must answer yes, if you want the repair to be done.

If you hesitate, you may want to create a cloned copy, and work on it.

If you suspect that there are bad blocks (physical damage) on the drive, you can try to search for and mark those blocks with the following command

```
sudo e2fsck -cf /dev/sda5
```

See ```
man e2fsck
``` for more details. See also the following link:

 [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

