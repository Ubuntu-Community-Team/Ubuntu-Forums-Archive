---
title: "Where is the list of apps?"
date: 2013-12-26
forum: General Help
---

### Post by glenntk on 2013-12-26
Hi Readers;


[LIST]
[*]I'm using 12.04 LTS and can't find a folder or drop-down of all my installed application.  The only way I can is if I go to Software Center, wait for ALL software to load and then select Installed.  If this is the only way, isn't there a means to dictate that "Installed" software loads first  when going into Software Center.  To be honest, I liked Ubuntu 9.1's desktop configuration much better. 
[*]Is there a setting to assure Ubuntu is using the full processing power (as 9.1 had)? 
[*]I keep hearing about different GUIs, I'm using Gnome I think and have heard of GTK+; are there other "faces" I can put on Ubuntu 12.04 LTS? 
[/LIST]

I thank everyone who reads this and provides input.  I also hope everyone had a Merry Christmas!

Glenn

---

### Post by 3rdalbum on 2013-12-26
> **glenntk said:**
> Hi Readers;


[LIST]
[*]I'm using 12.04 LTS and can't find a folder or drop-down of all my installed application.

Click the Ubuntu icon at the top-left of the screen, then click the second icon along the bottom of the Dash that opens up. Or, right-click the Ubuntu icon and choose Applications. Or, hit Super-A.

> [*]Is there a setting to assure Ubuntu is using the full processing power (as 9.1 had)? 

Every version of Ubuntu ever released will use your full processing power when needed, including 12.04.

> [*]I keep hearing about different GUIs, I'm using Gnome I think and have heard of GTK+; are there other "faces" I can put on Ubuntu 12.04 LTS? 


The default Ubuntu 12.04 image uses the Unity desktop and my answer to your applications question assumes that you're actually using Unity. It would take a conscious decision for you to install Gnome.

You can certainly install a different desktop environment. The most popular alternatives are Gnome Shell (Gnome 3), KDE, XFCE and LXDE; all of these are available in the Ubuntu Software Center for installation. Once installed, you can click the Ubuntu icon on the login screen and choose the different desktop to use. You can have multiple desktops installed at the same time and choose between them at the login screen.

---

### Post by tgalati4 on 2013-12-26
If you want to see all of the installed packages on your system, open a terminal:

```
dpkg --get-selections | more
```

Spacebar to page forward, "q" to quit.  If you want to save the list to a file:
```
cd
dpkg --get-selections > largelistofallpackagesinstalledonmysystem.txt
```

---

### Post by glenntk on 2013-12-26
Thank you very much for all the information!!!  And you are most likely correct about me not using Gnome; I just saw it a few times and guessed of that being my GUI.  I'm saving all of your information and again thank you greatly for all of your help!  I'm relatively new to Ubuntu and brand new to 12.04.  Oh I do have one question:  Is it normal for thhe icons of the list of applications to not show up, or only show up on some of them?

Have a great day and thanks again!

Glenn

---

### Post by oldos2er on 2013-12-26
[A non-exhaustive list of desktop environments and window managers.]("http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available")

---

