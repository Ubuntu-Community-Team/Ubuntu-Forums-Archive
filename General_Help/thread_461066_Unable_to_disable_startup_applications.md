---
title: "Unable to disable startup applications"
date: 2007-06-01
forum: General Help
---

### Post by cloudstrife87 on 2007-06-01
Hi everyone,

I've been using Ubuntu Feisty for 3 weeks and very impressed of its stability and the tons of software in respiratory, and of course i've face a number of problems too but managed to solve the problem by googling and searching through the forums. But until today, after installing Automatix and Beagle desktop search, whenever i change or delete any startup programs in the System-Preferences-Sessions-Startup Programs, after i close the Sessions window and reload it, the settings revert into the original settings. No matter how i tried but i still cant change the settings of the startup programs. I've even uninstalled Beagle desktop search but the problem still persist. Does anyone here have any clue how to troubleshoot this problem??

---

### Post by Ub1476 on 2007-06-01
Hmm.. Maybe you have to delete the .applicationname folder? It can be found in your home folder. Click <Control>+h to show your hidden folders.

---

### Post by atlanta800 on 2007-06-01
I've had the same problems today as well. I also just installed Beagle today as well. I cannot add anything to the session as well (been trying to add gaim).

---

### Post by cloudstrife87 on 2007-06-01
I've tried to delete the .beagled folder in my home folder, but the problem stil persist...
But i noticed something, i saw a ".xsession-errors" log file in my home folder, and whenever i tried to change the settings in the Sessions, i saw new lines of error log in this file:

** (gnome-session-properties:15934): WARNING **: Could not save /home/james/.config/autostart/beagled-autostart.desktop file


** (gnome-session-properties:15934): WARNING **: Could not save /home/james/.config/autostart/beagle-search-autostart.desktop file


** (gnome-session-properties:15934): WARNING **: Could not save /home/james/.config/autostart/evolution-alarm-notify.desktop file

I browsed to .config/autostart folder, and found a file called "beagled.desktop", but nope, it doesn't solve the problem....

Any more clue??

---

### Post by atlanta800 on 2007-06-01
> **cloudstrife87 said:**
> I've tried to delete the .beagled folder in my home folder, but the problem stil persist...
But i noticed something, i saw a ".xsession-errors" log file in my home folder, and whenever i tried to change the settings in the Sessions, i saw new lines of error log in this file:

** (gnome-session-properties:15934): WARNING **: Could not save /home/james/.config/autostart/beagled-autostart.desktop file


** (gnome-session-properties:15934): WARNING **: Could not save /home/james/.config/autostart/beagle-search-autostart.desktop file


** (gnome-session-properties:15934): WARNING **: Could not save /home/james/.config/autostart/evolution-alarm-notify.desktop file

I browsed to .config/autostart folder, and found a file called "beagled.desktop", but nope, it doesn't solve the problem....

Any more clue??

That helped a lot, I figured it out. The reason it was giving that error is because somehow the .config/autostart had changed ownership to the root user and group. So run this command (substituting USER for your username) from your home folder to fix everything:
```
sudo chown -R USER:USER .config/autostart/
```
And then go back into Sessions and it should work great. Let me know if you still have problems.

---

### Post by cloudstrife87 on 2007-06-02
> **atlanta800 said:**
> That helped a lot, I figured it out. The reason it was giving that error is because somehow the .config/autostart had changed ownership to the root user and group. So run this command (substituting USER for your username) from your home folder to fix everything:
```
sudo chown -R USER:USER .config/autostart/
```
And then go back into Sessions and it should work great. Let me know if you still have problems.

Whoa....it works!!! Hurray!!! I've even installed back the Beagle desktop search, need not worry about the Sessions thingy already:p... Thank you very much :D...

---

