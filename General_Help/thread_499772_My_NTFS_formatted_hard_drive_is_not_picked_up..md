---
title: "My NTFS formatted hard drive is not picked up."
date: 2007-07-13
forum: General Help
---

### Post by burritomaster on 2007-07-13
I bought and installed my new Maxtor hard drive and formatted it in NTFS. Ubuntu does not detect a hard drive. Is there some special steps I need to take?

---

### Post by bobshowrocks on 2007-07-13
Yes, simply type into a terminal: ```
sudo apt-get install ntfs-3g
``` Assuming that you have the universe and multiverse repos enabled. And now there should be a program called NTFS configuration tool in the 'System Tools' section of your Menu.

---

### Post by burritomaster on 2007-07-13
Short and to the point. Thanks. Now I can move files around with out copying them to my  portable hard drive.

---

