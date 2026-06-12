---
title: "Display Issues"
date: 2007-12-22
forum: General Help
---

### Post by Socratez on 2007-12-22
I was playing around with my laptop tonight and I somehow messed the display up. I went into Admin>Screens&Graphics and tried boosting my laptop display resolution. I changed it to a LCD 1280x1024 and hit test and it seemed to work so I saved the config, went back in and applied it restarted X CTRL+ALT+BACKSPACE and all looked well except the resolution didn't increase. I launched my browser and the top rigth buttons are gone (Min/max, restore, close) I tried closing using Alt+F4 but it didn't work either. All shortcut keys are not working and once i launch one application i.e Browser I can no longer access the menus for anything else i.e applications, system until i close the currnet application.

Ideally I would just like to run whatever tool 7.10 runs during install for the graphics so i can get it back to how it was by default after the install ... Can anybody help? I am in dire need of this to finish a paper i have been working on ..


Soc

---

### Post by taurus on 2007-12-22
Open a terminal and run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, restart X with <Ctrl><Alt>Backspace.

---

### Post by Socratez on 2007-12-22
Did that to no avail ... I even rebooted in failsafe from the kernel / grub menu and did it that way ... Still no luck ... I really don't wanna have to do a reinstall over such a silly issue and waste my weekend. Any other ideas? any other options besides the -phigh ?

Soc

P.S. - Also if it helps I can' resize or move the window and the taskbar ont he bottom doesn't show my applications. I can't minumize but can restore and use F11 to Fullscreen ... I removed some software tonight too like deskbar-applet / search applet / brail / fspot / and some others ... is there a log i can check to verify which ones incase that is the culpret?

---

### Post by Socratez on 2007-12-22
I think I know what did it but have no idea how to reverse it ... I remember when i removed the deskbar-applet after my next boot it gave an error about the applet not being there and then i hit delete or remove or whatever option and i think that wrote something to a conf file for the top and bottom task bars ? Possible or am I just out to lunch ?


Soc

---

### Post by Socratez on 2007-12-22
Ok so i had removed compiz-gnome and that was the reason ... I reinstalled it and now it seems as thought all is well. I guess it doesn't pay to try and "Optimize" your machine without a full understanding of what will be effected.

I'll have to start another thread for that!

Soc

---

