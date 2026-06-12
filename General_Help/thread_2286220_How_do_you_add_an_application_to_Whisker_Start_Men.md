---
title: "How do you add an application to Whisker Start Menu"
date: 2015-07-10
forum: General Help
---

### Post by B-777 on 2015-07-10
I just installed menulibre and I have no idea on how to add an application to the menu.

Specifically I want to add a script (that is stored in the /home directory) to the start menu so I can run it when need be.

I have not been able to find any documentation or information on how to do this.

---

### Post by monkeybrain20122 on 2015-07-10
Create a .desktop file for your script and put in in ~/.local/share/applications. See template here
[http://ubuntuforums.org/showthread.php?t=2285867&p=13317366#post13317366](http://ubuntuforums.org/showthread.php?t=2285867&p=13317366#post13317366)
Change Exec= to path to your script

Instead of dumping your script at your home I would create a subfolder bin (or Scripts) and put it there

---

### Post by B-777 on 2015-07-10
Thanks for the help.

Managed to create a desktop shortcut for the script, but have not added it to the application directory yet. I may just leave it on the desktop for now for easy access.

---

### Post by monkeybrain20122 on 2015-07-11
To add it to the whisker menu you have to put the .desktop file in ~/.local/share/applications and then perhaps to logout and log back in.

---

