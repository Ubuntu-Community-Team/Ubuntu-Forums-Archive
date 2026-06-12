---
title: "Auto Mounting more than one partition at startup"
date: 2015-01-14
forum: General Help
---

### Post by hotshot247 on 2015-01-14
I'm using ubuntu 14.10 and i can mount one partition by going to the startup applications and for the command, i type, /usr/bin/udisks --mount /dev/disk/by-uuid/(uuid here) and it works for one partition but when i try to add a second one and restart my computer, it'll delete the first one from the startup programs and only load the second one... Does anybody know how to fix this issue? It seems like i found a bug... Maybe their is another way to mount partitions.. Any help with this issue will be great! Thanks!

---

### Post by oldfred on 2015-01-14
Normal way to mount partitions of internal drives is with fstab.
       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

    
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by Dennis N on 2015-01-14
make a script with all the mount commands and save it to ~/bin with a name of your choice. Mark it executable, than add the chosen name to startup applications. I've done this and can attest that it works fine.

Note: 14.10 uses udisks2 by default and you could use its commands. I assume you must have installed udisks.

---

### Post by QIII on 2015-01-14
The preferred method is fstab for what the OP appears to be asking.  ;)

---

### Post by hotshot247 on 2015-01-14
Hey dennis, i upgraded from 14.04 is probably why i still have fstab as well. I made the script and set it to startup and ours working. Thanks everybody for the replies!

---

### Post by Dennis N on 2015-01-14
Thanks for the feedback. I'm happy to hear that the suggestion solved the problem.

---

