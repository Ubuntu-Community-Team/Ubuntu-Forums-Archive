---
title: "can't install...anything!"
date: 2008-04-24
forum: General Help
---

### Post by bighomer on 2008-04-24
I haven't got my kununtu installation on the net, but I wanted to install some software (like abiword for example). Installing .deb packages fails more often than it is successful. Installing from .src is a long and painful process, and you'll be damn lucky if it works. And installing from source code...well, I just recenly started fooling around with Linux again, and I swear I can't remember ever getting source code to compile, install, and successfully run an application. 

As I said, I have no internet connection on this machine, so I have yet to try the apt-get command, or whatever. But I seriously hope it works much better than the other methods I've tried. People say bad things about MS, myself included, but on XP it's as easy as downloading an executable file, installing it (in most cases), and running it. Why can't it be that simple on Ubuntu? What's with all the damn dependencies? Why can't dependencies be included within certain .deb packages? Is anyone else so fed up with this? Am I the only one having trouble here? 

Some deb files simply say dependencies not met. Others (more recently) will run but soon a popup tells me that the .deb does not exist or some crap. Others will run; the hard drive light will stay on for about fifteen seconds and then it will stop. The package install window will disappear. No 'package installed successfully' message this time. 

Abiword is just one of many apps that I've tried and failed to install on kubuntu (I think I finally did manage to get it running on Ubuntu once...) I'm no computer whiz programmer, but I'm not a dumbass either (well...not always). Someone please tell me there's an easier way to install an application on kubuntu. All I want is to be able to install (and run) an app without feeling the urge to bang my computer against the wall. Any help appreciated. 

ps. sorry for being so blunt, I'm just a little peeved right now. ](*,)

---

### Post by chrisccoulson on 2008-04-24
The repositories are full of software for you to install via the package manager (accessible via Synaptic or Add/Remove on Ubuntu), and the package manager will handle the dependencies for you. No need to go searching around websites for source files and deb files etc.

The example you gave (Abiword) is in Ubuntu main, and is an apt-get away.
```
sudo apt-get install abiword
```

---

### Post by xaenyx on 2008-04-24
Hm..  I'm not sure that you can achieve what you want without using an internet-dependant package manager.  The way I see it, you have two options--download the .deb packages from the repos for the package you need, or mirror synaptic itself.  To mirror the apt repository, you could use wubi to install ubuntu onto the windows partition (without repartitioning or anything), boot into it, install apt-mirror, mirror onto an external harddrive or dvds or something, and then hook that into the internet-less computer.

Also, there are lots of dependencies in windows--Whenever I install windows, I then need to install the latest Windows Installer, .net framework, gtk, etc etc.

---

### Post by bighomer on 2008-04-24
I thought apt-get was only for internet users, but here's what I got, Chris:
```

steven@gunslinger:~$ sudo apt-get install abiword
[sudo] password for steven:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package abiword
steven@gunslinger:~$

```

That's certainly an interesting approach xaenyx...I might try it, but I'm not sure I know how to mirror anything...or what apt-mirror is. Well, I'll see what I can do. Thanks for the replies guys.

---

### Post by elmer_42 on 2008-04-24
I think the best suggestion so far is the Wubi suggestion. I think the failure of abiword is due to no internet connection, but I may be wrong. I already have abiword. It may be of no use, but this is what Terminal returned.
```
staylor@Mariner:~$ sudo apt-get install abiword
[sudo] password for staylor:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
abiword is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

