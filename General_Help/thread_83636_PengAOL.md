---
title: "PengAOL"
date: 2005-10-29
forum: General Help
---

### Post by eighteenblue21grey on 2005-10-29
I just got Ubuntu Linux and need need to set up AOL. 

Heres how far i got;

Downloaded peng1.05.tar.gz from sourceforge

Extracted the peng folder to my desktop

I didnt see an executable file (an .exe entension) to i went to the help file

The first thing it said was to type "% ./recompile" in the base directory of peng

I was unsure what that meant so i assumed going to /peng and double clicking the recompile files icon  then clicking run - which as far as i know added a file to /peng/

Thats as far as i am so i need to do what to do next and if what i have done so far is all right. PS this is the first thing im trying to run on linux (trying to migrate from Windows) so try not to be to technical if you can. 

Thank you. :)

---

### Post by aysiu on 2005-10-29
When instructions say *type such-and-such*, it's usually meant to be in a terminal. To open a terminal, go to Programs > Accessories > Terminal. You should get a black window with white text that says something like: ```
eighteenblue21grey@ubuntu: ~$
``` That's where you type commands. This tutorial may help:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html)

But I suspect you probably have to have compiling tools first. So in the terminal type this in ```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by eighteenblue21grey on 2005-11-29
[QUOTE=aysiu]When instructions say *type such-and-such*, it's usually meant to be in a terminal. To open a terminal, go to Programs > Accessories > Terminal. You should get a black window with white text that says something like: ```
eighteenblue21grey@ubuntu: ~$
``` That's where you type commands. This tutorial may help:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html)

But I suspect you probably have to have compiling tools first. So in the terminal type this in ```
sudo apt-get update
sudo apt-get install build-essential
```[/QUOTE]

Thank you for your help aysiu, i added those components and followed the tutorial and have got further, but i have come up against another wall;

When i try and run PengAol.conf in the terminal, i get an error like permission denied, as far as i can work out this is something to do with sudo, i dont think i am using it correctly though, here is what happens (roughly);

oz@ubuntu: ~$ cd etc/Pengaol
oz@ubuntu: ~$ ./PengAol.conf
permission denied
oz@ubuntu: ~$ su
Password: pass           // i typed my password that i use to login to Ubuntu 
Sorry!
Login failure

Any ideas people?

---

### Post by eighteenblue21grey on 2005-11-29
Anyone?

---

### Post by Bachstelze on 2005-11-29
This tutorial was obviously not written for ubuntu. Type "sudo -s" instead of su and it should work

---

### Post by sethmahoney on 2005-11-29
I totally thought I saw PengAOL in the repositories.  Did you try looking there before you went through this install procedure?

---

### Post by Bachstelze on 2005-11-29
[QUOTE=sethmahoney]I totally thought I saw PengAOL in the repositories.  Did you try looking there before you went through this install procedure?[/QUOTE]

You are totally right...

@topicstarter > just run 

```
sudo apt-get install penggy
```

---

