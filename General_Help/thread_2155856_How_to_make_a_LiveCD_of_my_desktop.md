---
title: "How to make a LiveCD of my desktop"
date: 2013-06-19
forum: General Help
---

### Post by carmen2012 on 2013-06-19
I've got my desktop just the way I need it and I'd like to make a LiveCD of it.

In the past, I've used Remastersys, but it looks like this project is coming to an end.  Is there another way to accomplish this task.

Please note that my Linux skills are very basic and I need something that is really just point and click preferably.

Thank you

Carmen

---

### Post by carmen2012 on 2013-06-19
Would anyone know?

---

### Post by claracc on 2013-06-20
I suggest you to use clonezilla to do the image.

Please read: [http://www.logicsupply.com/blog/2012/03/21/how-to-create-a-custom-ubuntu-12-04-installation-image/](http://www.logicsupply.com/blog/2012/03/21/how-to-create-a-custom-ubuntu-12-04-installation-image/)

---

### Post by VMC on 2013-06-20
> **carmen2012 said:**
> I've got my desktop just the way I need it and I'd like to make a LiveCD of it.

In the past, I've used Remastersys, but it looks like this project is coming to an end.  Is there another way to accomplish this task.

Please note that my Linux skills are very basic and I need something that is really just point and click preferably.

Thank you

Carmen
Remastersys has been forked to **[system imager]("http://www.os4online.com/2013/04/forking-remastersys-and-state-of-os4.html")**. But I would second the notion of using CloneZilla.

---

### Post by carmen2012 on 2013-06-20
Thanks for the suggestion of Clonezilla, but I don't think it would work to make a LiveCD.  One of the limitations on the Clonezilla site is "The destination partition must be equal or larger than the source one."

I've installed by desktop on a 500GB drive.

---

### Post by sudodus on 2013-06-20
- Do you want to make a portable drive with an installed system?

- Or do you want a live CD, that can be used to create systems similar to your original one?

- Or do you want a complete backup of your system?

The size of the drive is not really limiting the possibility to make a clone. It is the sizes and locations of the used partitions, typically the root partition and the swap partition.

So if you shrink them it should work to clone them afterwards. 16 GB is plenty for an installed Ubuntu system. Even 8 GB would do for a small system on a USB pendrive.

- Don't move the head end of the root partition! Otherwise I think the bootloader needs to be reinstalled.

- You can wipe the swap partition and skip it on the clone, and create a new one at the target computer. Just remember to edit /etc/fstab with the new UUID or the swap partition. Or you can make a small swap partition and have a complete system in the cloned image.

---

### Post by carmen2012 on 2013-06-20
Hi Sudodus

With older versions of Ubuntu, I was able to install Ubuntu on a desktop pc and then use Remastersys to make a bootable CD.  I could then use this bootable CD to boot a "foreign" laptop and have access to all the software that I need as well as my dekstop.

I would like to do the same thing.  So long story short, it's a live CD for personal use that I could use to boot up a workstation with my desktop image.

---

### Post by sudodus on 2013-06-20
1. I think you can still use ***Remastersys***, even  if it is no longer developed. The present version has been used  recently by people discussing it here at the Ubuntu Forums.

2. What size USB drive have you got? Or are prepared to buy?

See this wiki page [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

which is mainly describing live USB drives for installation (but which can also run with persistence to carry personal files and selected program packages), but also specs for USB pendrives.

In general, with a slow drive (cheap flash) or connection (USB 2) you will get slow response with persistent live and installed systems. Volatile live drives are faster (and you can still save data if there is free space, but not add program packages). You can make them faster (once they have loaded) if you add the ram boot option.

See these links that describe installed systems (installed in the same sense as systems installed to hard disk drives).

- compressed image to expand to a 16 GB pendrive
[https://help.ubuntu.com/community/InstalledSystemFakePAE](https://help.ubuntu.com/community/InstalledSystemFakePAE)

- very detailed instructions to create an installation by *C.S.Cameron*
[URL="http://ubuntuforums.org/showthread.php?t=2155901&p=12698654#post12698654"]http://ubuntuforums.org/showthread.php?t=2155901&p=12698654#post12698654
[/URL]

---

### Post by carmen2012 on 2013-06-21
> **sudodus said:**
> 1. I think you can still use ***Remastersys***, even  if it is no longer developed. The present version has been used  recently by people discussing it here at the Ubuntu Forums.[URL="http://ubuntuforums.org/showthread.php?t=2155901&p=12698654#post12698654"]
[/URL]

I did some digging around the forum and discovered that the last version of Remastersys to be released was 3.0.4-2.  The deb file is not available through the remastersys.com website, but I did find it through Google at [http://sourceforge.net/projects/os4systemimage/files/Remastersys%203.0.4-2/](http://sourceforge.net/projects/os4systemimage/files/Remastersys%203.0.4-2/)

Is there any way to verify that this is the "real" version?

---

### Post by mastablasta on 2013-06-21
it seems so since OS4 took over and rebranded it into system imager: [http://www.os4online.com/2013/04/forking-remastersys-and-state-of-os4.html](http://www.os4online.com/2013/04/forking-remastersys-and-state-of-os4.html)

more on the tool here: [http://system-imaging.blogspot.com/](http://system-imaging.blogspot.com/)

this 3.0.4-2 is last/final version from creator of Remastersys.

---

