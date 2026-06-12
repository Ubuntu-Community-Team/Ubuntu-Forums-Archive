---
title: "messed up mbr"
date: 2013-01-05
forum: General Help
---

### Post by KlamKhowder on 2013-01-05
Alright I hope this is the right place to post this if not feel free to move/delete, also I hope to make this post as short as possible, that said, i feel as though this issue is rather complicated.

To begin I am almost a complete noob when it comes to ubuntu (the extent of which you will soon discover)

So like many I was dual booting windows 7 and Ubuntu, and like a fool i believed that i could just wipe my ubuntu partition to free up space. well that means GRUB was deleted and that is where my twisted journey with GRUB rescue began.

I tried booting from an ubuntu install disk but my laptop doesn't seem to recognize it. 

I tried booting from a windows 7 install disk, but for some reason I can't.

The only thing i can get to work at this moment is a live cd of RESCATUX (some sort of debian based live cd focused on fixing things) from which I ran the "repair windows MBR" function, this only furthered my problems as now when I boot my computer instead of getting the GRUB rescue command, all I get is "MBR 1:" flashing on screen. It was only after this that I discovered that there are commands one can use with GRUB rescue that will make it function. 

If i knew more command line functions that are available to me in RESCATUX perhaps I could fix this awful mess but as it stands I seem to just keep digging myself deeper and deeper into this hole. can anyone help?

---

### Post by dino99 on 2013-01-05
you should fix that empty mbr by reinstalling grub from the command line:

sudo grub-install /dev/sda
sudo update-grub

note: take care of using a livecd/liveusb having grub-pc (aka grub2), not the old grub (grub-legacy). So use the ubuntu iso.

---

### Post by KlamKhowder on 2013-01-05
Hey man thanks for such a swift reply.

anyway I tried what you asked but when i entered "sudo grub-install/dev/sda" the terminal returns no such file or directory.

the live cd i'm using does support grub2 btw.

---

### Post by BlinkinCat on 2013-01-05
> **KlamKhowder said:**
> Hey man thanks for such a swift reply.

anyway I tried what you asked but when i entered "sudo grub-install/dev/sda" the terminal returns no such file or directory.

the live cd i'm using does support grub2 btw.

Hi,

Not sure, but try leaving a space between install and /dev

Cheers - :)

---

### Post by KlamKhowder on 2013-01-05
hmmm it didn't like that,  it just returned "grub-install: command not found"

---

### Post by dino99 on 2013-01-05
sudo grub-install/dev/sda  (wrong, you might use copy/paste)

sudo grub-install  /dev/sda  (good)

---

### Post by KlamKhowder on 2013-01-05
that still just gets me "grub-install: command not found"

---

### Post by KlamKhowder on 2013-01-05
the rescatux live cd has the option of installing GRUB, should i just make a small ext4 partition with gparted and try to install GRUB on that? because just trying to install it on my standard windows partition does not seem to be helping.

---

### Post by xc3RnbFO8P on 2013-01-05
Try:
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by sgage on 2013-01-05
> **KlamKhowder said:**
> that still just gets me "grub-install: command not found"

If you deleted your Ubuntu partition, grub has no where to find its config files, even if you reinstall the boot loader to /dev/sda - there needs to be a Linux filesystem with the grub files in it.

You will need to either reinstall Ubuntu, and use grub as the boot manager, or get your laptop to boot a Windows repair CD, and install the Windows MBR.

If you ever want to install Ubuntu again, you have the option of installing grub in the Ubuntu partition itself. You can then add an entry in the Windows boot manager for Ubuntu using EasyBCD, a great free utility. Then, when you feel like nuking Ubuntu, your boot process will be unaffected.

---

### Post by offgridguy on 2013-01-05
> **sgage said:**
> 

If you ever want to install Ubuntu again, you have the option of installing grub in the Ubuntu partition itself. You can then add an entry in the Windows boot manager for Ubuntu using EasyBCD, a great free utility. Then, when you feel like nuking Ubuntu, your boot process will be unaffected.
How i wish i had known this sooner. Thank you :D

---

### Post by KlamKhowder on 2013-01-05
Well I fixed it, thank you all for your helpful comments, I was able to get into a live CD and install Ubuntu alongside windows. I know its not an ideal way of doing things however since I only had one partition and was worried about data loss due to resizing, that is the option I went for.

Once again, thank you.

---

