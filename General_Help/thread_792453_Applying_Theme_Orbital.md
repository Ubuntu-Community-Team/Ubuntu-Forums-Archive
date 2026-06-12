---
title: "Applying Theme: Orbital"
date: 2008-05-12
forum: General Help
---

### Post by Stvnx7 on 2008-05-12
Guys, I've searched the forum and I can't get this thing to work probably. I know that there is probably some good reasons why there are a lot of theme engines, etc., but it can get very confusing for new people like me. 

Anyway, I would like step-by-step instructions on installing this theme:

[http://www.gnome-look.org/content/show.php/Orbital+Pack?content=59920](http://www.gnome-look.org/content/show.php/Orbital+Pack?content=59920)

I know how to install the 56577-gtk-osx-theme.tar.gz file (by the way, can I delete the tarball after it is installed?). 

I downloaded and installed startupmanager. I still don't know how to install the splash. This is what I get when I try to compile the splash theme:

steven@steven-laptop:~/Desktop/Theme/usplash-theme-orbital$ sudo make && make install && make clean
[sudo] password for steven: 
make: Circular orbital_1280_1024.png <- orbital_1280_1024.png.c dependency dropped.
pngtousplash orbital_1280_1024.png > orbital_1280_1024.png.c
/bin/sh: pngtousplash: not found
make: *** [orbital_1280_1024.png.c] Error 127
rm orbital_1280_1024.png.c
steven@steven-laptop:~/Desktop/Theme/usplash-theme-orbital$ usplash-switcher

It says I have an error. Don't know what to make of it. Is it important or not? 

Please help guys. I know you are sick and tired of answering this question, but it is very confusing. After I get step-by-step directions for this, I believe I will be able to apply most other themes that I would like to install. 

Please take a look at the URL. There is a screenlet & GDM theme file that I have no idea what to do with. 

Thank you guys. I will seriously love you if I can get this working.


And again, I spent over 30 minutes searching the forums (that's how I got startupmanager to work), but I reached a dead-end with it.

---

### Post by FuturePilot on 2008-05-13
See here
[https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")
about half way down on how to compile a Usplash theme.

---

### Post by Stvnx7 on 2008-05-18
Thanks for helping out with the splash. Now can anyone tell me how to get the GDM file working? What the heck is that for?

---

### Post by mano cazalet on 2008-05-18
that's the login window.

u can select your new image under system - administration - login window

and yes you can delete the tarball file

---

