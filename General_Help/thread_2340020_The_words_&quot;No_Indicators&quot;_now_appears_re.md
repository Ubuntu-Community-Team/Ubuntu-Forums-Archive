---
title: "The words &quot;No Indicators&quot; now appears replacing Network Applet in Taskbar by Clock"
date: 2016-10-15
forum: General Help
---

### Post by roler2 on 2016-10-15
I now have the words "No Indicators" in black lettering replacing the Network Applet by the Clock in Lubuntu 16.04.1.

The Indicator Applet still appears in the Panel Applets section under Panel Preferences. So the words "No Indicators" is replacing that specific Indicator Applet in the Taskbar.

Is there a fix? Please advise. Thank you!

The Volume Applet is still present.

---

### Post by T.J. on 2016-10-15
> **roler2 said:**
> I now have the words "No Indicators" in black lettering replacing the Network Applet by the Clock in Lubuntu 16.04.1.

The Indicator Applet still appears in the Panel Applets section under Panel Preferences. So the words "No Indicators" is replacing that specific Indicator Applet in the Taskbar.

Is there a fix? Please advise. Thank you!

The Volume Applet is still present.

In order for the Indicator applet to work, the appropriate services must be started when you login to your session, otherwise they won't show.    You will find them under  /usr/lib/x86_64-linux-gnu in various folders.  So in order to start the sound indicator, you need to add /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service to autostart in your session.

It's similar for the others.

---

### Post by roler2 on 2016-10-16
Thank you! I will see if I can find the network indicator-network-service or something similar and copy and paste it to the autostart section and see if that will work.

---

### Post by roler2 on 2016-10-22
I apologize for very late reply. The indicator service is working and is listed in autostart and within the task manager as a running service. It appears that the actual network applet is missing. Is there a way to install just the network applet? If so, what is the correct name of the applet to install? Would it be 'indicator-applet-complete'? Thank you again for any assistance you may be able to provide.

---

### Post by T.J. on 2016-10-23
> **roler2 said:**
> I apologize for very late reply. The indicator service is working and is listed in autostart and within the task manager as a running service. It appears that the actual network applet is missing. Is there a way to install just the network applet? If so, what is the correct name of the applet to install? Would it be 'indicator-applet-complete'? Thank you again for any assistance you may be able to provide.

That is quite all right.

In most cases, the network applet is a separate applet, tied to the Network-Manager software.  I'll check into this and get back to you.

---

### Post by roler2 on 2016-10-31
Thank you! The Network Indicator icon appears to be completely missing, as if I try to add it to the System Tray nothing happens, even though the Service is running correctly in autostart.

---

### Post by T.J. on 2016-10-31
Uusually the proper applet is installed as part of the **network-manager-gnome** package.

---

### Post by roler2 on 2016-11-04
Do I have to install the entire package or is there a way to just install the network-manager applet separately?

---

### Post by roler2 on 2016-11-06
network-manager-gnome 


Appears to have lots of dependencies that are missing and applicable to Ubuntu rather than Lubuntu. My Network is working just fine, it is just the networking applet that is missing in the System Tray. I think I will have to live without the applet. I don't want to install the entire network-manager package with all the missing dependencies and then have it mess up the OS, which is working well even though there is no network applet.

---

### Post by T.J. on 2016-11-07
You could always try wicd.

---

### Post by roler2 on 2016-11-11
Well. . .I am giving up. I reinstalled network-manager-gnome and I am still getting the "No Indicators" message in Bold Black Lettering when I try and add the nm-applet to the System Tray. Must be an obscure Lubuntu issue. I thought reinstalling would re-add the Applet. Guess not.

---

### Post by CantankRus on 2016-11-12
Bring up panel preferences > panel applets.
Click on "Indicator applets" then Preferences.
In the dialogue window that comes up, mark/check Indicator Applications.

---

### Post by roler2 on 2016-11-13
Great idea. . .I thought that would be the answer! Unfortunately. . .didn't bring back the Applet. I still get the No Indicators message, which replaces the Applet in the System Tray. Maybe it is a Lubuntu issue or a gnome issue.

---

### Post by vasa1 on 2016-11-13
Have you tried another icon theme?

---

### Post by CantankRus on 2016-11-13
What's your terminal out put from...
```
apt policy indicator-application indicator-application-gtk2
```

Both should be installed in Lubuntu.

Run this if not installed...
```
sudo apt install indicator-application-gtk2
lxpanelctl restart
```

---

### Post by roler2 on 2016-11-16
Thank you! You are brilliant!

---

### Post by CantankRus on 2016-11-16
> **roler2 said:**
> Thank you! You are brilliant!

That's what I keep telling everyone. :P

---

