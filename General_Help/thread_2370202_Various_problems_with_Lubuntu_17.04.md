---
title: "Various problems with Lubuntu 17.04"
date: 2017-08-31
forum: General Help
---

### Post by RadioAdi on 2017-08-31
Hi, 

I installed 17.04 on to my laptop yesterday and have been experiencing issues which individually are not much cause for concerned, but collectively are not giving me much confidence in the stability of my sytem:

**1.** Synaptic Package Manager and LightDM GTK+ Greeter Settings don't start from main menu. 

I found a fix at below location whereby I need to add gksudo to the .desktop file and job done, but why do I need to do this?

[https://askubuntu.com/questions/185755/synaptic-package-manager-doesnt-launch-from-the-application-menu](https://askubuntu.com/questions/185755/synaptic-package-manager-doesnt-launch-from-the-application-menu)

**2.** RSSOwl giving below error on attempting to view a feed:

> An error has occurred. See error log for more details.
Could not load SWT library. Reasons: 
    /home/{user}/.rssowl2/config221/org.eclipse.osgi/bundles/27/1/.cp/libswt-gnome-gtk-3735.so: libgnomevfs-2.so.0: cannot open shared object file: No such file or directory
    no swt-gnome-gtk in java.library.path
    /home/{user}/.swt/lib/linux/x86_64/libswt-gnome-gtk-3735.so: libgnomevfs-2.so.0: cannot open shared object file: No such file or directory
    Can't load library: /home/{user}/.swt/lib/linux/x86_64/libswt-gnome-gtk.so

I have tried to find a fix but no luck. Sure I can use a different RSS reader, but it has always worked before. 

 **3.** 'Software' application (I think this used to be called 'Lubuntu Software' or similar) shows below error on launch

> GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell was not provided by any .service files

Anybody else experienced these issues? Anybody got any ideas on fixes for 2 and 3?

---

### Post by mender27 on 2017-09-16
I also have a fresh install of Lubuntu 17.04, straight after the initial updates. I checked both the Greeter Settings and Synaptic, and neither of them show errors. Same with "Software" (This is the GNOME3 GUI tool for software management). You are right that the missing tool is/was most likely gksudo in your case. However, since you seem to have multiple possibly unrelated issues, it looks to me like a corrupted installation.

If it's no trouble, I would recommend re-downloading the .iso for Lubuntu 17.04 and installing again :).

---

### Post by yoshii on 2017-09-16
I had some soundcard issues with Lubuntu that seemed to imply from the error logs that some ALSA files were missing.  I couldn't find out how to install them so I gave up and went back to Xubuntu instead.  I like PCmanFM (pcmanfm) file manager which Lubuntu comes with, but Xubuntu seems slightly more complete and more customizeable to me.  You might want to try it.  It's also considered to be well-backwards-compatible like Lubuntu and also not too big of an install (yet it requires a larger download).  I think it's a bit better maintained because XFCE is so popular.

---

