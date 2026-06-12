---
title: "Logging into Awesome Windows Manager"
date: 2007-12-22
forum: General Help
---

### Post by Mateo on 2007-12-22
I successfully installed Awesome but now do not know how to log into it.  When I go to the Sessions screen in GDM it is not listed.  I've heard you can edit some file to do this, but I'm not sure how.  So, how do I log in?  Please no recommendations that require me to bypass GDM or uninstall it.  Thanks!

---

### Post by mali2297 on 2007-12-22
In a terminal, type
```

sudo nano /usr/share/xsessions/awesome.desktop

```
and copy/paste the following:
```

[Desktop Entry]
Encoding=UTF-8
Name=awesome
Comment=awesome window manager
Exec=awesome
Icon=
Type=Application

```
Save (Ctrl+o) and exit (Ctrl+x). 
Hopefully, awesome will now show up in the sessions menu at the login screen.

If you just want to try out awesome within Gnome, type in the terminal
```

pkill metacity && sleep 3 && awesome &

```
(I am not 100% certain that this will work.)

---

### Post by shrndegruv on 2007-12-27
i also installed Awesome.  My problem is that the super key on my inspiron 6000 doesn't work in awesome (but it does in gnome).  Did you get this to work?

---

### Post by mali2297 on 2007-12-28
> **shrndegruv said:**
> i also installed Awesome.  My problem is that the super key on my inspiron 6000 doesn't work in awesome (but it does in gnome).  Did you get this to work?

It works out of the box for me. The key is called Mod4 in .awesomerc and is used heavily. Perhaps you can try to change Mod4 to Super_L in the configuration file.

---

### Post by shrndegruv on 2007-12-28
I tried changing the config for firing up an xterm, and now one fires up when I hit enter, so I think changing the modkey to Super_L, Super_L is not recognized.


Sooooo close....

---

### Post by mali2297 on 2007-12-28
> **shrndegruv said:**
> I tried changing the config for firing up an xterm, and now one fires up when I hit enter, so I think changing the modkey to Super_L, Super_L is not recognized.


Sooooo close....

Change back .awesomerc to the default.

To get a list of the available modifiers, run
```

xmodmap -pm

```
in the terminal. 

If mod4 is unmapped, run
```

xmodmap -e "add mod4 = Super_L"

```

---

