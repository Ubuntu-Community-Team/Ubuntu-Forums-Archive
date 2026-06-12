---
title: "[SOLVED] changing login screen"
date: 2008-05-18
forum: General Help
---

### Post by zachthejones on 2008-05-18
I did a clean install of Hardy with Ubuntu. I've recently installed Kubuntu to play around with ("sudo apt-get install kubuntu-desktop"). I chose to keep my default gdm. Therefore, my system uses GDM login screens and I've had fun downloading various ones from gnome-look.org.

Just recently, it gave me a weird error message when I tried to open "Login Window" program - which is actually the gnome program for changing the GDM theme.

Here's the error message: "You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead."

fun times. I was just wondering:

1) if there was a KDE way to manage the login screens?
2) if I've already passed up any option to use that...
3) is there a way to change my default?
4) any other options for managing login screens that I'm completely oblivious about?

---

### Post by zachthejones on 2008-05-26
okay, I'm not getting the error message any more. But does anyone out there know how (or if its possible) to change the login manager from GDM to the KDE one?

---

### Post by ChompTheMan on 2008-05-26
To change your login manager to KDE's, which is called KDM, open up a terminal and type in:

```
sudo nano /etc/X11/default-display-manager
```

and you should see:

```
/usr/bin/gdm
```

change it to:

```
/usr/bin/kdm
```

and press Crtl+o and it will ask you if you want to save it.  Hit enter for yes, then Ctrl+x to exit.

To be able to download themes from kde-look and use them easily you will need to download the KDM theme manager:

```
sudo apt-get install kcontrol-kdmtheme
```

Now open up Kcontrol(alt+f2 and type in 'kcontrol') and go to 'System Administration >> KDM Theme Manager' and choose or install your KDM theme of choice.  You may encounter a bug, like I do, where you encounter this error message at the login screen - "cannot open theme file /usr/share/apps/kdm/theme/CurrentTheme".  To ensure you don't encounter this problem here is the quickfix.  Go back to your terminal and:

```
sudo nano /etc/kde3/kdm/kdmrc
```

navigate to this line:

```
Theme="/usr/share/apps/kdm/themes/CurrentTheme"
```

if there are quotes wrapped around like in the above example then remove the quotes like so:

```
Theme=/usr/share/apps/kdm/themes/CurrentTheme
```

again, hit Crtl+o to save and Ctrl+x to exit.

Whew!  Now you should be good to go.  I'm pretty sure all you have to do to see the effects of this is to restart X(log out and back in or Ctrl+Alt+Backspace), if not then reboot and you can now enjoy your KDM login themes.

Edit:  Additionally, there are more KDM themes available in the official repositories.  To install:

```
sudo apt-get install kde-kdm-themes
```

---

### Post by zachthejones on 2008-08-14
Thanks for the help! But, um, after following your insructions to change to the KDM login theme I tried rebooting and my computer booted right into terminal - no KDE or anything...

But, I couldn't download the theme manager (wasn't in my repos - is it in a specific one?) and so maybe I was just missing themes or something...

I switched back to the gdm login manager and everything works great now.

Did I miss something?

---

### Post by elektronaut on 2008-08-15
You probably missed that it's ```
/usr/sbin/gdm
``` and ```
/usr/bin/kdm
```

---

### Post by Frank Black on 2008-08-15
Well I don't know but it could be the F4

---

### Post by zachthejones on 2008-08-16
Thanks! fixing making sure it said

```
/usr/bin/kdm
```

fixed it!

---

### Post by dodle on 2008-08-25
If you have multiple Display Managers installed you should be able to run one of the following commands to switch between them:```
sudo dpkg-reconfigure gdm

sudo dpkg-reconfigure kdm

sudo dpkg-reconfigure xdm
```

---

