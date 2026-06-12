---
title: "Secondary Hard Drive Read-Only issue"
date: 2007-07-23
forum: General Help
---

### Post by BTRobertson on 2007-07-23
First off, it's key to note that I'm a Windows user who's VERY new to Linux and Ubuntu. :) But, I'm getting by and learning a great deal. Now, my Ubuntu Dell machine is my primary machine at my place of work, since I've learned how to access network shares, printers, and other resources with little to no problems. :)

I do have one issue: I have a second hard drive slaved in this machine that is marked read-only. I've tried to elevate my user account to root by using "sudo su" and then using chmod and chown to change permissions for /dev/sdb, the ID for the second hard drive in the Hardware Information page. However, when I run the commands, it keeps telling me that it's a read-only file system (NTFS 3.1). How am able to access this drive in order to read, write, and execute from it? Thanks!!

B.T. Robertson
[www.btrobertson.com](www.btrobertson.com)
Author of the *Chronicles of the Planeswalkers* novel series

---

### Post by benx009 on 2007-07-23
> **BTRobertson said:**
> First off, it's key to note that I'm a Windows user who's VERY new to Linux and Ubuntu. :) But, I'm getting by and learning a great deal. Now, my Ubuntu Dell machine is my primary machine at my place of work, since I've learned how to access network shares, printers, and other resources with little to no problems. :)

I do have one issue: I have a second hard drive slaved in this machine that is marked read-only. I've tried to elevate my user account to root by using "sudo su" and then using chmod and chown to change permissions for /dev/sdb, the ID for the second hard drive in the Hardware Information page. However, when I run the commands, it keeps telling me that it's a read-only file system (NTFS 3.1). How am able to access this drive in order to read, write, and execute from it? Thanks!!

B.T. Robertson
[www.btrobertson.com](www.btrobertson.com)
Author of the *Chronicles of the Planeswalkers* novel series

ntfs comes read-only in ubuntu by default.  the only way to change it is by installing the package **ntfs-3g**.  if you want a nice configuration tool to help you remount your ntfs as read/write (or maybe back to just read-only), install the **ntfs-config** package.

---

### Post by Forrest319 on 2008-01-24
I had the same issue and this fixed it.  I was about to create a new thread but the forums were smart enough to point this out to me after I typed my subject line.  Now it's time to figure out how to merge a couple of partitions without destroying any data...

---

### Post by jdbark1952 on 2008-01-28
I have a similar problem, after upgrading from 7.04 to 7.10, I'm no longer able to access my storage partition that was being shared by my Windows XP side of the computer. I already had checked and ntfs-3d package was installed, after reading this thread I installed ntfs-config but still can not use the other partition.

My upgrade started as an update from 7.04 that did not work so I did a new install from a CD.

---

### Post by jdbark1952 on 2008-01-29
OK, turns out my problem was just due to the act that I had just put windoze into hibernate. After logging back into windoze and turning it off UBUNTU had no problem with the other partitions.

---

