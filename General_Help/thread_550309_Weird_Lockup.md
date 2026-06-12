---
title: "Weird Lockup"
date: 2007-09-13
forum: General Help
---

### Post by Jriske on 2007-09-13
After I install folding at home, every time my screensaver turns on when I restore my desktop I can move my mouse but not click on any actions or programs. I uninstalled Folding at home by removing the process from init.d as well as /opt/ and /etc yet this still happens.

The only way to restore it is to restart X with ctrl + alt + backspace or hard restart the computer.

---

### Post by ntetreau on 2007-09-13
Quick question, does it still happen after the screensaver comes up?

---

### Post by Jriske on 2007-09-15
Once the screensaver goes active, and I come back to my computer it locks up. It may not be folding at home, but this is when it started to happen. I tried to uninstall manually and by the script.

I ran these commands as well to make sure it was uninstalled as well.

    sudo /etc/init.d/folding stop
    sudo rm /etc/init.d/folding
    sudo update-rc.d folding remove
    sudo userdel -r folding
    sudo rm -rf /var/folding

---

### Post by Jriske on 2007-09-15
Doing a google search, my problem is similar to this: [http://ubuntuforums.org/showthread.php?t=37910](http://ubuntuforums.org/showthread.php?t=37910)

---

### Post by Jriske on 2007-09-16
I've been searching for a solution for days, still no luck. It may have something to do with ATI/XGL/Compuz, but I never had this problem until I installed folding at home.

---

### Post by Jriske on 2007-09-17
Bump

---

### Post by ntetreau on 2007-09-18
Just a quick thought (it also keeps the thread alive!), what aobut going back in synaptic, searching for the already installed screensaver packages and reinstalling them?

---

### Post by Jriske on 2007-09-18
I think I solved it. I don't need a screensaver anyways. I uninstalled xscreensaver and gnome-screensaver and installed a screen lock program and it seems like it works.

---

