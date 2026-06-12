---
title: "No files show up with ls on /media/cdrom"
date: 2007-12-26
forum: General Help
---

### Post by devehf on 2007-12-26
I am using Linux for the first time this week. I am trying to figure out how to access files on my CD-ROM from terminal (booting to recovery mode). 

I am going to try to install proprietary ATI drivers found in ati-driver-installer-8.443.1-x86.x86_64.run that I obtained from ATI on another computer. I think I need to do this to get my ATI Radeon Xpress 1250 chipset embedded on my GIGABYTE GA-MA69GM-S2H MoBo to work. Getting a black screen when X tries to load now.

Anyway, I put in a CD that has the *.run file on it. I go to /media/cdrom0 and do a 'ls' command and nothing shows up. What gives? 'ls -a' shows only '.' and '..'.

fstab shows the CD-ROM drive @ /dev/scd0. Do I need to mount it or something?

Thanks in advance.

---

### Post by kpkeerthi on 2007-12-26
Verify if the CD is mounted by typing **mount** in a terminal.

If not mount using **sudo mount -a** (since your fstab has it, this command should mount the CD) and then check if you can **ls**

---

### Post by dnvikram on 2007-12-26
If that line is in fstab it should have automatically mounted the cdrom.If not,then first verify that line is not commented and if the auto option is set.If everything is fine,then as Keerthi said,run mount -a to read  the fstab.

---

### Post by devehf on 2007-12-26
> **kpkeerthi said:**
> Verify if the CD is mounted by typing **mount** in a terminal.

If not mount using **sudo mount -a** (since your fstab has it, this command should mount the CD) and then check if you can **ls**

It doesn't look like the CD is mounted.

I'm not sure that the fstab is complete. There is only one line for each of my DVD drives.

'/dev/scd0     /media/cdrom0   udf,iso9660 user,noauto,exec 0     0'
'/dev/scd1     /media/cdrom1   udf,iso9660 user,noauto,exec 0     0'

up above those lines I have a couple of lines, one for 'sda1' (looks like the first hard drive 'ext3') and 'sda5' (looks like a system volume = 'swap'). they both have UUID values. nothing like that for the DVD drives.

---

### Post by devehf on 2007-12-26
> **dnvikram said:**
> ...verify... the auto option is set.
ah that could be the prob. should i edit the fstab line for the cd to be 'auto' and not 'noauto'?

and should i use 'vi' to edit?

thanks for the replies.

---

### Post by zvacet on 2007-12-26
You can do it other way.in recovery mode run

```
dpkg-reconfigure xserver-xorg
```

when you come to drivers select **vesa**.that will give you basic graphic and you can after that see content of your Cd and install your drivers.

---

### Post by devehf on 2007-12-27
> **zvacet said:**
> You can do it other way.in recovery mode run

```
dpkg-reconfigure xserver-xorg
```

when you come to drivers select **vesa**.that will give you basic graphic and you can after that see content of your Cd and install your drivers.

This was a great suggestion. I tried doing this and realized I needed to install a bunch of stuff as prescribed in the sticky ATI drivers thread in this forum. Then I was able to get into X to run the ATI restricted drivers. This is going OK, but it is a little slow. I am considering running the latest drivers from ATI.

I was about to give up when I couldn't access the CD.

---

### Post by devehf on 2007-12-27
> **devehf said:**
> This was a great suggestion. I tried doing this and realized I needed to install a bunch of stuff as prescribed in the sticky ATI drivers thread in this forum. Then I was able to get into X to run the ATI restricted drivers. This is going OK, but it is a little slow. I am considering running the latest drivers from ATI.

I was about to give up when I couldn't access the CD.

ON 2nd thought. maybe not. see: [these experiences]("http://ubuntuforums.org/showthread.php?p=3991130#post3991130") from the first kids on the block

---

