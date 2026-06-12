---
title: "disk partition: /usr, /home and / ; separately -- problem."
date: 2012-11-21
forum: General Help
---

### Post by kareti venkatesh on 2012-11-21
I partitioned my hard disc in such a way that i have logical parts for /usr, /home and /. 
I have done this , so that in case i want to change my os I need not re install all the application and format my home dir. 

My doubt is , I forgot that the configuration  files are in /etc, and i did not give any logical partition for it. so if I change my os by just formating / , will i be able to run the programs in the /etc?

Right now I am using Xubuntu.

---

### Post by Lars Noodén on 2012-11-21
If I recall correctly /etc must be on the same partition as /  There is, in theory, /usr/etc, but I haven't seen that used.  When re-installing, you'll just have to make sure you backup /etc first.

---

### Post by dannyboy79 on 2012-11-21
when you format / during a new OS install, it will format /etc/ as well. Unless the other OS is debian based, sharing /home and /usr configuration files won't play nice I don't think.

---

### Post by JKyleOKC on 2012-11-21
In addition to what's already been said, note that many (but not all) packages store per-user configuration data as hidden files in the user's home directory, and are designed so that this data will override the system-wide settings stored in /etc.

This is both a blessing and a curse when one is distro-hopping, because that config data in $HOME may be incompatible with the new distro being tried.

As a general rule, system-wide config data stored in /etc should be considered to be specific to the distro and version that wrote it, and NOT preserved when moving to another distro. However some items may have been customized and these usually do need to be preserved. My solution is to create a backup archive containing only those specific files from /etc. and restore it after making the switch.

The only reason for keeping /usr in its own partition that I can imagine would be to speed up access to the program files stored there, and that would be significant only if (a) the drive holding "/" was very slow and (b) the different drive holding "/usr" was very fast. If both partitions are on the same physical drive then there's no point at all to making them separate, and doing so just introduces another possible failure point.

---

