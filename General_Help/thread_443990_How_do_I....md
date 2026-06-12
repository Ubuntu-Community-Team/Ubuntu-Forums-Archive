---
title: "How do I..."
date: 2007-05-14
forum: General Help
---

### Post by CM Xtasy on 2007-05-14
1. Disable the prompting for password windows (Im the only user)

2. Disable login screen from when I come back from Suspend (Standby)

---

### Post by mdurham on 2007-05-14
'sudo' without password, run the following: sudo visudo 
adding this should do it: %admin ALL=(ALL) NOPASSWD: ALL

Sorry, can't help with question 2

---

### Post by phidia on 2007-05-14
Open System>Administration>Login and click the security tab. You can select automatic login from there. I'll leave the suspend issue to someone else-I'm not sure about that., well...take a look in the screensaver from System>Preferences and click power management.

---

### Post by CM Xtasy on 2007-05-14
> **mdurham said:**
> 'sudo' without password, run the following: sudo visudo 
adding this should do it: %admin ALL=(ALL) NOPASSWD: ALL

Sorry, can't help with question 2

Exactly where do I put that?  I put it under the %admin that was already there, exit, and it didnt save.

---

### Post by aysiu on 2007-05-14
> **CM Xtasy said:**
> Exactly where do I put that?  I put it under the %admin that was already there, exit, and it didnt save.
Paste the command ```
sudo visudo
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal) This will open the /etc/sudoers file in a text editor.

---

### Post by CM Xtasy on 2007-05-14
> **aysiu said:**
> Paste the command ```
sudo visudo
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal) This will open the /etc/sudoers file in a text editor.

Im talking about where to put ```
%admin ALL=(ALL) NOPASSWD: ALL
```

---

### Post by mdurham on 2007-05-14
> **CM Xtasy said:**
> Im talking about where to put ```
%admin ALL=(ALL) NOPASSWD: ALL
```

I would comment out the original line (with a '#') and insert the new one below it.

---

### Post by aysiu on 2007-05-14
> **CM Xtasy said:**
> Im talking about where to put ```
%admin ALL=(ALL) NOPASSWD: ALL
```
So am I.

That code goes into the /etc/sudoers file, which the ```
sudo visudo
``` command allows you to edit.

---

### Post by CM Xtasy on 2007-05-15
> **aysiu said:**
> So am I.

That code goes into the /etc/sudoers file, which the ```
sudo visudo
``` command allows you to edit.

no I know what it does.  Im saying to I put "%admin ALL=(ALL) NOPASSWD: ALL" underneath ```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```  or do I put it somewhere above it or do I overwrite %admin ALL=(ALL) ALL

---

### Post by aysiu on 2007-05-15
Overwrite it.

---

### Post by CM Xtasy on 2007-05-15
Ok thanks lol

now just need to find the answer for #2 :|

---

### Post by strabes on 2007-05-15
You can do #2 in KDE very easily. You just click on the power icon in the notification area and it's the first option on the dialog that appears. See the attachment. Install KDE. You'll love it. ```
sudo aptitude install kubuntu-desktop
```

---

