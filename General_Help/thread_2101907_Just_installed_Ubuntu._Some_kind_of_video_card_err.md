---
title: "Just installed Ubuntu. Some kind of video card error?"
date: 2013-01-05
forum: General Help
---

### Post by smallclaims on 2013-01-05
Hi all,
I Just installed Ubuntu and went to the Ubuntu Software Centre; some of the button went all fuzzy, as can be seen here:
[]("http://s18.beta.photobucket.com/user/vinokirk/media/Screenshotfrom2013-01-05223628_zpse9640c4c.png.html")[[IMG]http://i18.photobucket.com/albums/b129/vinokirk/th_z_zps201463ed.jpg[/IMG]](http://s18.beta.photobucket.com/user/vinokirk/media/z_zps201463ed.jpg.html)

Anyone know what the problem could be?
Do I need to install new drivers? Is this achieved the same way as in Windows?

---

### Post by Pjotr123 on 2013-01-05
OK, and now we all may start guessing what your hardware is? :biggrin:

Please supply a hardware list in this fashion:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)
(item 7)

---

### Post by Impavidus on 2013-01-06
Definitely a problem with your video drivers. The solution depends a bit on the make and model of the card you have.

Video driver problems are the most common problem happening when installing ubuntu. Most of the time they can be solved without too much difficulty.

---

### Post by smallclaims on 2013-01-17
As requested, attached is my hardware.html

---

### Post by ManamiVixen on 2013-01-17
sudo apt-get install nvidia-current

That solves your issue.

---

### Post by ManamiVixen on 2013-01-17
I forgot to tell you this. Before installing the nvidia-current driver, sudo apt-get autoremove first. Some people have issues with the linux headers after install. autoremove followed by nvidia-current install fixes it.

---

### Post by smallclaims on 2013-01-19
Works perfectly, cheers fella

---

