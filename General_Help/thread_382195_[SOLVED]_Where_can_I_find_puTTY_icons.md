---
title: "[SOLVED] Where can I find puTTY icons?"
date: 2007-03-11
forum: General Help
---

### Post by Co.Sinecure on 2007-03-11
Hi All,

Does anyone know where/how I can get the putty icons? I'd like to attach to the menu item so everything looks nicer!

I did have a look at the putty SVN repo to see if I could download it, and it looks like the icons are generated with a python/perl/imagemagik script combo. This doesn't appear to work for me..

I also checked gnome-look icons, just in case.

FWIW, I installed putty via Synaptic. 

Also, can anyone tell me how I can make the putty main option screen (not a session window) use anti-aliased fonts? It looks pretty ugly at the moment..

Thanks,
Will

---

### Post by llamakc on 2007-03-11
May I ask why you wouldn't just ssh from a gnome-terminal (in GNOME) or konsole (in KDE), both of which will have pretty fonts?

---

### Post by Co.Sinecure on 2007-03-11
> **llamakc said:**
> May I ask why you wouldn't just ssh from a gnome-terminal (in GNOME) or konsole (in KDE), both of which will have pretty fonts?

Part of the reason is that I'm switching between Ubuntu and windows every so often (this is my work machine, need windows for certain dev & timesheet tasks), and I'd like to be able to keep everything configured the same by using the same tools on both platforms.

---

### Post by llamakc on 2007-03-11
Putty (the Linux port) appears to use the gtk1 stuff, and is going to be ugly.

You can create a launcher for it and use any icon you would like.

---

### Post by Co.Sinecure on 2007-03-11
> **llamakc said:**
> Putty (the Linux port) appears to use the gtk1 stuff, and is going to be ugly.

You can create a launcher for it and use any icon you would like.

Ok, so I can't do anything about the main window (short of editing the source..:) )

I realise I can use any icon, but I wanted to use the actual putty icon. Its not that big a deal, but I'd prefer it.

---

### Post by llamakc on 2007-03-11
> **Co.Sinecure said:**
> Ok, so I can't do anything about the main window (short of editing the source..:) )

I realise I can use any icon, but I wanted to use the actual putty icon. Its not that big a deal, but I'd prefer it.

mail yourself the icon from your Windows install.

---

### Post by Co.Sinecure on 2007-03-11
> **llamakc said:**
> mail yourself the icon from your Windows install.

Already thought of that :) 
Can't see an icon file in the folder on my windows mount, but I'll have a better look when I switch back over this afternoon.

---

### Post by explemonk on 2007-03-13
This may not help you just yet, but the Putty package from the Feisty universe repository installs an icon (the version I got is 0.59-2).

---

### Post by Co.Sinecure on 2007-03-13
> **explemonk said:**
> This may not help you just yet, but the Putty package from the Feisty universe repository installs an icon (the version I got is 0.59-2).

Cool, thats good to know. Thanks.

---

### Post by geirha on 2007-03-13
I tried downloading the source for unix, untarred it, entered the icons-dir and ran make. It made lots of icons of varying size in png-format...
```

~/src$ wget -O- http://the.earth.li/~sgtatham/putty/latest/putty-0.59.tar.gz | tar zx
~/src$ cd putty-0.59/icons/
~/src/putty-0.59/icons$ make
./mkicon.py  putty_icon 16 putty-16.png
./mkicon.py  putty_icon 32 putty-32.png
./mkicon.py  putty_icon 48 putty-48.png
./mkicon.py -2  putty_icon 16 putty-16-mono.png
./mkicon.py -2  putty_icon 32 putty-32-mono.png
./mkicon.py -2  putty_icon 48 putty-48-mono.png
./icon.pl -4 putty-16.png putty-32.png putty-48.png -1 putty-16-mono.png putty-3 2-mono.png putty-48-mono.png > putty.ico
./mkicon.py  puttygen_icon 16 puttygen-16.png
./mkicon.py  puttygen_icon 32 puttygen-32.png
./mkicon.py  puttygen_icon 48 puttygen-48.png
./mkicon.py -2  puttygen_icon 16 puttygen-16-mono.png
...

```
Have you tried this?

---

### Post by Co.Sinecure on 2007-03-13
That worked!

I did try to run the scripts I downloaded off the subversion repository initially, but that didn't work.

Thanks geirha. :)

---

