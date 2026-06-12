---
title: "Virtual Cdrom"
date: 2005-05-13
forum: General Help
---

### Post by ante0 on 2005-05-13
Hi, i've been searching on Google.com for a Virtual cdrom drive application, but with no success at all.
So my question is: Are there any good Virtual cdrom drives you can recomment?

-Using Ubuntu Hoary-

---

### Post by Sam on 2005-05-13
No need for this kind of application, you can mount the ISO as a folder:
```
$ sudo mount -o loop -t iso9660 <filename>.iso /mnt/iso
```
Have a look [here](http://www.ubuntuforums.org/showthread.php?t=33881) for making a nautilus script.


EDIT: If you're using Hoary, you should post on the [Hoary Other application support](http://ubuntuforums.org/forumdisplay.php?f=55) forum...

---

### Post by ante0 on 2005-05-13
Thanks for the quick reply =)

Oh, this is my first post ever here on Ubuntuforums so i had no idea actually =)
Thanks again

Edit: This is my first post in a while here on Ubuntuforums  :razz:

---

### Post by ante0 on 2005-05-13
The thing is, i need to install Diablo 2 that has 3 cds... though when i try to install the installer asks for the second cd, and when im about to insert it the cdrom is locked and if i try to unmount the cd the installer shutsdown.
So i need to make new dirs in /mnt/ like iso, iso1, iso2, iso3 etc. will that work?

One more thing, how do i move this thread? =)

Edit: forgot to say im using Cedega latest version

---

### Post by Sam on 2005-05-13
1) If you can browse for the other cd in the installation, you can create the directories and mount your iso files.

2) You cannot move it, only a mod can do it...

---

### Post by ante0 on 2005-05-15
Edit: Can i mount the iso to my cdrom (/dev/hdc) thats located in /media/cdrom0 so it acts like a real cd?

Edit2: Just tried to mount it, but it became a ordinary mounted disk... so i could still insert a cd in the drive and run it, still with the drive mounted

---

