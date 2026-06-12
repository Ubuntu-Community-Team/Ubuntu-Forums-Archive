---
title: "Make bootable CD"
date: 2007-04-13
forum: General Help
---

### Post by stchman on 2007-04-13
Hello all, I am wanting to know how to make a bootable cd using Ubuntu.  Nero can do it I wonder if either K3B or Gnomebake can.

Thanks

---

### Post by indytim on 2007-04-13
I haven't had the need yet, but I believe k3b supports it as either a cd data or dvd data project type.

IndyTim

---

### Post by anaconda on 2007-04-13
k3b can do that too. You will need eg. an image of a bootable floppy 

eg. if you select the "new data CD project" there is a button about in the middle of the k3b screen. which is 3 steps right from the "Burn" button and on the left side of "Rename Audio Files"

which is "Edit the boot images of this project to make it bootable" just select new and point it to the image file... and you will have a bootable CD.

I think this will accept floppy, but if it wants to have an image of a floppy.. you can make an image with "dd" in terminal first put the floppy in the drive and then type:
dd if=/dev/fd0 of=floppyimage.img


Huh.. Now I understand why it really is so much easier to give instructions to the terminal.. write this: or something..

---

### Post by stchman on 2007-04-13
> **anaconda said:**
> k3b can do that too. You will need eg. an image of a bootable floppy 

eg. if you select the "new data CD project" there is a button about in the middle of the k3b screen. which is 3 steps right from the "Burn" button and on the left side of "Rename Audio Files"

which is "Edit the boot images of this project to make it bootable" just select new and point it to the image file... and you will have a bootable CD.

I think this will accept floppy, but if it wants to have an image of a floppy.. you can make an image with "dd" in terminal first put the floppy in the drive and then type:
dd if=/dev/fd0 of=floppyimage.img


Huh.. Now I understand why it really is so much easier to give instructions to the terminal.. write this: or something..

Are there any standard images out there.  I know on Windows you can download some .img files for bootable CDs.  Nero 6.6 and better have a built in image for bootable CDs.  Will these .img files that I have in Windows work for K3B as well?

Thanks

---

### Post by stchman on 2007-04-14
I have found a boot image file.  It is a Caldera open DOS image.  I have laid out a procedure on my website.  It allows you to burn a bootable CD using K3B.

[http://www.stchman.com/boot_cd.html](http://www.stchman.com/boot_cd.html)

I have tested it and it works.

---

### Post by guysmiley25 on 2007-04-15
Does anyone know about getting a image off the CD. So that I can use it with another?

---

### Post by stchman on 2007-04-15
> **guysmiley25 said:**
> Does anyone know about getting a image off the CD. So that I can use it with another?

In Windows there is a program called isoBuster.

Linux has an app called KIso.

---

### Post by guysmiley25 on 2007-04-16
Is there a non KDE version?

---

### Post by stchman on 2007-04-16
> **guysmiley25 said:**
> Is there a non KDE version?


The KDE version will run on Gnome.

---

### Post by guysmiley25 on 2007-04-18
I'm running XFCE it still works but I don't like running KDE apps.

Also kiso lets me add boot images, but I want to extract a boot image from the disc. Like you can with isobuster.

---

### Post by guysmiley25 on 2007-04-19
Ping

---

### Post by guysmiley25 on 2007-04-22
Bump again, maybe no such application exist?

Dont want to go install windows just to do this!

---

### Post by guysmiley25 on 2007-05-05
Still wondering about this one!

---

### Post by guysmiley25 on 2007-10-26
Come on guys!

---

