---
title: "Installing tarball with no /.config file ? Ultrascan III program"
date: 2017-07-01
forum: General Help
---

### Post by brianare on 2017-07-01
Hello, I am trying to install this program on my computer and I  am running into some trouble. 

The website gives instructions on how to install it, but I get lost halfway through: [http://www.ultrascan3.uthscsa.edu/installation.php](http://www.ultrascan3.uthscsa.edu/installation.php)

I am able to untar and move it into the /usr/lib/ directory where I want to install it, but I am not sure what to do from that point. 

I followed the instructions and I know what those commands do, but I'm not sure how they apply to the situation.

If anyone can be kind enough to help me solve this puzzle, I would greatly appreciate it. 
-Brian

---

### Post by monkeybrain20122 on 2017-07-01
It is a binary (already compiled) with its own libraries rather than source codes,  there is  no need to compile it therefore no configure makefile and the likes. "Installation" is basically just copying the archive to appropriate directories and making the symlinks and setting the environmental variables following the instructions so the system can find it.

---

### Post by SeijiSensei on 2017-07-01
I strongly recommend installing any software that doesn't come from the repositories under /usr/local.  You'll see lib, bin, sbin, and etc directories under /usr/local into which the appropriate files can be copied.  /usr/local/sbin and /usr/local/bin are usually included in the default PATH so you can launch programs in those directories as easily as ones in /usr/bin and /usr/sbin.

---

### Post by brianare on 2017-07-01
Thanks for you reply. Okay that really helps. How do i set the envious variables? In the terminal? Also how would i run/find the program after i install it

Thanks again. I really do appreciate it. Im learning a lot : )

---

### Post by monkeybrain20122 on 2017-07-02
Ok. Here is the step by step. 

First extract the downloaded archive (say us3-Linux64-3.5.2311.tar.gz) somewhere. It doesn't have to be /usr/lib. You can just extract it in your home. It is cleaner that way IMO.

