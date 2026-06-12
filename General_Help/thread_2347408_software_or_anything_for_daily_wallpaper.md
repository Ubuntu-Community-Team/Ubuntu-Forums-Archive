---
title: "software or anything for daily wallpaper"
date: 2016-12-24
forum: General Help
---

### Post by rcrahul60 on 2016-12-24
Is there any software or anything that changes wallpaper automatically daily :)

---

### Post by #&amp;thj^% on 2016-12-24
Wallch wallpaper changer can be easily installed via Ubuntu Software Center. It can also be installed via CLI / Terminal Commands. Discription:[http://melloristudio.com/wallch/](http://melloristudio.com/wallch/)
```
sudo apt install wallch
```
Or if your not hungup on adding a PPA to your sources have a look here: 
[http://ubuntuhandbook.org/index.php/2016/01/install-variety-wallpaper-changer-in-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/01/install-variety-wallpaper-changer-in-ubuntu-16-04/) 
> Be aware your are update-ing your system with unsupported packages from this untrusted PPA (Normal warning we give when adding outside sources)

---

### Post by Impavidus on 2016-12-26
You can also use the command line to set the wallpaper, run that command from a shell script and run that shell script automatically every day. That gives more flexibility than a ready-made application. I don't have the exact command on Ubuntu, but on my system (Xubuntu 16.04) it's```
xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor0/workspace0/last-image -s /path/to/file
```Unfortunately, the details change with every new release of Xubuntu. I use it to put a fresh weather satellite image on my desktop every hour, automatically switching between visible and infrared.

---

### Post by rcrahul60 on 2017-01-02
thanx man

---

