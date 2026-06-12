---
title: "Distros and home folder"
date: 2007-06-19
forum: General Help
---

### Post by adamorjames on 2007-06-19
OK, I've managed to put my /home directory onto a different partition. Now, I'm wondering what would happen if I decided to delete the partition with Ubuntu 6.06 on it and put 7.04 on that partition. Would the home partition stay as my /home directory and just the OS partition get deleted and changed or would the new Ubuntu wipe out my /home directory and put it's own home directory in place of mine!?

---

### Post by Happy_Man on 2007-06-19
Only your / partition will get replaced. Your /home partition will be absolutely untouched. Unless you tell the installer to format that too. That's the beauty of /home partitions, it makes upgrading, reinstalling, etc. so much easier! And also, you can use the same /home for two different distros! It just gets better and better!

---

### Post by adamorjames on 2007-06-19
Hey, Happy, do all distros use /home?

---

### Post by Happy_Man on 2007-06-19
All distros will have a /home folder in them... that's standard as far as I know. So yeah, all your settings could be saved between distros. Not much else is though, such as mount points (Ubuntu is the only one i've tried that uses /media, others use /mnt). Even still, it's great fun.

---

### Post by adamorjames on 2007-06-19
OK, thanks! You've been a great help!

---

### Post by H.E. Pennypacker on 2007-06-19
Whatever you do, for your own good, do not reformat the home partition.  Do not, again, format the home partition when the Feisty installer asks you if you want it formatted.  Only format the root partition, since you want that gone anway.

---

### Post by adamorjames on 2007-06-19
OK! I'll also try to back up my /home directory onto some sort of storage device just in case. Everything should turn out just fine ( I hope) .

---

### Post by rhodry on 2007-06-19
> **Happy_Man said:**
> All distros will have a /home folder in them... that's standard as far as I know. So yeah, all your settings could be saved between distros. Not much else is though, such as mount points (Ubuntu is the only one i've tried that uses /media, others use /mnt). Even still, it's great fun.

Just one thing to be careful of if you want to use multiple distros with a single /home partition: permissions! You may find you cannot read some files created in one distro but being read in the other.

Even if you create the same primary user on (say) Ubuntu and PCLinuxOS partitions, you can come unstuck because different distros create different USER ID's. For example, one may use 1000 as the id for the primary user whereas another may use id 100. When you come to access the common files on /home, the id's may not match and you will not have access - usually read access will be ok though.

I got stung with this one time. You can get around it by manipulation of folder structures and group permissions, but best to know the details before you embark. Also, BACKUP everything important regularly!!!!

One other thing, each distro will want to setup its own Grub in the MBR. Make sure you know how to manipulate grub restores if you need them.

Having said this, I have been a Ubuntu user since v5.04 but, I often run different distros, like Mepis, PCLinuxOS, DreamLinux, Sabayon, Fedora and others, on spare partitions to try them out, using a 'common' /home. It works really well. 

Cheers,
Paul.

---

### Post by adamorjames on 2007-06-20
Thanks Paul. I may PM you about something later.

---

