---
title: "Partitions messed up"
date: 2007-09-03
forum: General Help
---

### Post by herbster on 2007-09-03
Don't know what's going on here. I had 2 partitions that I deleted, both were locked, so someone in #ubuntu instructed to do:

```
sudo swapoff -a
```

which allowed me to delete the partitions. I then tried to make one partition out of the new free space, so I did:

```
sudo swapon -a
```

I got an error in GParted when trying to make a new partition, saying I had to reboot. Well I've rebooted and when I did, I got the shell, telling me that I didn't have apt-get installed, and the prompt was root. I just did "exit" and it went into GDM, all is fine. However I cannot do anything with this partition atm, and I need to. Here's what I get now:

```
bobby:~/Desktop$ sudo swapon -a
Password:
swapon: cannot stat /dev/disk/by-uuid/0a2c3e86-f175-4939-a4a6-960ffee30c64: No such file or directory
bobby:~/Desktop$ 
```

Here's GParted now:
[IMG]http://bobgill.net/gparted.png[/IMG]

:confused:

P.S. My Feisty is on /dev/sdb in case anyone's wondering.

---

### Post by herbster on 2007-09-03
Bump-- folks, really need a fix here, this lack of a swap part is messing a lot up for me and I don't know where to go with this.... :(

---

### Post by logos34 on 2007-09-03
Try using Gparted from the ubuntu live cd to delete sda2 and create a new swap, if you can.  Not sure why it's giving you problems.  Remember to take out the old UUID in fstab,* otherwise it'll error out and dump you at the shell.

*Ex:

/dev/sda2 none swap sw 0 0

---

### Post by herbster on 2007-09-03
logos,

Thank you! That worked :)

---

