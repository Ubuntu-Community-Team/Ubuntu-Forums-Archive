---
title: "[SOLVED] No shutdown button or Compiz settings"
date: 2007-12-10
forum: General Help
---

### Post by varaonaid on 2007-12-10
Hi,

I recently installed ubuntu-desktop on top of kubuntu so I could try out gnome.  So far I really like it but have a couple of issues.

I have no button for shutdown or restart.  I do have hibernate, suspend, logout switch user and lock screen.  What could cause this and how would I fix it?
EDIT: I searched around some more and found the info about running the gnome-settings-daemon.  I attempted to run it by typing in terminal "gnome-settings-daemon &" but I got this error message: 
[1] 7052
myuser@username:~$ 
** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...

[1]+  Aborted                 (core dumped) gnome-settings-daemon

EDIT #2: I also tried the fix: System>>Administration>>Login Window.  Choose Local tab, In Menu bar check Show Actions Menu.  However, I don't have the Login Window option in the System>>Administration>> menu.  Am I missing a package or something?

So I'm not sure what to do next to try to fix this.  Any thoughts?

EDIT #3: I decided to make GDM my desktop manager instead of KDM.  KDM had remained the default since my addition of the ubuntu-desktop package and gnome because I already had KDE installed first.  I edited the /etc/X11/default-display-manager file to read /usr/sbin/gdm instead of /usr/bin/kdm.  When I rebooted, the login screen was ubuntu instead of kubuntu, GDM was used and I had the shutdown/restart buttons back.


Secondly, I have no custom settings/advanced preferences for Compiz.  I've installed the gnome-compiz-manager package but it didn't add the custom settings option.  Have I installed the wrong package?  Is there a better one to allow me to access the Compiz settings?
EDIT: I added the compizconfig-settings-manager package as well and it solved this issue.  I have the advanced settings now.  One issue fixed, one to go. :)

Thanks so much in advance!

---

