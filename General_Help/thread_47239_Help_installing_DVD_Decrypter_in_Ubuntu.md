---
title: "Help installing DVD Decrypter in Ubuntu"
date: 2005-07-07
forum: General Help
---

### Post by coasthi on 2005-07-07
Hi all I been trying to install DVD Decrypter  and DVD  Shrink   ](*,)  and been following the Tutorial I found in this forum It's been very helpful and I did manage to install DVD Decrypter and have down loaded the dll.zip file on to my desk top but when I try and run  **unzip Desktop/dll.zip -d ~/.wine/fake_windows/Windows/System/ **  it keeps coming up with this message **"checkdir:  cannot create extraction directory: /home/apal/.wine/fake_windows/Windows/System"** any idea why I can't unzip the file can anybody help please. I have tried a few different things but up till now haven't been able to unzip the dll.zip.

---

### Post by manicka on 2005-07-07
Unzip and  copy/paste it manually

Is this the tutorial you're using?
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

If not, use it instead

---

### Post by coasthi on 2005-07-08
Thank you very much for your reply manicka I been using the same tutorial you have a link to. I can’t find the** wine/fake_windows/Windows/System ** the only one I can find is ** /usr/share/wine/skel/C/windows/system **  it has other dll files in it but it won’t let me copy or Paste  the dll file into it.

---

### Post by thagame on 2005-07-10
i followed that tutorial and i got to the part where you run it and go to settings then in I/O it says click the SPTI - Microsoft option but it wont let me pick it.

---

### Post by manicka on 2005-07-10
[QUOTE=thagame]i followed that tutorial and i got to the part where you run it and go to settings then in I/O it says click the SPTI - Microsoft option but it wont let me pick it.[/QUOTE]
 Yes, I got that error to. From memory the next time I started DVD decrypter or maybe after installing DVD shrink, the option was available.

---

### Post by steven_ellis on 2005-07-10
For some reason I can't click on any of the menus under DVD Decrypter. I've installed in following the MrBass Guide, but it gives me odd errors if I have a DVD mounted, and can't find the HW if I don't have a disk mounted.

DVD Shrink works fine though.

One thing to note is i'm using CrossOver Office rather than Vanilla Wine.

Anyone else had issues with crossover?

Steve

---

### Post by dolson on 2005-07-19
[QUOTE=manicka]Yes, I got that error to. From memory the next time I started DVD decrypter or maybe after installing DVD shrink, the option was available.[/QUOTE]

I got it just now, after having it work fine for like a month... The difference is that I recently upgraded my version of Wine. The new one is crap. They changed the configuration and it's broken (at least for me) now.

---

### Post by wellery on 2005-07-19
If you can't tick SPTI - Microsoft it's probably because you have to do this first:

gedit ~/.wine/config
[Version]
"Windows"="win98"
change to
"Windows"="nt40"

---

