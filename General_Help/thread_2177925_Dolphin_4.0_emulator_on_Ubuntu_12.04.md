---
title: "Dolphin 4.0 emulator on Ubuntu 12.04"
date: 2013-10-01
forum: General Help
---

### Post by loco-w on 2013-10-01
Hello. Are there anyone who has been able to compile the dolphin 4.0 emulator on ubuntu 12.04 ?
I am getting alot of errors trying to compile it. It seems I need a newer versions of cmake and alot of other stuff.
I can't find any ppa's for it and I'm not sure it can be done on the 12.04.

---

### Post by General_Faliure on 2013-10-01
Here is a link to the Dolphin PPA: [https://launchpad.net/~glennric/+archive/dolphin-emu](https://launchpad.net/~glennric/+archive/dolphin-emu)
But it seems you need to be at Ubuntu 13.04 to install Dolphin 4. (It worked for me on Lubuntu 13.04)
On 12.04 you can only install 3.5

---

### Post by loco-w on 2013-10-01
Yes. That was what I was afraid of. I was hoping to upgrade my dolphin from 3.5 to 4.
Just going to keep trying to solve the compile issue.
If someone know of a way, feel free to shout it out here :o

---

### Post by true255 on 2013-10-02
Hey guys,

Actually, I suceed to install and run Dolphin-emu 4 on Ubuntu 12.04 perfectly, games works + wiimote etc.
I compiled it with git source and had to upgrade cmake to a newer version and gcc 4.6 to 4.8 (4.7 might works too) (found ppa for both), too fix all compiling errors.

---

### Post by true255 on 2013-10-02
I will give you ppa and others infos a bit later.

---

### Post by loco-w on 2013-10-03
> **true255 said:**
> I will give you ppa and others infos a bit later.

That would be GREAT !

I struggle to compile it.

---

### Post by true255 on 2013-10-04
Ok here's the info:

I added those following PPA:
[B][COLOR=#444444][FONT=arial]ppa:[/FONT][/COLOR][COLOR=#444444][FONT=arial]kalakris/cmake ---> need to upgrade cmake[/FONT][/COLOR]
[FONT=arial]ppa:ubuntu-toolchain-r/test  ---> install gcc / g++ 4.8
[/FONT]
[/B]Ounce gcc 4.8 is installed, you also need to change the default compiler from gcc 4.6 to gcc 4.8.
-Go to /usr/bin and delete current gcc and g++ symlink (rm gcc and rm g++)
-Recreate symlinks: sudo ln -s gcc-4.8  /usr/bin/gcc
sudo ln -s g++-4.8 /usr/bin/g++


Now if you follow all the compile instruction from [http://code.google.com/p/dolphin-emu/wiki/Linux_Build](http://code.google.com/p/dolphin-emu/wiki/Linux_Build) , you should be able to play game on Dolphin-emu 4 from Ubuntu 12.04.

Let's me know how it does,

---

### Post by loco-w on 2013-10-16
Took some time before I had time to try it and.......  A big thank you true255!
It worked great.
The wiimote connect has gotten alot better with dolphin 4.0 so I'm all smiles :-)


[IMG]http://ubuntuforums.org/images/icons/icon12.png[/IMG]

---

