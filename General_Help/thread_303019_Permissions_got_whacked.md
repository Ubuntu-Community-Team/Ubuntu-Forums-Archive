---
title: "Permissions got whacked"
date: 2006-11-19
forum: General Help
---

### Post by Sohum on 2006-11-19
Right, so I tried to relocate my ~ directory to an ntfs partition. I didn't have enough space on it, so the mv stopped halfway. So I rebooted with a 6.06 live cd, used gparted to do some partitioning I'd wanted to do, and rebooted.
Now, during my partitioning, I copied my entire / from one partition to another, then copied the (partial) ~ directory from the ntfs drive to it.
So, when I rebooted, it refuses to log me in! Spewing something about permissions and stuff.
So I failsafe booted, chowned /home/sohum to sohum: , I chmoded it to 655, and, following up on a tip i'd seen elsewhere, chowned /tmp to root:root and chmoded it to 1777.
(On a related note, how can you check the owner/permissions of a folder/directory from the command line?)
So, anyway, now it still refuses to log me in. No, technically, it does, then it says that my session lasted less than ten seconds, which probably means something bad. The file it advised me to check contained the following line:
```
unable to create ~/.gnome2: Permission denied
```
So, what do I do now?

---

### Post by Tomosaur on 2006-11-19
to check the permissions of folders/files on command line, type:
```

ls -l

```

I don't know of this will work or not, but you could try this as a solution (from live cd)
```

chown -R sohum /home/sohum
chgrp -R sohum /home/sohum
chmod -R 755 /home/sohum

```

good luck!

---

### Post by steve.horsley on 2006-11-19
You cannot locate your home on an NTFS partition - NTFS cannot store the required permission flags and ownerships. Your best hope to recover the system is to relocate your home back to its original partition, or back to the root partition.

If you moved your entire root partition, you will likely find two problems that need fixing:
1) /etc/fstab will be pointing to the old partition. This will need editing to point to the new partition.
2) GRUB will be looking on the wrong partition for its files. They should still be there until you erase the old partition, but before doing that you must reinstall GRUB by running grub-install.

From the command line, **ls -l** will show you the ownerships and partitions. But if you say **ls -l** for a directory, it lists the contents, and you can stop it recursing into the directory with **ls -ld**.

---

### Post by Sohum on 2006-11-20
steve, the entire dance goes as follows:
[LIST=1]
[*]copy partial /home/sohum to existing partition (ntfs)
[*]copy / to new partition (ext3)
[*]copy partial /home/sohum to partition mentioned in (2), replacing files if required
[/LIST]
grub is working fine, I configured grub properly.
My /etc/fstab is not, but i'll deal with that later.
(If I boot into recovery mode from grub, I can use my pc as root from the terminal)
tomosaur: i am the owner of my files, having chowned them, recursively, to sohum: (which is supposed to change the group to sohum as well).
I'll try chmoding them to 755 instead of 655 and see if that works when I get home.

And thanks for the file permission and group viewing tips!

---

### Post by Sohum on 2006-11-20
right, 755 worked.
thanks!
Now, I want to know what are the packages to dpkg-reconfigure to get the default settings for networking and for /etc/fstab? I figure that that's the easiest way to do it.

---

### Post by Sohum on 2006-11-20
dpkg-reconfigureing all of the following, and then ifdown eth0; ifup eth0 got my connection working again.
[LIST]
[*]tcpd
[*]network-manager
[*]network-manager-gnome
[*]netbase
[*]libnm-util0
[*]dhcp3-client
[/LIST]

---

