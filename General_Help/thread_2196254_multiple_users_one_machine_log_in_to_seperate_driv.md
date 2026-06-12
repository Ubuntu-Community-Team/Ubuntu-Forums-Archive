---
title: "multiple users one machine log in to seperate drives"
date: 2013-12-28
forum: General Help
---

### Post by confusedstingray on 2013-12-28
i would like to know if this is possible,
after moving don't have room to run more than 1 computer (each user had own computer)
want to install 13.10 
 want 3 users on same machine running 13.10 
to boot to serperate hard drives 
so each user has thier own drive, 
that way if the time comes to move them to a new machine just have to pull their drive and put it in new machine

looking to use one of the releases xubuntu and ubuntu studio as well as ubuntu 
 
from what i read i have to have a base drive with a ubnutu version installed, 
can't figure out how to edit or modify the user login 
any help 
thank you for your time and patience

---

### Post by oldfred on 2013-12-28
If you want to be able to remove drives and put into another sytem, then you need three totally different installs in each hard drive. Each is separate but will see the other drives, so you may have to hide mounts. Is security an issue?

You can also install grub to each drive to boot that drive. But each grub will find the other two installs and offer to boot them. Or you can choose to boot from BIOS or one time boot key to correct drive.

---

### Post by vanadium on 2013-12-29
I would probably limit this to a single install, and have the user home folders on the different drives. When the time comes to have separate computers again, the (in the mean time updated) OS in the new computers is installed in about 30 minutes.

---

