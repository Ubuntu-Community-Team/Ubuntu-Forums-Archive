---
title: "Leftover login screen after trying XFCE"
date: 2020-04-12
forum: General Help
---

### Post by kesetyan on 2020-04-12
Hi,

I'm running Lubuntu 18.04 on a desktop computer in a dual boot arrangement with Windows 7 Professional.

Generally everything is fine.  I installed the Mate desktop manager because I had a few minor, though nevertheless irritating problems with LXDE.  The improvement was immediately noticeable and the occasional freezes and mouse click sensitivity problems I was getting with the LXDE desktop ceased.  On another desktop computer, I was running Linux Mint 19.03 XFCE.  I quite liked XFCE so thought I'd try it in Lubuntu on the dual boot system.  However I soon realized I'd be better sticking with Mate and removed XFCE.  I thought I had cleared it completely but find that, after a period of inactivity or if I log out, the login screen is an XFCE image.  While this is not a problem, I would prefer not to have it and would rather have a plain screen with the login window (not even a return to the Mate login window).

I've yet to find a way to do this and would appreciate any help other forum members might be able to offer.  I really don't understand why the XFCE screen is still on the system - Catfish finds no XFCE references.

Thanks and keep safe in this global pandemic.

---

### Post by webaake on 2020-04-13
Xfce uses Lightdm as login manager (mostly) and that has no direct Xfce references. You should be able to get what you're using now by running in the terminal;```
cat /etc/X11/default-display-manager
```

And then you can either configure it or replace it. I don't know what Mate or Gnome uses as default. Xfce only on my machines. :p

More about Lightdm (and GDM): [https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by kesetyan on 2020-04-13
Hi Websake,

Thanks for your help.

Unfortunately, somehow I managed to stop Lubuntu rebooting but was able to use a system image backup to get Lubuntu back and the restored image was created before the XFCE issue.  I'm now updating software as the backup image is about 5 weeks old.  Data files have not been affected as I store them in a different location.

I better mark this thread as resolved even if the solution, due to my error, was not as you advised.  It is a good reminder on the worth of regular backups though.

Cheers.

---

### Post by mörgæs on 2020-04-14
Next time a problem appears you should consider doing a clean install of Mate 20.04.

You have merged Lubuntu, Xubuntu and Mate, all on a 18.04 platform, and after that removed parts of it. It gives an unnecessarily complicated setup.

---

