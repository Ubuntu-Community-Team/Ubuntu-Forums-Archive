---
title: "(Unity) Desktop background problems"
date: 2014-05-03
forum: General Help
---

### Post by bw4linux2 on 2014-05-03
Since I upgraded to Trusty Trahl a few days ago, my desktop background is always black and right-clicking does nothing. I've already tried resetting Unity and re-installing ubuntu-desktop. I haven't been able to find any log with helpful information, so please let me know any logs you need to see to help troubleshoot. Thanks.

---

### Post by deadflowr on 2014-05-03
1) Could you post the commands or method you tried to rest unity with.

2)Do you have any other desktops installed?
(ie, Gnome, KDE, xfce, lxde, cinnamon)

---

### Post by bw4linux2 on 2014-05-05
I performed the upgrade with 'apt-get update', 'apt-get dist-upgrade' (unfortunately). During 'dist-upgrade', I ran out of disk space and had to do 'apt-get clean' and remove some other files. Then I did 'apt-get -f install' to finish upgrade. Since then, I have done 'unity --reset' , 'unity --reset-icons', and rebooted. As well as removing and installing ubuntu-desktop meta-package. Gnome and I think Xfce desktops are also installed.

---

### Post by Frogs Hair on 2014-05-05
The reset command changed in 12.10 and since nautilus handles the desktop in Ubuntu may want to reinstall it to see if anything changes.If the unity panel is working try nautilus first. 

Unity Reset ```
setsid unity
```

```
sudo apt-get install --reinstall nautilus 
```

Possibly related . [http://askubuntu.com/questions/385594/wallpaper-suddenly-went-black-on-ubuntu-13-10](http://askubuntu.com/questions/385594/wallpaper-suddenly-went-black-on-ubuntu-13-10)

---

### Post by bw4linux2 on 2014-05-05
Those commands completed successfully and I logged out and back in. Unfortunately, the problem has not been resolved.

---

### Post by bw4linux2 on 2014-05-05
I did "gsettings set org.gnome.settings-daemon.plugins.background active true' and desktop background now works. Still no icons or right-click, but progress has been made.

---

### Post by Frogs Hair on 2014-05-05
Try the following :

```
sudo apt-get install --reinstall ubuntu-desktop
```

```
sudo apt-get install dconf-tools

```

Open the editor when installed and proceed to  org - gnome - nautilus and make sure the defaults are set and check out the desktop settings as well. If set to default the options will be inactive.

---

### Post by bw4linux2 on 2014-05-06
Thank you very much! I had to set all three icons to show under .org.gnome.nautilus and also had to set show-desktop under .org.gnome.desktop. The problem has now been completely resolved. Hopefully this resolution won't be reversed by a reboot.

---

