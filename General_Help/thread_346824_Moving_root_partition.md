---
title: "Moving root partition"
date: 2007-01-26
forum: General Help
---

### Post by sevcsik on 2007-01-26
Hi!

During my Ubuntu install, I selected the wrong partition for root (only 3GB). I'd like to change the root partition to a 15GB partition before it. How can I do that?

Since the target partition is before the small partition, I can't resize it. I was planning to copy everything to the larger partition, and remove the other one.

I copied all files from the small partition to the 15GB partition (expect the mount point's contents of course), and I modified GRUB, to load from that. The system boots and Gnome starts normally, but few things doesn't work:
[LIST]
[*]sudo
[*]networking
[*]automatic mount of removable devices
[/LIST]

I think all of them are permission problems. Sudo is complaining about setuid, /etc/init.d/networking says that permission denied for device, and and nautilus says that pmount can be only started by root.

I checked and every permission is the same as on the old root partition. If I boot from the old partition, everything works just like before. What can I do with that? Or is there any more elegant way to do this transfer?

Thanks for the help!
Sevcsik

---

### Post by sevcsik on 2007-01-28
Any ideas?

---

### Post by mdurham on 2007-01-28
how did you copy the files to their new partition?

---

### Post by sevcsik on 2007-01-30
with Gnome Commander.

---

### Post by rapidwiz on 2007-01-31
Unless you quite experienced, you probably going to have a ton of issues, the easiest way to get around this is to move /var, /usr, /home etc to new partitions and leave root intact at 3GB. Something like the below. This way you home free and a lot of time saved.

/dev/sda5              6079936   1021484   4749604  18% /
/dev/sda9              5439404   1753412   3409676  34% /home
/dev/sda10             5479048   2817504   2383220  55% /usr

---

### Post by sevcsik on 2007-01-31
Thanks! I'll do that. I just hoped there's something more 'elegant' :)

---

### Post by sevcsik on 2007-02-01
Hi again!

I moved /usr to a seperate partition. Now everything works, except pmount. Nautilus says that it can't launch pmount. If I chmod /usr/bin/pmount +x for users, it says that pmount must be installed with 'suid root'

SOLVED: I reinstalled pmount, now it works.

---

