---
title: "Remove login manager?"
date: 2008-01-16
forum: General Help
---

### Post by _sAm_ on 2008-01-16
Hi

After installing Ubuntu; is it possible to remove the GDM login manager so the user would have to log in from the command line, and thereafter run ”startx” to start the gnome desktop? 
I am asking cus I want to install a “home server” with Ubuntu, and use the GUI(=gnome desktop) only from time to time to manage things that I cant(cus lack of knowledge) with the command line.

Will there bee any benefits from this approach, like more safe cus less active GUI, and faster boot time? I will remote control the server with either ssh or VNC(depending on what I am going to do).

I know that you can install kde-core or something, is there something like that for the gnome desktop? I dont need all the applications that comes with the normal ubuntu desktop. 

Thanks in front

---

### Post by NilsE on 2008-01-16
You could install with the alternate CD and selectively install what you want 

or

You could boot using the recovery mode in grub which brings you to the console instead of the gui but you may have to build a script to start the network etc..

---

### Post by _sAm_ on 2008-01-16
Thanks for answering my post

I installed Ubuntu in Virtualbox just to test. Logged in using the recovery mode, then runned sudo aptitude remove gdm. After that I restarted Ubuntu; it started as before and stopped with a text mode where I could log in. After logging in startx gave me the normal Ubuntu-desktop. 
But I think your suggestion no 1 with alternate cd is better, and found a nice guide to do so here; [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

But I still wonder; will there bee any different for a simple “home server” to run with or without X?

---

### Post by bodhi.zazen on 2008-01-16
> **NilsE said:**
> You could install with the alternate CD and selectively install what you want 

No, unfortunately, unlike other distros, you have little control of the software installed.


> You could boot using the recovery mode in grub which brings you to the console instead of the gui but you may have to build a script to start the network etc..

Better, Ubuntu defaults to runlevel 2

So ....

```
sudo mv /etc/rc2.d/S20gdm /etc/rc2.d/s20gdm
```

change it back to re-enable gdm

start gdm (if desired) with sudo /etc/init.d/gdm start

---

