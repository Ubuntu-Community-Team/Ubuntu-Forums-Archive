---
title: "How to have boot USB from CD"
date: 2013-11-05
forum: General Help
---

### Post by lumaja2 on 2013-11-05
I want to have a boot CD with Ubuntu 12.04 LTS from my live CD.
 How to make this USB?
 Thank you

---

### Post by sudodus on 2013-11-05
Please explain: Do you want to a ***boot CD disk*** or a*** boot USB pendrive***?

Which operating system are you running, and have you got an iso file with 12.04 LTS (the original one) or 12.04.3 LTS (the latest point release)?

---

### Post by lumaja2 on 2013-11-06
OS Ubuntu 12.04 LTS  Sorry my question was totally wrong. I recorded a CD from Ubuntu web site on 5 May 2012 with this OS don’t know if is an iso file I need to make an boot USB pendrive.

---

### Post by sudodus on 2013-11-06
If you have a fair internet connection, I suggest that you download a new iso file with the latest point release Ubuntu 12.04.03 LTS.

Otherwise it is possible to clone from a CD disk to a USB pendrive either directly or indirectly via an iso file. You can use ***dd*** to clone. It it a very powerful but also dangerous tool, nicknamed 'disk destroyer', because it does what you tell it to do without questions. So if you tell it to overwrite your internal hard disk drive ... In other words, double check and triple check, that the input and output devices are the correct ones!

[http://www.linuxjournal.com/content/copy-cd-or-dvd-dd](http://www.linuxjournal.com/content/copy-cd-or-dvd-dd)

[http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/](http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/)

-o-

From a [new] iso file you can make a USB boot drive according to one of these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

