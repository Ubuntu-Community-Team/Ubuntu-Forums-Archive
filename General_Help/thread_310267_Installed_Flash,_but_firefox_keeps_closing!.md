---
title: "Installed Flash, but firefox keeps closing!"
date: 2006-11-30
forum: General Help
---

### Post by sanelx09 on 2006-11-30
I've installed the flash player for firefox through the terminal.

Once it finished installing, it said delete some file from /home/sanel/mozilla. However, there is no such directory. I cant find "mozilla" anywhere, it isn't in /home/sanel.

Therefore, I can't delete the file I need to, and firefox closes each time I open up a flash-related site.

---

### Post by LLRNR on 2006-11-30
It's not **mozilla**, it's **.mozilla**, notice the dot before the actual name, so it means it will be hidden. You can see it with:

```
cd ~
ls -a
```

And enter it with **cd .mozilla** (once in your ~ folder).

LLRNR

---

### Post by kohoutec on 2006-12-01
> **sanelx09 said:**
> firefox closes each time I open up a flash-related site.

I had this problem - the solution was to change the colour depth to 24 in /etc/X11/xorg.conf

---

### Post by dbk927 on 2006-12-01
Go to your home folder, then hit Ctrl+H.  That will show hidden files, then you can navigate to the .mozilla directory

---

### Post by sanelx09 on 2006-12-01
> **kohoutec said:**
> I had this problem - the solution was to change the colour depth to 24 in /etc/X11/xorg.conf

First off, I'm not sure where "colour depth" is to be found inside the xorg.conf file, all I see is a bunch of "depths" but not color depths, please be more specific.

However, it doesn't allow me to save this file, saying I dont have the privileges, but Im an admin, why?

---

### Post by LLRNR on 2006-12-01
I don't see how those two things are related but anyway: even though you're an "admin" (I suppose you mean that you're the only user of the PC) you don't get root privileges unless you use "sudo" in front of each command you give. This is just to ensure the fact that the normal user will be less likely to make dumb things. It's just... better, harmful changes done by a "sudo" are often hard/impossible to undo. You can have a look [here](https://help.ubuntu.com/community/RootSudo) if you want to know more about the "sudo" thing.

So, to be more specific, if you want to edit your /etc/X11/xorg.conf file, you'd have to hit Alt+F2 and type in```
gksudo gedit /etc/X11/xorg.conf
```(["graphical sudo"](http://www.psychocats.net/ubuntu/graphicalsudo))

Then scroll down until you see **Section "Screen"**. Right under that, you'll have an option called **DefaultDepth** - change the value next to it into **24**, save the file, exit gedit and then restart your X server by hitting Ctrl+Alt+Backspace... STILL I can't see what's the issue connecting Firefox crashes when accessing Flash content with the default color depth... but anyway, here you go :)

LLRNR

EDIT - **_Very important :_**
Before you do anything to your xorg.conf file, open a terminal (Applications -> Accessories -> Terminal) and make a copy of your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by sanelx09 on 2006-12-01
Great. Youtube doesn't close anymore after I did those changes. 

Thanks for the help!

---

