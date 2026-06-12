---
title: "Is there a &quot;list-view&quot;  application menu for V 12.10?"
date: 2013-01-09
forum: General Help
---

### Post by swbca on 2013-01-09
I just installed Ubuntu 12.10. Is there a way to get "list format" launch menus rather than space consuming Icons with separate text. A grid view of screen objects has always made my dizzy trying to find my target.
 
Linux Mint14 has a nice "list view" menu but it has some issues that require a reboot every few hours on every computer I try it on.

---

### Post by TOMBSTONEV2 on 2013-01-09
I think you want the gnome 3 desktop then.
```

sudo add-apt-repository ppa:gnome3-team/gnome3
``````
sudo apt-get update
``````
sudo apt-get install gnome-shell
```Then to get everything working as you would expect (Calendar etc):
```
sudo apt-get install evolution
```

But I urge you to give unity a try; there is a bit of a learning curve but I find it works good. =)

---

### Post by kurt18947 on 2013-01-09
I use gnome-shell the vast majority of the time.  There are at least two extensions that give a more 'traditional' menu structure.  I also install tint2 panel to add easy window switching.

---

### Post by swbca on 2013-01-10
I select "gdm" as the default display manager but it still comes up with the unity desktop after a reboot. All commands ran to completion without diplaying any errors.

---

### Post by TOMBSTONEV2 on 2013-01-10
Where are you selecting gdm from? I have not taken these steps myself as I like unity, I just know of them.

---

### Post by kurt18947 on 2013-01-10
If you're trying to run gnome-shell, you must first install gnome-shell from the repositories.  To open it, you can use either lightdm or gdm.  Click on the little gear or star looking thing to the right of the user name.  One choice is Ubuntu which is unity.  There should be at least two other choices, gnome and gnome classic.  Gnome is gnome-shell, Gnome classic is similar to though not identical to gnome 2.  There may also be a gnome classic - no effects for older or weaker graphics systems.

---

### Post by swbca on 2013-01-10
> **TOMBSTONEV2 said:**
> Where are you selecting gdm from? I have not taken these steps myself as I like unity, I just know of them.
 
After installing the GNOME Shell,   Then you can switch managers anytime with this command, but I can't get Gnome to go after setting it as default
 
"sudo dpkg-reconfigure gdm"   Then you select LightDM or GDM.

---

### Post by TOMBSTONEV2 on 2013-01-12
Did you get it working the way you wish?

---

### Post by stinkeye on 2013-01-12
> [SIZE="3"]Is there a "list-view" application menu for V 12.10?[/SIZE]
Simple answer...Yes.

Download and install [**_[COLOR="DarkRed"]classicmenu-indicator[/COLOR]_**]("http://www.florian-diesch.de/software/classicmenu-indicator/dist/classicmenu-indicator_0.07_all.deb")
Type menu in the dash and click on classicmenu-indicator.
On first run it will be added to startup applications.

PS Enter "help" in the dash and familiarize yourself with Unity.
You may find, as I do, hitting the Super key and typing the application name or something related to the application a quicker method than list menus.
Make use of the launcher for often used applications.

---

