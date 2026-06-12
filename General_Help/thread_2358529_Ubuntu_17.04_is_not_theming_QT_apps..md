---
title: "Ubuntu 17.04 is not theming QT apps."
date: 2017-04-14
forum: General Help
---

### Post by Brandon_MacEachern on 2017-04-14
Out of curiosity, is anyone else having issues with QT apps not being themed properly in Ubuntu 17.04?  For example, K3b, and gqrx, are getting some old style theme, and are not getting the Ambience themes at all anymore, ever since upgrading to 17.04.  I verified this across multiple computers (that were upgraded from 16.10, where it was working just fine then).

I tried in both Gnome and Unity, and no matter what theme I select in either DE, QT apps simply are just showing a very generic theme which reminds me of KDE3.

---

### Post by Brandon_MacEachern on 2017-04-14
I have been trying to figure this out all day, still nothing.

Running QT apps from the terminal gives no errors regarding themes.

---

### Post by Brandon_MacEachern on 2017-04-16
Really?  Nothing?

---

### Post by vasa1 on 2017-04-16
I read about "kvantum" which may do what you want but I forgot where I read that :(

Edit: [https://askubuntu.com/a/763987](https://askubuntu.com/a/763987)

---

### Post by Brandon_MacEachern on 2017-04-16
That won't work, QT apps that allow you to manually change the theme, do not see any of the GTK themes, the only options are "Breeze", "Windows", and "Fusion", that's it.

It's as if GTK themes in QT apps are entirely broken on Ubuntu 17.04, nothing is working whatsoever.

Usually I'd see GTK+ in there, but it's missing on every machine that was upgraded from 16.10 to 17.04.

---

### Post by Brandon_MacEachern on 2017-04-16
For the time being since I couldn't get kvantum to run, using qt5ct fails to run, complains about environment variables.  I can fix them in terminal enough to make it run, but guess what, no GTK themes show up, and appears every QT app is just simply running the Fusion theme, and nothing else.

EDIT:  I just installed a fresh Ubuntu 17.04 install to a virtual machine, and out of the box, QT apps do NOT have gtk themes like they did in 16.10 and under.

This would appear to be a bug since it was supposed to be included like it has in the past.

[https://i.imgur.com/4zAbIE3.png](https://i.imgur.com/4zAbIE3.png)

You can see that VLC in a fresh Ubuntu 17.04 install is showing the Fusion theme, not Ambiance.

I'd file a bug report, but hell if I know what package to tag for this.  I'd tag VLC just to file a report, but then again, it's not VLC's fault.

---

### Post by Brandon_MacEachern on 2017-04-16
Found a fix.

[COLOR=#000000][FONT=Arial]sudo add-apt-repository ppa:nilarimogard/webupd8[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-get update[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-get install qt4-qtconfig qt5ct[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]nano ./profile < Add this line: export QT_QPA_PLATFORMTHEME=qt5ct
[/FONT][/COLOR]sudo nano /etc/environment < add the same line as above.
[COLOR=#000000][FONT=Arial]Log out, log in.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Launch qt4-qtconfig and qt5ct and set both to "gtk".  Then do the same as sudo, or any qt program run as root won't have the right theme either.
[/FONT][/COLOR]

---