then make a symbolic link to /usr/local/lib (following [COLOR=#000000]SeijSensi's advice)

[/COLOR]sudo ln -s /full/path/to/us3-Linux64-3.5.2311 /usr/local/lib/ultrascan3

[COLOR=#000000]so e.g if you extracted the tarball in your home

[/COLOR]
```
sudo ln -s /home/your-username/us3-Linux64-3.5.2311 /usr/local/lib/ultrascan3
```

[COLOR=#000000]Now to set the environmental variables, open an empty text file, put in these lines

[/COLOR]```
export ULTRASCAN=/usr/local/lib/ultrascan3
export PATH=$PATH:$ULTRASCAN/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib/ultrascan3/lib
[COLOR=#000000]
[/COLOR]
```


Give the file a name, say uscan3.conf and save it somewhere. I would create a subdirectory in your home called Scripts and save it there, but it doesn't matter, you can just dump it in your home.

Then everytime you start the program in the terminal, start with

source /path/to/the/uscan3.conf

to set the environmental variables (where the system will look for files) What this does is just running the three commands in the conf file. The reason for creating a conf file is that it is more convenient to run one command instead of three, and it is a lot easier to remember

e.g if your script is in your home, then simpy

```
source uscan3.conf
```

or 
```

source ~/Scripts/uscan3.conf
``` if the file is inside /home/your-username/Scripts


If you want this to be automatic, so that you don't have to run this command everytime you use your software, you can put

```
source ~/Scripts/uscan3.conf
``` 

in  your .profile. It is a hidden file, you can view it by opening the file manager, choose either show hidden from the menu or press ctr +h. Note the "." in front. This way whenever you login these environmental variables will be set automatically. Some people do it for convenience but I kind of recommend against it because some libraries bundled with ultrascan may be in conflict with system's version, you don't want to override the system version unless you are using ultrascan. So I would suggest you manually set the environmental variable per session as above.

---

### Post by brianare on 2017-07-02
Thanks so much for the reply. I followed your instructions, but how do I run the program to get to its gui. I typed the source command to set the environment variables, but I'm not sure how to start the program.

Thanks again, so much! You're so kind for helping me : )

---

### Post by monkeybrain20122 on 2017-07-03
Well I don't know anything about your software, never used it, never heard of it. I can dl it and take a look when I go home, but perhaps you can check out its tutorial?

---

### Post by brianare on 2017-07-04
I looked at the website tutorial for hours before I posted and did not get as far as I have here (thanks again), but the tutorial does not supply enough info on how to start the program. I think the writers assumed that anyone installing the software would know how to run it, if they got that far. I know it's a lot to ask, but I would appreciate if you did take a look at it. It's just some program that colleges researches use. I'm trying to get it to work for my father-in-law. he needs to use it. Also, I have ran into tar.gz's like this in the past and they have always stumped me. I think this thread can help others who have similar issues when it comes to binary tar.gz/s


Thanks again (i'll keep working at it myself and post anything if I make progress)

Brian

---

### Post by monkeybrain20122 on 2017-07-05
Hi, I have downloaded it and had a look at it. If you open the folder us3-Linux64-3.5.2311 you will find a subfolder called bin. In it are the binaries. To start the gui you should be able to just click us_analyte_gui and if you like you can create a .desktop file (launcher icon) for it.  [but see **Edited **in the end]

But unfortunately it is not that simple because it will not start if you just follow the installation guide. By running it in the terminal you will get an error that says 

> This application failed to start because it could not find or load the Qt platform plugin "xcb"
in "".




So check whether libqxcb.so is installed in your system, in the terminal type
```

sudo updatedb

locate libqxcb.so
```

If it does not return anything, that means it is not installed, then you need to install it. But first you have to find out which package does it come from, so run
```
dpkg -S libqxcb.so
```

It will return libqt5gui5

so install that

```
sudo apt install libqt5gui5
```

But you are not done yet. us3 still won't run because it can't find libqxcb.so. It only looks at a very special place. First let's find out where libqxcb.so is installed in your system. run again updatedb and locate

In my system its path is /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so

For us3 to detect it you have to create a folder called platforms inside us3-Linux64-3.5.2311/bin(go inside bin, right click, create new folder and name it platforms), then put libqxcb.so in there. You can copy it or make a symlink

To make a symlink
```

sudo ln -s  /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so  /path/to/us3-Linux64-3.5.2311/bin/platforms/
```

Now I am doing this on Ubuntu 17.04 and it still won't run because libqxcb.so needs a file called libudev.so.0, you can find out by typing in the terminal 

```
ldd  /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so 
``` 
It will print out a bunch of stuffs and their paths in the system but next to libudev.so.0 it says "not found". 

So again locate libudev

I found that  there is only libudev.so.1, so I created a symlink to libudev.so.1 and just call it libudev.so.0

```
sudo ln -s /lib/x86_64-linux-gnu/libudev.so.1  /lib/x86_64-linux-gnu/libudev.so.0

```


It finally works! When I click on us3-Linux64-3.5.2311/bin/us_analyte_gui it starts the gui. Alternatively you can just type us_analyte_gui in the terminal (because of the environmental variables and the symlink we set in the installation, you don't need to type the full path) At this point a pop up appears and says that you must register to use the software (screenshots) So it works, once you get your license. Enjoy. :)

**Edited: **clicking only works if you put 
```
source ~/Scripts/uscan3.conf 
``` in your .profile. Otherwise you will have to run us_analyte_gui  in the terminal after you type the source command. I said in my previous post that I don't recommend putting that in your .profile, but it is kind of tedious to run a gui application in the terminal, so at the moment just put that line in your .profile, logout and login again for test, but this would mess up your paths so that some qt5 apps won't load. So once you have tested that it is working, remove that line from .profile, then create a script that goes

```
#! /bin/bash
source ~/Scripts/uscan3.conf
us_analyte_gui
```

Call it something like ultrascan3, make it executable (right click it, Properties > Allow executing file as program, or in the terminal, run 
```
chmod +x  /path/to/where/you/saved/ultrascan3
```
Depending on your DE there should be an option in the file manager to run these files by clicking . E.g if you use Ubuntu (unity) or Ubuntu gnome, open the File manager, choose Edit > Preferences > Behaviour and under executable text files  check Ask each Time. Then you can start your program by just clicking this file (or you can create a .desktop launcher to point to it)

---

### Post by brianare on 2017-07-07
Oh my god. you are the greatest. Such an in depth lesson. I cant thank you enough! I did it and it works. I learned so much about the locate command and the ln command. I never knew what those did before. Thanks again! You really are the best, monkeybrain : )!!!

---

