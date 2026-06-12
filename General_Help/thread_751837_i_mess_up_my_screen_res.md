---
title: "i mess up my screen res"
date: 2008-04-10
forum: General Help
---

### Post by valpobro on 2008-04-10
ok i was trying to get compiz working and when i downloaded envy when i go to use it it says There was an error in the installation process. You can see the log file /var/log/envy-installer.log
and when i do it manually it restarts and is all messed up 
i'm using a dell with a ati hd 2600 with 512mb i really just want to use the tv out on it

please help me i'm new at all this

---

### Post by metalf8801 on 2008-04-10
the first thing you should try is 
System > Preferences > screen resolution 

try that and post again if it doesn't work

---

### Post by valpobro on 2008-04-10
the only resalution that shows up is 600 800...

---

### Post by spec456 on 2008-04-11
If you have xrandr Type in terminal:

```
xrandr
```

what is the output of that?

---

### Post by metalf8801 on 2008-04-11
[http://ubuntuforums.org/showpost.php?p=4322584&postcount=3](http://ubuntuforums.org/showpost.php?p=4322584&postcount=3)

you might want to print that out or right down the code because after the first one you won't be able to look at the web page because your going to exit gnome

If that doesn't work this helped someone else 
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by valpobro on 2008-04-11
this is what came up when i did the xranda thing  
daniel@daniel-desktop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        61.0

---

### Post by spec456 on 2008-04-11
It seems like its not detecting any other resolutions. You can try to uninstall compiz and then reboot your computer and see if that helps. Compiz messed up the way my windows were showing on the first install, so after i uninstalled it everything went back to normal.

---

