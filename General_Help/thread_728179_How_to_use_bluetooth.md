---
title: "How to use bluetooth?"
date: 2008-03-18
forum: General Help
---

### Post by GordonFreeman on 2008-03-18
Hello everybody,
I just installed XUbuntu 64Bit on my Dell XPS M1530, so far everything works finde.
Except my bluetooth mouse, it worked once (I think before installing the nvidia driver) but now when I enable it, nothing happens.
Doing a "lsmod|grep blue" returned a module called bluetooth so it seems, that the bluetooth module is loaded.
But is there a way to check/search for bluetooth devices?
Under Windows Vista there's a little application running in the system tray with which I can search and install bluetooth devices.

But I don't know how to do it under XUbuntu (I've used Fedora before but then I haven't had a bluetooth module).


My question is more about general handling/configuring of bluetooth under xubuntu than specially with my mouse, since it worked once it will work again, but I don't know how to use bluetooth under xubuntu.


Thanks.


yours 
Gordon

---

### Post by Sweet Mercury on 2008-03-27
I'm gonna bump this because I'm having a similar issue. I can't even find how to configure Bluetooth under XFCE/Xubuntu.

---

### Post by kpkeerthi on 2008-03-27
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by theZoid on 2008-04-06
> **kpkeerthi said:**
> [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

I've used that method above on several distros incl KDE Hardy and Gnome Hardy, Fedora and even Zenwalk and it always works.  Now, with Xubuntu 8.04 beta, when I try to connect I get:

sudo: hidd: command not found

all BT services are running, Bluez utils et al are installed....something is wrong here....anyone?

thanks !!  driving me loco....

---

### Post by costre on 2008-04-06
I had the same problem in Ubuntu Hardy, hidd is no longer available. I got it working, see if this helps?

[http://ubuntuforums.org/showthread.php?t=737918](http://ubuntuforums.org/showthread.php?t=737918)

/Albin

---

### Post by theZoid on 2008-04-07
> **costre said:**
> I had the same problem in Ubuntu Hardy, hidd is no longer available. I got it working, see if this helps?

[http://ubuntuforums.org/showthread.php?t=737918](http://ubuntuforums.org/showthread.php?t=737918)

/Albin

Great....let me take a look at it !!

---

