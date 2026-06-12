---
title: "Installed Server, boots to command line"
date: 2007-05-28
forum: General Help
---

### Post by mac173 on 2007-05-28
I installed ubuntu server with the LAMP option, but when I boot up I get a command line and no GUI. 

How do I load the GUI?

---

### Post by taurus on 2007-05-28
There is no window manager (GUI) if you install server version.  So, if you want Gnome, you need to install it.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by mac173 on 2007-05-28
Thanks, its installing now. 

Once I have it installed, will I be able to get it to boot to Gnome? I know a noob should prolly not be messing with a server, but I want to learn something about Apache, and set up a web page server on my home network. Doing it from command line will be a very LONG learning curve........

---

### Post by strabes on 2007-05-28
You might not want everything that comes with ubuntu though. To install a basic gnome system, just run ```
sudo aptitude update
sudo aptitude install gnome-core
sudo /etc/init.d/gdm start
```

---

### Post by taurus on 2007-05-28
When you turn on your machine, it will boot into GUI login screen (gdm) so you just have to log in with your name and password.  Then, you are using Gnome window manager.

---

### Post by mac173 on 2007-05-28
OK, Gnome installed, but when I reboot, I get this message..

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?

I said yes and got...

X: cannot stat /ect/X11/X (No such file or directory), aborting.

What now?

I have an ATI 9600XT Video card, is this the problem?

---

### Post by taurus on 2007-05-28
Reconfigure X with

```
sudo dpkg-reconfigure xserver-xorg
```
When done, see if X is running now with

```
startx
```

---

### Post by mac173 on 2007-05-29
Taurus, I did that, and got the exact same result as before. I tried it a second time, but no change. 

I can always reinstall if needed. 

Just to clarify what I am trying to do. 

I have ubuntu installed on a second hard drive on the machine. I want to dual boot, and have a combination workstation and server. I plan on writing and serving a web page on my home network for learning purposes. This is why I want the GUI on a server. 

Should I reinstall?

---

### Post by blacksadness on 2007-05-29
hey why do a server installation if you already want a graphical system, if you have ubuntu go in synaptic, and in the edit menu there's an option to select a set of packages i'm not home  now so i forgot the option name but it lets you select selected setups to install one of the option is LAMP server that would install what you need for a server

---

### Post by mac173 on 2007-05-29
OK, so I can just install the workstation CD (and get all the programs it has) and then install the LAMP server stuff?

Sounds like that is what I should have done in the first place, live and learn.....

Is that gonna solve the problem I am having?

---

### Post by blacksadness on 2007-05-29
> **mac173 said:**
> OK, so I can just install the workstation CD (and get all the programs it has) and then install the LAMP server stuff?

Sounds like that is what I should have done in the first place, live and learn.....

Is that gonna solve the problem I am having?

when you installed ubuntu-desktop it should have installed what the workstation cd has, which is weird because you shouldn't have had the X problem, if you dont' have valuable data on the server installation i would recommend going the other way arround.. (desktop first then install the LAMP option)

---

### Post by mac173 on 2007-05-29
> **blacksadness said:**
> when you installed ubuntu-desktop it should have installed what the workstation cd has, which is weird because you shouldn't have had the X problem, if you dont' have valuable data on the server installation i would recommend going the other way arround.. (desktop first then install the LAMP option)

Well, I don't know if I have valuable data on the server installation. I downloaded both the Workstation and the Server install software, and have them on disk. I did do the checksums on them. I only have installed what is on the server disk, and then the procedure discribed earlier in the thread that installed Gnome. 

I guess the X server problem is not related to the server installation specifically. Will I lose any software by installing the Workstation CD first, then adding the LAMP software?

---

### Post by blacksadness on 2007-05-29
well the workstationi cd would install gnome and the desktop applications, if you put the server cd you will automatically detect it adn promt you to add it to you repository, installing lamp after that would be easy.. what i meant by valuable data is personal settings and programs you added from outside the repositories i guess you don't have any on the server install..

---

### Post by dweez on 2007-05-29
There is no difference between regular Ubuntu and the Server edition except for applications installed by default.  Server is stripped down more but you could just as easily get it to a be identical/similar to regular Ubuntu by installing the missing apps.  As you noticed, one major difference is that Server doesn't install a windows manager by default.

If all you want to do is play around and learn some web stuff, just use your regular Ubuntu install and follow the instructions at this link to get LAMP running:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by mac173 on 2007-05-29
Thanks, I think I will do that tonight. 

The workstation should work fine, as I have run the OS from the CD several times without problem. 

I will post a new thread if I have problems with the workstation install. 


Once again, thanks to all of you who posted answers for me. I have printed the thread for future reference, and to look up the commands so I know what it was they did. The whole purpose of this is to learn, but starting on command line is biting off more then I can chew!

---

