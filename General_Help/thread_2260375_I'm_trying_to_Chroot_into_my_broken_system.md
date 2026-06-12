---
title: "I'm trying to Chroot into my broken system"
date: 2015-01-11
forum: General Help
---

### Post by chkneater on 2015-01-11
I have an Ext HDD and the Grub broke after a kernel upgrade, which I shoulda known would happen.  Anyway when I chroot into the broken system I cannot upgrad-grub, I get an error saying 'cannot find /, is /dev mounted'. I haven't seen any other probs similar to mine... usually I use 'image-boot' and that usually works, but i don't remember where to place it escept for grub.d or the other directory with the startup files in it... and don't mention DL boot repair, can't DL a thing cuz  of dpkg and missing file errors...  I can't fix it with synaptic eihter?  Thanx for any help!!

---

### Post by Sef on 2015-01-11
To fix your GRUB, use [SuperGrubDisk]("http://www.supergrubdisk.org/").

---

### Post by chkneater on 2015-01-11
dont have the space for that, I'm on live CD and also I need to chroot into my broken partition to use it anyway

---

### Post by Bashing-om on 2015-01-11
chkneater; Hello;

My way to do a full CHange Root - a slow way, but a sure way - :
```

## Change /dev/sdxY to actual partition value eg. /dev/sda5

sudo mount /dev/sdxY /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /run /mnt/run

sudo chroot /mnt/ /bin/bash

```

When done with what is needed in the CHange Root ->
I am a firm believer to "back out " so all files are for sure properly closed :
```

exit
sudo umount /mnt/run 
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

