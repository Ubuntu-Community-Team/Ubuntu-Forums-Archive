---
title: "Use created partition permanently by all users."
date: 2007-01-09
forum: General Help
---

### Post by Osvaldo on 2007-01-09
Hi.

I'm using Edgy.

I've created a new partion "hda4" that uses a "ext3" filesystem using gparted.

I would like to access **permanently**, and with **all users** to it, so I can increase storage size.

I've check this page:

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html)

But there's no:

System->Administration->Disks

menu entry on my Gnome!

I've installed Edgy from the CD, and as far as I can remember I have never removed that entry from the menu.

Best regards, and thanks for reading this.

Osvaldo

---

### Post by DerHesse on 2007-01-09
I don't think the link you have provided deals with your Problem.
If you want to use the partition from within ubuntu, you need to edit /etc/fstab

---

### Post by pay on 2007-01-09
Add this to your fstab```
sudo nano /etc/fstab
``` ```
### ADDED BY USER ###
/dev/hda4 /media/hda4 ext3 defaults 0 0
```and then```
sudo mkdir /media/hda4
sudo mount -a
```

---

### Post by Osvaldo on 2007-01-09
Thank you very much.

I must add that a user with administrator permissions has to create folders on the new partition, and then give them to the other users. Here's how I did it:

```
cd /media/hda4
sudo mkdir foldername
sudo chown username foldername

```

---

