---
title: "Grub does not load Windows"
date: 2007-11-02
forum: General Help
---

### Post by Victim_of_Gluttony on 2007-11-02
I have an HP laptop that came with windows vista and an 8gb recovery partition. i deleted the recovery partition so that i could ubuntu on the laptop and dual boot. but when i try to load vista, i get and error that says 'NTLDR is missing'

---

### Post by hikaricore on 2007-11-02
It almost sounds as if your recovery partiton was the ***dows BOOT partition to me.

You may want to call HP and ask them about it, just say the recovery partition is corrupted or something so they don't bitch about linux.  ^_^

---

### Post by Prospero2006 on 2007-11-02
My initial post, as hikoricore stated, wasn't too helpful.
My apologies. 

In all seriousness:


I would install Ubuntu anyway and see if the automated dual booting configuration
doesn't pick up your windows. It's really good about detecting your other operating systems and automating
their startup.

Pros

---

### Post by hikaricore on 2007-11-02
That wasn't really appropriate.

The OP did not delete ***dows, it seems he possibly deleted his boot partition.

---

### Post by Victim_of_Gluttony on 2007-11-02
> **Prospero2006 said:**
> My initial post, as hikoricore stated, wasn't too helpful.
My apologies. 

In all seriousness:


I would install Ubuntu anyway and see if the automated dual booting configuration
doesn't pick up your windows. It's really good about detecting your other operating systems and automating
their startup.

Pros i have installed ubuntu multipul times. it wasnt even until i tried debian that vista showed up in grub.

---

### Post by LuxVoodoo on 2007-11-02
Early on in my Ubuntu experience (which was around Dapper), I tried the same thing with the partitions on my HP desktop.  I had a 200 GB hard drive, with 8 gigs of that being a restore partition.  In order to make a little more space for Ubuntu, I deleted the the restore partition, then tried to install Ubuntu using the automatic installer.  Grub wound up never showing my Windows partitions.  So then I tried the old "fixmbr" routine, and that didn't work.  Ultimately, I restored Windows completely, including the 8 GB restore partition, because I panicked and didn't know what to do next.  The next time I tried installing Dapper, I left the restore partition alone and let the automatic installer divide up the free space 50/50.  I've been solid ever since, with Windows XP. Windows Restore, and Ubuntu all showing up in Grub.  My advice to any newbie looking to dual boot is just to let the automatic installer do its thing. Don't mess with the restore partition!

---

### Post by Victim_of_Gluttony on 2007-11-03
Voodoo, how did you restore Vista? I would love to do that.

---

### Post by meierfra on 2007-11-03
Maybe you just need to edit the windows item on the grub menu. Type the following in a ubuntu terminal and post the output:

```
sudo fdisk -l
``` 
and
```
cat /boot/grub/menu.lst
```

---

### Post by suchawato on 2007-11-03
Have you tried [SuperGrubDisc]("http://supergrub.forjamari.linex.org/")?
That works great for fixing boot problems, incl, windows boot problems.
I use it all the time.

---

### Post by TuxTwig on 2007-11-03
I'm having a similar problem with GRUB, Windows Vista shows up in the boot menu, but when I try to boot, a black screen comes up and a minute later, the Vista loader comes up, after that the screen jut goes black again. I've tried SGD and it hasn't worked. I'm sure all my partitions (including Vista) are intact.

---

