---
title: "Alien is hanging when converting .rpm to .deb"
date: 2017-09-08
forum: General Help
---

### Post by spaceman1980 on 2017-09-08
I am trying to install the Substance Painter Free 30-Day Trial from  Algorithmic. They only distribute it as a Redhat package manager file  (RPM). I am currently using KDE Neon. I am trying to convert it to a  .deb file so I can install it with gdebi. I am using Alien, which is the  only RPM-to-DEB converter that I know of. I first ran:```
sudo alien -k --scripts Substance_Painter-2017.2.0-1.el6.standard.full.x86_64.rpm
```   I looked in Dolphin and saw that new directories were being created,  but the terminal was giving no output whatsoever. I deleted the  directory Alien created and re-ran Alien:
  ```
sudo alien -k --veryverbose --scripts Substance_Painter-2017.2.0-1.el6.standard.full.x86_64.rpm 
```Now, when I run it, it creates several files and directories. It  takes a long time to run rpm2cpio, and once it finishes that, it creates  some more Substance painter files and gets stuck here:```
chmod 755 Substance_Painter-2017.2.0/debian/rules
    debian/rules binary 2>&1
```I ran top and found that using up 99% (varying,  sometimes less or more) of my CPU was dpkg. This went on for a very long  time. I have come to the conclusion that Alien is hanging. I have come  here to ask if anyone has had a similiar problem, and if anyone has  found a way to make this work. I have not yet found any situations that  replicate this on the Internet. Is --scripts even neccessary? I only did it because Alien warned me that I should use it.  Thanks so much for anyone that answers this! :D:razz:

---

