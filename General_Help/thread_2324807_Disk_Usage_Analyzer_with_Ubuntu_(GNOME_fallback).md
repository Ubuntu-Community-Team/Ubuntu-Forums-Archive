---
title: "Disk Usage Analyzer with Ubuntu (GNOME fallback)"
date: 2016-05-16
forum: General Help
---

### Post by merlinus on 2016-05-16
All of a sudden, whenever I open a network connection, this app opens instead of a filemanager, and I cannot get rid of it.  It also opens whenever I plug in an external usb flash drive.  I cannot remove it without also removing gnome desktop.  

I am running Ubuntu 14.04 with the gnome panel (fallback).

Thanks for any assistance!

---

### Post by QDR06VV9 on 2016-05-16
EDIT just seen this was for LXDE
Have you by chance looked at your settings in the Preferred Applications.
And maybe....have you already checked this but Right Click Option and Open With.
Kind Regards

---

### Post by merlinus on 2016-05-16
I cannot find Preferred Applications in the menus.  And there does not seem to be a right-click option for Places/Connect to Server.

---

### Post by QDR06VV9 on 2016-05-16
> **merlinus said:**
> I cannot find Preferred Applications in the menus.  And there does not seem to be a right-click option for Places/Connect to Server.

If you are indeed using Gnome it will bet in Settings> Tabs> Preferred Applications file manager what ever you are using?
Your Thread title is what is confusing [lubuntu]

---

### Post by vasa1 on 2016-05-16
> **runrickus said:**
> ...
Your Thread title is what is confusing [lubuntu]
That happens quite often. I've seen other threads unrelated to Lubuntu being tagged Lubuntu. Looks like a glitch somewhere.

---

### Post by QDR06VV9 on 2016-05-16
Oh yes i just remembered the good old fashion way of calling that Setting.
```
gnome-default-applications-properties
```
And then at the top you will see the tabs "Internet" "Multimedia" "System" Choose this one.
And then look at the default File manager and make sure it reads Nautilus.
Hope that was all it was.
Kind Regards

---

### Post by merlinus on 2016-05-16
Sorry.  I am running Ubuntu 14.04.  But I do no have Settings> Tabs> Preferred Applications.  I am running gnome fallback.

---

### Post by QDR06VV9 on 2016-05-16
Look again at post #6
There is a terminal command for that.

---

### Post by merlinus on 2016-05-17
gnome-default-applications-properties gives this error message -- Command not found.

---

### Post by QDR06VV9 on 2016-05-17
That's not good.:confused:
EDIT:
Install the package called "exo-utils". Then press Alt+F2 and run the command "exo-preferred-applications".
 In Preferred Applications, click on the Utilities tab, and under File Manager, select Nautilus. (You must install Nautilus first, if you haven't already.)

---

### Post by merlinus on 2016-05-17
FWIW, I use Thunar as my file manager, not Nautilus, but of course Nautilus is installed.

---

### Post by QDR06VV9 on 2016-05-17
I suspected something like that.
But change to suit your needs.
Regards

---

### Post by merlinus on 2016-05-17
exo-util was already installed, and I changed the FM to Nautilus.  But the problem is the same as with Thunar -- trying to connect with other computers on my LAN via Places/Connect to Server brings up Disk Usage Analyzer, and not the FM.  This only began a few days ago, and nothing has changed on my computer other than a kernel update.

---

### Post by QDR06VV9 on 2016-05-17
> **merlinus said:**
> exo-util was already installed, and I changed the FM to Nautilus.  But the problem is the same as with Thunar -- trying to connect with other computers on my LAN via Places/Connect to Server brings up Disk Usage Analyzer, and not the FM.  This only began a few days ago, and nothing has changed on my computer other than a kernel update.

To be sure you may need to log-out and back in again and I have seen where a reboot was needed.
And maybe try booting to an older kernel.

---

### Post by merlinus on 2016-05-17
I have rebooted several times.  That is usually one of the first things I do when experiencing difficulties.  And I cleaned out the older kernels a few days ago.

I may simply do a fresh install of 16.04, which will hopefully solve the problem.

---

