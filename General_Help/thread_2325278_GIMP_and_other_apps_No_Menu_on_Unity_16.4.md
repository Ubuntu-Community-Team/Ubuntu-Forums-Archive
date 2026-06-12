---
title: "GIMP and other apps No Menu on Unity 16.4"
date: 2016-05-20
forum: General Help
---

### Post by 7-webmaster on 2016-05-20
How can I use GIMP, GVIM, and other applications which Canonical has apparently decided no longer need to be supported by Unity and therefore do not display a menu?

---

### Post by vasa1 on 2016-05-20
Please don't post data urls. Post actual images using the forum's attachment facility. It's the little paper clip above the posting area.

---

### Post by Linuxisfast on 2016-05-20
You need to manually add to the launcher, earlier on software center did the needful. Also installing GIMP from Gnome Software doesn't show the other options that are available, either one needs to use synaptic or apt-cache.

---

### Post by 7-webmaster on 2016-05-22
> **Linuxisfast said:**
> You need to manually add to the launcher, earlier on software center did the needful. Also installing GIMP from Gnome Software doesn't show the other options that are available, either one needs to use synaptic or apt-cache.

I don't see what the launcher has to do with displaying the menu bar once the application is launched.

Your response is a bit cryptic, but I did try reinstalling GIMP use apt and it informed me I had the latest version.  I have looked at all of the web pages discussing installation of GIMP on 16.04 and none of them describe this problem.  I either need a version of GIMP that can exploit the Unity common menu bar, or some way to have the menu bar appear on the GIMP window (which Unity doesn't facilitate.  I also don't want to have to address EVERY single application that no longer displays a menu one at a time.

---

### Post by 7-webmaster on 2016-05-22
> **vasa1 said:**
> Please don't post data urls. Post actual images using the forum's attachment facility. It's the little paper clip above the posting area.

Thank you for the reminder.

Passing the screenshot as an attachment would have required creating a file to attach, which I could not do because I cannot get GIMP to work on 16.04.  Catch 22.

---

### Post by coffeecat on 2016-05-22
Ubuntu (Unity) 16.04 here, and the stock repository GIMP displays its menu in the menu bar, just as it has done for some years. Perhaps you might like to tell us what customisations, if any, you have done to Ubuntu which may explain why you are not seeing the GIMP menus in the menu bar.

---

### Post by CantankRus on 2016-05-22
The menu is in the unity panel but only appears on mouse hover.
If the menus aren't showing check you have these packages still installed... indicator-appmenu appmenu-qt appmenu-qt5
```
apt-cache policy indicator-appmenu appmenu-qt appmenu-qt5
```
You can also try reloading the panel.....
```
initctl restart unity-panel-service
```

In **System Settings > Appearance ** you can set the menu to appear in the applications titlebar and always be visible.

---

### Post by 7-webmaster on 2016-05-31
> **coffeecat said:**
> Ubuntu (Unity) 16.04 here, and the stock repository GIMP displays its menu in the menu bar, just as it has done for some years. Perhaps you might like to tell us what customisations, if any, you have done to Ubuntu which may explain why you are not seeing the GIMP menus in the menu bar.
I am not aware of doing anything, but the menus for these apps are now visible again.  I genuinely did not have access to the menus, even when I pointedly hovered the cursor over the top bar.  Which as I pointed out in one of my comments meant that I could not attach the screenshot as a file because I could not paste the screenshot into GIMP in order to create a file to attach.  I have no customizations whatsoever.

It might be significant that **every** time I reboot 16.04 on my laptop I am notified of a system problem, which I immediately forward to support.  It is also perhaps significant that Ubuntu did not support suspend/restart on closing the lid on my laptop until 15.10, and even in 16.04 still does not restart if the laptop is not _continuously powered while suspended_.  I think that you will agree that the ability to close the lid and then open it while operating on battery is a fundamental requirement for laptop support, but the Linux kernel group have not yet gotten around to addressing that requirement with respect to my 5-year-old Dell laptop.

---

### Post by acutus on 2016-06-04
I too had this issue and, like 7-webmaster, I had made no modifications. The way I fixed this was to put GIMP in single-window mode, I then followed the instructions of cantankRus and restarted GIMP and it seems to have fixed the problem. As far as I'm aware, essentially once the modifications had been made the menubar and GIMP needed restarting to have full effect.

---

