---
title: "A few questions and need some clarification before I install WUBI+Fiesty in Win XP"
date: 2007-05-19
forum: General Help
---

### Post by shuttleworthwannabe on 2007-05-19
Ok, firstly thanks for this innovative approach to Linux. I have always wondered why this could not be done, now I see it is a reality. I wish to try it out and have many othe rwindows users convert easily.

Here are my questions:

I have Windows XP NTFS format on sda1 (I am not sure why it calls it sda1 instead hda1), and Ubuntu on sda5 and swap on sda6.
GRUB controls access to Ubuntu and WinXP.

I have downlaoded Wubi (*.exe) in to the Wubi folder in My Documents. I have Feisty ISO on CdROM ALTERNATE version.
1. Do I copy the entire iso (as iso or contents of the iso??) into the same folder as Wubi?
2. When I run the Wubi *.exe , will it know to search for the Feisty copy of the iso in the same folder

thanks

---

### Post by ecology2007 on 2007-05-19
1 and 2) Just copy the both wubi.exe and the alternative.iso as a file on the same folder, then run wubi. Click advanced and select the right ubuntu edtition you want to use. It will detect and use the iso.

Just try it is easy.

Last think, since you allready have some linux knowledge, don't hesitate to contact us (especiaally ago) if you ever have an error at "formating 33%". We can not reproduce it, but we will try to debug it together.

---

### Post by shuttleworthwannabe on 2007-05-20
Thanks ecology2007; another questions:

3. Will Wubi installation over-write the existing GRUB with a new GRUB? What will happen to the existing GRUB? and the installed Feisty on already existing partition?
4. I have an ATI graphics card, and get screen res problem each time with any linux; but with ubuntu, it is quite simple to get the GUI going; I fall back to text mode and while connected to internet, I install the xorg-driver-fglrx; and now with Feisty, it recognizes the restricted drivers on first boot and sets the correct resolution and have full 3D acceleration. Will I expect the same procedure with Wubi+Feisty installation?

Apologies for the rampant way of asking these questions; I want to be sure that I do not mess anything. I may be linux exposed, but I am still playing it safe.

again, many thanks for the help,

swb

---

### Post by ago on 2007-05-20
> **shuttleworthwannabe said:**
> Thanks ecology2007; another questions:

3. Will Wubi installation over-write the existing GRUB with a new GRUB? What will happen to the existing GRUB? and the installed Feisty on already existing partition?
Grub will not be touched, wubi will modify boot.ini, which means that you will have to boot into windows and from there select Ubuntu.

To avoid this double boot menu, you have also other options:

1. install wubi in the linux partition using lubi
2. modify manually the main menu.lst to add a menu item that loads the configfile in c:\wubi\menu\grub\menu.lst

> Will I expect the same procedure with Wubi+Feisty installation?
Wubi should work exactly like ubuntu

---

### Post by shuttleworthwannabe on 2007-05-20
Thanks, u are a star!

Will give feedback as soon as I have it installed.

swb

---

