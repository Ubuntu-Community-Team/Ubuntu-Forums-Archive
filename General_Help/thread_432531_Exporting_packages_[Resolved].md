---
title: "Exporting packages? [Resolved]"
date: 2007-05-04
forum: General Help
---

### Post by Phr34Ck on 2007-05-04
Hey, I've been using Ubuntu for some time now on my windowsxp using virtulization and I think I'm ready to make it my main OS on my laptop. However, can I export all packages that I have? My Internet connection is slow, and it will take me *at least* 6 hours just to download what I have right now. I need a way to export the program/packages I got to my newly installed Ubuntu.

thanks for the help.

---

### Post by aysiu on 2007-05-04
All the installation packages live in the /var/cache/apt/archives directory.

Copy them to the desktop of your new installation and paste these commands into the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by Phr34Ck on 2007-05-04
Thanks a gazillion man.

---

