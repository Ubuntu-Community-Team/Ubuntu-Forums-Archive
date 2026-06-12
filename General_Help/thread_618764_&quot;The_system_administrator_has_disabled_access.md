---
title: "&quot;The system administrator has disabled access to the system temporarily&quot;"
date: 2007-11-20
forum: General Help
---

### Post by awtomlinson on 2007-11-20
Embarrassingly, I have played around with some settings & do not remember what I have done.  Upon rebooting, I cannot login to GDM.  I receive the following error:

"The system administrator has disabled access to the system temporarily"

I can only login to Fail Safe GNOME, but I do not have the privileges to change any settings, as sudo, su, & gksudo do not work.  If I boot into Fail Safe Terminal, I do not have privileges to start the xorg server.  Can someone please tell me how to either fix this in GUI mode or how to edit the file I need to fix the issue via the terminal.  Again, I don't know exactly which settings I changed.

I apologize & thanks for all the help.

---

### Post by eggdeng on 2007-11-20
Have you tried booting in recovery mode? This logs you in to a GUI as root. You could try creating a new user to see if the damage is limited to the old user account.

---

### Post by awtomlinson on 2007-11-21
I will try that later, but I really want to get this fixed with my current account.  Any other suggestions?

---

### Post by awtomlinson on 2007-11-21
I added a new user account in the Recovery Console & still get the same error.  Someone please help!!

---

### Post by awtomlinson on 2007-11-22
I have also checked all options that I would have possibly changed under the Preferences & Administration submenus of the System menu while logged into the Recovery Console.  I am unable to access Network or Network Tools under the Administration menu.  I assume the setting that I changed is under one of these 2 menu options.  How can I access these menus?  While logged into Recovery Console I am told I don't have rights to open these menu items.  I was under the impression that I had sudo or even su rights under Recovery Console.

---

### Post by awtomlinson on 2007-11-22
I found out how to fix the issue in an old thread, here:

[http://ubuntuforums.org/archive/index.php/t-5409.html](http://ubuntuforums.org/archive/index.php/t-5409.html)

"Go to:
System>Administration>login screen setup (I think you can also run "gksudo gdmsetup" to get this). I then switched to the "security" tab and unchecked the box next to "Always disallow TCP connections to X server"

However, this solution is from Hoary, the menu setup is different under Gutsy.  I can't find this option under Gutsy & am unable to run gdmsetup because I have to start GDM in order to do this, & I can't login to GDM.

---

### Post by awtomlinson on 2007-11-25
So my question is, how do I Always disallow TCP connections to X server from the terminal?  What file do I need to edit?

---

### Post by awtomlinson on 2007-12-04
There has to be a way to edit a text file to change the "Always disallow TCP connections to X server" setting.  Perhaps gdm.conf?  Someone please help, I am really trying to avoid reinstalling the operating system.

---

### Post by awtomlinson on 2007-12-04
I found out how to do this in the /etc/gdm/gdf.conf file, but it didn't work.  I get the same error while trying to login to GDM.  I now remember that I also installed Bastille the last time I could login to GDM.  I found this thread:

[http://ubuntuforums.org/showthread.php?t=273246&highlight=pam_access.conf](http://ubuntuforums.org/showthread.php?t=273246&highlight=pam_access.conf)

My question now is, where do I find the pam_access.conf file & what exactly do I need to change?

---

### Post by awtomlinson on 2007-12-04
Issue Resolved!  From the terminal, I entered "RevertBastille" & I can now login to GDM.

---

