---
title: "Openoffice not rendering fonts correctly in documents (Hardy)"
date: 2008-06-26
forum: General Help
---

### Post by flar on 2008-06-26
I'm a longtime Ubuntu user, I just installed Hardy and the fonts in documents look terrible in OpenOffice.  Specifically I'm using Times New Roman.  Everything is set up correctly, it's not a matter of settings, I've tried several.  Font rendering was perfectly fine in Gutsy.  This is a show stopper for me because I use this computer for work, very disappointing because Hardy seems to have many other improvements over Gutsy.  

I'm just wondering if this is a change in Ubuntu or OpenOffice?  And does anyone know how I can get fonts to look like they did in Gutsy?

Here are screenshots to show what I mean.  Notice how in Gutsy everything was uniform, and all the letters can be seen clearly.  In Hardy, the letters run together and the 11 point font in the quotation looks much different than the 12 point font used in the rest of the text.  The test on Hardy looks cheap and amateur.

What's going on here?  I ask again, is this a change in Ubuntu or a change in OpenOffice?


[SIZE="3"]Gutsy:[/SIZE]

[IMG]http://i84.photobucket.com/albums/k28/segaert/oddstuff/gutsy.jpg[/IMG]





[SIZE="3"]Hardy:[/SIZE]

[IMG]http://i84.photobucket.com/albums/k28/segaert/oddstuff/hardy.jpg[/IMG]

---

### Post by prshah on 2008-06-26
> **flar said:**
> 
Specifically I'm using Times New Roman.


Maybe you need to install msttcorefonts```
sudo apt-get install msttcorefonts
``` Times New Roman is a part of this (meta) package. Note that you will need to logout and log back in after installing these fonts for them to appear properly in OpenOffice. If that doesn't work, please post the output of ```
cat /var/log/Xorg.0.log | grep -i font
```.. maybe some font paths are wrong?

---

### Post by niyonk on 2008-06-26
prshah,

your avatar burns my eyes :redface:
lol

---

### Post by flar on 2008-06-26
Thanks prshah, I definitely have msttcorefonts installed properly.  

It's a clean install and I've been using linux for many years, so I know about hinting and best shapes, and what to install, etc. Something has changed with either openoffice or ubuntu in this release, and I wonder if anyone knows exactly what has changed because I can't use hardy if it looks this bad.  

There's definitely been a change for the worse in the antialiasing of openoffice document fonts.  I'm using a CRT monitor btw.

---

### Post by flar on 2008-07-01
.

---

### Post by flar on 2008-07-02
I added pictures to the first post to demonstrate the problem.

---

### Post by flar on 2008-07-06
Is nobody using Ubuntu and OpenOffice for serious work?  Hardy is an excellent distro, but this is unacceptable for word processing.  I installed Hardy on my laptop and it was also like this. I think I'll file a bug report.

---

### Post by flar on 2008-08-08
Still nothing on this?  

This is an extremely serious flaw, gutsy's apps are starting to get old and I want to upgrade soon but I will be forced to switch to another distro.  I really, really don't want to do that.  

How does something like this happen in such a popular distribution?

---

### Post by silkstone on 2008-08-08
I'm using OOo 2.4.1 on Hardy. With Times New Roman as the font, the text spacing and kerning look exactly as in your 'Gutsy' version. There is very little difference between 11pt and 12pt, which I would expect.

I'm sorry I can't explain why yours looks so different and is clearly wrong, but it must somehow be your set-up rather than OOo or Hardy, as it works fine for me.

If you would like to know any of my settings for anything, please ask. I haven't really altered much from defaults.

EDIT/

In case this has any effect on it, I have...

System > Preferences > Appearance > Fonts set to Best Shape

---

### Post by flar on 2008-08-12
I'm not sure why your fonts are working properly silkstone. I wish I knew.  I have three computers running ubuntu, I've tried both upgrades from gutsy and clean installs on all of them and I always get the same result. 

Anyway, I filed a bug report and it has been confirmed but no fix yet:  [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/256058](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/256058)

---

### Post by flar on 2008-08-14
I can confirm this problem is due to an Ubuntu patch to OpenOffice. 

If I download and install OpenOffice from their site the fonts look fine, like they used to.  

Only problem is, that creates some problems for package management.  Hopefully someone will look at my bug report and fix this in the Ubuntu packages.

---

