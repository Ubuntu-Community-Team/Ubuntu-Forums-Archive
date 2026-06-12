---
title: "System update screwed my system up."
date: 2008-06-05
forum: General Help
---

### Post by Del Piero on 2008-06-05
I was one of the first to download Hardy Heron RC1 and i love it, and until this day i was using it with no problems what so ever. Yesterday i got this new system update full of modules and other gnome upgrades it was about 55 mb and just came out last night.  Anyway after installing the updtates i shut down the PC and when i turned it on this morning, instead of the loading Linux text that i get from Lilo i got 9A 9A 9A 9A 9A etc and then nothing happens, help please.

---

### Post by Del Piero on 2008-06-05
Bump...

---

### Post by Sef on 2008-06-05
1) Do not bump unless 24 hours have gone by.  Otherwise you could get an infraction.

2) > instead of the loading Linux text that i get from Lilo i got 9A 9A 9A 9A 9A etc and then nothing happens, help please.

Did you install LILO?  GRUB is the default boot manager.

---

### Post by danwood76 on 2008-06-05
Its probably to do with the fact that Ubuntu uses grub and not Lilo.
There was probably a kernel update and lilo wasnt updated automatically.

Can I ask why you are using lilo?

You should re install lilo from the Live CD, that might solve it.

---

### Post by Del Piero on 2008-06-05
> **danwood76 said:**
> Its probably to do with the fact that Ubuntu uses grub and not Lilo.
There was probably a kernel update and lilo wasnt updated automatically.

Can I ask why you are using lilo?

You should re install lilo from the Live CD, that might solve it.

Actually i always use Lilo and thats why i use the alternate install CD, Grub is not very handy in dual-booting because it always ***** up when it's not installed on the mbr and i don't want it on my mbr, i want every OS to be totally seperate on it's partition and i use GAG boot loader to choose, add, remove any OS from the main boot menu.

---

### Post by Del Piero on 2008-06-05
> **Sef said:**
> 1) Do not bump unless 24 hours have gone by.  Otherwise you could get an infraction.

2) 

Did you install LILO?  GRUB is the default boot manager.

Sorry did not know about the bump rule...

And yeah i used the Alt-Install cd to install Lilo instead of Grub, alway did that since Edgy.

---

### Post by mrMango on 2008-06-05
Well, GRUB stands for GRand Unified Bootloader. You're using the GAG boot loader the same way you would be using grub.

But yes, it's probably an error from not properly having run lilo-setup after a kernel update. Unfortunately, my expierence with lilo is limited.

---

### Post by danwood76 on 2008-06-05
> **Del Piero said:**
> Actually i always use Lilo and thats why i use the alternate install CD, Grub is not very handy in dual-booting because it always ***** up when it's not installed on the mbr and i don't want it on my mbr, i want every OS to be totally seperate on it's partition and i use GAG boot loader to choose, add, remove any OS from the main boot menu.

Thats a bit backwards, I use GAG on my MBR to dual boot with GRUB installed on my linux partition.
Its just a matter of setting it up that way, you tell it to setup on the partition rather than the drive.
To be honest there is no advantage of LILO, but this is off topic.

Reinstall LILO from the alternate CD or the live CD and you should solve your issues.

---

### Post by Del Piero on 2008-06-05
> **danwood76 said:**
> Thats a bit backwards, I use GAG on my MBR to dual boot with GRUB installed on my linux partition.
Its just a matter of setting it up that way, you tell it to setup on the partition rather than the drive.
To be honest there is no advantage of LILO, but this is off topic.

Reinstall LILO from the alternate CD or the live CD and you should solve your issues.

Thanks, will do that when i get home and will tell you what happened. And yeah i know it's a matter of settings but even when i set up Grub properly i ended with a very unpleasant experience.

---

### Post by wheelwrightmike on 2008-06-06
Hello,

> **danwood76 said:**
> Its probably to do with the fact that Ubuntu uses grub and not Lilo.
There was probably a kernel update and lilo wasnt updated automatically.

Can I ask why you are using lilo?

You should re install lilo from the Live CD, that might solve it.

How does one re install lilo from the Live CD?

Or how does one re install LILO from the Alternative CD?  Is that possible?  My machine is a Thinkpad T22.  It can't boot the live CD because of a problem with the Savage video card and the X server without manualy editing the x config file.

Thanks,
-Mike

---

### Post by danwood76 on 2008-06-06
Boot up the live CD, and chroot into your install.
So say your linux partition (with /boot on it) was sda1 do:

```

sudo mkdir /mnt/ubuntu # Make mount point
sudo mount /dev/sda1 /mnt/ubuntu/ # Mount ubuntu drive
sudo mount -t proc none /mnt/ubuntu/proc # Mount /proc
sudo mount -o bind /dev/ /mnt/ubuntu/dev # Bind /dev
sudo chroot /mnt/ubuntu /bin/bash # Chroot into a bash shell within ubuntu part

```
Check lilo is intalled:
```

sudo apt-get install lilo

```
Then run the lilo config and save it to the drive:
```

sudo liloconfig
sudo lilo -b /dev/sda1

```

Hope it helps

---

### Post by wheelwrightmike on 2008-06-06
> **danwood76 said:**
> Boot up the live CD, and chroot into your install.
<snip>
Hope it helps

Thanks,
If I can get the live CD to boot, I'll try it.
-Mike

---

