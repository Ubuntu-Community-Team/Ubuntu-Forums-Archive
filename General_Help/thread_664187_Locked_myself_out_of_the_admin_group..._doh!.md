---
title: "Locked myself out of the admin group... doh!"
date: 2008-01-10
forum: General Help
---

### Post by sammydee on 2008-01-10
Hi all

erm... done a bit of a stupid thing...

I was TRYING to add myself to the "fuse" group so I could mount fuse filesystems without having to sudo. I used the command usermod to do it and managed to make it so I am a member of the fuse group and NO OTHER GROUPS.

This is a pain because as well as being totally unable to access the cd drive or sound, I am also now unable to sudo. I can get to a recovery console as root, but I need to know what command to run to restore my user to all the right groups.

any help?

sam

---

### Post by astoltz on 2008-01-10
the command is the same: usermod.  But you have to use the -G option and then give it the whole list of groups that you want yourself to be member of.  Have a look at the man page for a better explanation:  ```
man usermod
```You could also just edit the file /etc/group but that may be a little more tedious than usermod.

---

### Post by nowshining on 2008-01-10
u can alsu use adduser

i did that once

:D

adduser USER GROUP


example

adduser urusername group

adduser nowshining admin

:)

sudo first in cli/recovery mode

---

### Post by sammydee on 2008-01-11
I can't remember which groups I was a member of by default. Can somebody on a default ubuntu install please type "id" at the command line and tell me?

Sam

---

### Post by Washer on 2008-01-11
```
uid=1000(ubuntuuser) gid=1000(ubuntuuser) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(ubuntuuser)
```

---

### Post by sammydee on 2008-01-11
Fixed it, thanks!

Sam

---

### Post by nowshining on 2008-01-11
ur welcome

---

