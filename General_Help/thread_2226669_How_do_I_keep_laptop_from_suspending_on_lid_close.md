---
title: "How do I keep laptop from suspending on lid close?"
date: 2014-05-28
forum: General Help
---

### Post by pretty_whistle on 2014-05-28
How?

I have ubuntu 14.04 wih xfce deskop.

---

### Post by mikeyinid on 2014-05-28
> **pretty_whistle said:**
> How?

I have ubuntu 14.04 wih xfce deskop.
Not sure about xfce, but check your power settings

[ATTACH=CONFIG]253544[/ATTACH]

---

### Post by Toz on 2014-05-28
There are 3 places you could try:

1. The Power Manager applet in the Settings Manager (in the "On A/C" and "On Battery" sections).

2. If that doesn't work, uncomment and change:
> #HandleLidSwitch=suspend
...to:
```
HandleLidSwitch=ignore
```
...in /etc/systemd/logind.conf (reboot required).

3. If that doesn't work, look for a setting in your bios that might handle the lid switch action.

---

### Post by pretty_whistle on 2014-05-28
Power settings?  That's what I thought but the power manager window wont open and is giving me this error:

[IMG]http://i60.tinypic.com/2d6rv5d.png[/IMG]

??  Don't know what's going on......

---

### Post by slickymaster on 2014-05-28
You can disable _systemd_ lid management. In **/etc/systemd/logind.conf**, change the line that reads:```
#HandleLidSwitch=suspend
```to read```
HandleLidSwitch=ignore
```save the file and reboot.

_**EDIT:**_
Damn. Toz  beaten me.

---

### Post by pretty_whistle on 2014-05-28
> **slickymaster said:**
> You can disable _systemd_ lid management. In **/etc/systemd/logind.conf**, change the line that reads:```
#HandleLidSwitch=suspend
```to read```
HandleLidSwitch=ignore
```save the file and reboot.

_**EDIT:**_
Damn. Toz  beaten me.
Lol....toz did. :)

The file in question wont let me save it unless I have admin access.  So how do I use the terminal for this?

---

### Post by slickymaster on 2014-05-28
> **pretty_whistle said:**
> Lol....toz did. :)

The file in question wont let me save it unless I have admin access.  So how do I use the terminal for this?

```
gksu gedit /etc/systemd/logind.conf
```It will prompt you for you password, enter it and it will open the file for edit.

If you don't have the package gksu installed then you can always use nano```
sudo nano /etc/systemd/logind.conf
```

---

### Post by pretty_whistle on 2014-05-28
> **slickymaster said:**
> ```
gksu gedit /etc/systemd/logind.conf
```It will prompt you for you password, enter it and it will open the file for edit.

If you don't have the package gksu installed then you can always use nano```
sudo nano /etc/systemd/logind.conf
```

Got it.

I found this line in that file:

```
#LidSwitchIgnoreInhibited=yes
```

Wouldnt I want to change that to a NO too?

---

### Post by slickymaster on 2014-05-28
> **pretty_whistle said:**
> Got it.

I found this line in that file:

```
#LidSwitchIgnoreInhibited=yes
```

Wouldnt I want to change that to a NO too?

IMO that won't be necessary because theoretically disabling the systemd lid management will be enough to what you're trying to achieve, but if by any chance it doesn't work, then yes, you can uncomment that line and change its value to NO.

---

### Post by pretty_whistle on 2014-05-28
> **slickymaster said:**
> IMO that won't be necessary because theoretically disabling the systemd lid management will be enough to what you're trying to achieve, but if by any chance it doesn't work, then yes, you can uncomment that line and change its value to NO.
Ok.

I decided to change it to NO just in case.

Your and Toz's solution worked so I'll mark this as solved. :)  Thanks, and thanks Toz.

---

