---
title: "Ubuntu won't boot (black screen)"
date: 2007-02-05
forum: General Help
---

### Post by Gibbs on 2007-02-05
I'm back on Windows XP (:() as Ubuntu will not boot. I have it on a seperate hard drive and I really don't want to format....I'll explain what happened/done.

I was trying to get opengl to render so I installed the nvidia drivers from add/remove. When I rebooted X service wouldn't start. It said something about not recognising the driver in xorg.conf.

I hit CTRL-ALT-F1 and changed to /etc/X11/ and did the following:
```
sudo mv xorg.conf xorg_bu1.conf
sudo mv xorg_na.conf xorg.conf
sl
```

This renamed a backup I had to xorg.conf. I even used sl to check everything was ok and it was. I used CTRL-ALT-DELTE to reboot.

Once it rebooted a black screen appears and does nothing once it gets passed the Ubuntu loading screen.

CTRL-ALT-F1 does nothing. Nothing works from what I can see it's just non-responsive.

I have Ubuntu on my other HDD and I HATE having to switch them over. I really want to ditch XP ASAP so please help!

Help is very appreciated! Thanks

---

### Post by lamego on 2007-02-05
Have you tried booting into safe mode ?
Or else you may need to from your LifeCD, mount your disk partition and fix whatever you have broken :)

---

### Post by Gibbs on 2007-02-05
How do you do this? I'm new to linux and apologise for my ignorance :p

I have the Live CD but don't know how to make changes to the system installed with it. Didn't even know Ubuntu had safe-mode...

---

### Post by Rich78 on 2007-02-05
It listed on the Grub boot loader screen.

It's purely console based so you'll need to know what you're looking for and how to fix it.

---

### Post by lamego on 2007-02-05
1. Boot from the liveCD
2. Open the terminal and list your partitions with:
3. sudo fdisk -l
4. mount your partition like:
  sudo mkdir /tmp/my_part
  sudo mount /dev/sda1 /tmp/my_part
Now you can just access your instaalation partition at  /tmp/my_part and revert your changes.

---

### Post by Gibbs on 2007-02-05
> **Rich78 said:**
> It listed on the Grub boot loader screen.

It's purely console based so you'll need to know what you're looking for and how to fix it.

Don't think i've ever seen it... I have the following (if I remember correctly):
[LIST=1]
[*]Install/Boot
[*]Boot from LiveCD
[*]Integrity Check
[*]Memtest
[*]Boot from hard drive
[/LIST]

> **lamego said:**
> 1. Boot from the liveCD
2. Open the terminal and list your partitions with:
3. sudo fdisk -l
4. mount your partition like:
  sudo mkdir /tmp/my_part
  sudo mount /dev/sda1 /tmp/my_part
Now you can just access your instaalation partition at  /tmp/my_part and revert your changes.

Giving it a try now.

Thanks for both of your posts. Will report back /salute (lol)

---

### Post by Gibbs on 2007-02-05
I booted into "safe graphics mode" and copied the xorg.conf from the CD to the mounted partition. It worked!

The commands given are valuable and will save me in the future too. Thanks!!!

---

