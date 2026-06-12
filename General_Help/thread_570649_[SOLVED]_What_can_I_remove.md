---
title: "[SOLVED] What can I remove"
date: 2007-10-08
forum: General Help
---

### Post by Walter_Crankite on 2007-10-08
What are the things I can remove safely from ubuntu without affecting the system.

If I install XP, the first thing I do is remove a lot of crap the OS does not need. 
What are the things I can safely remove without having a crashing ubuntu.

There are a lot of packages installed, maybe obligatory and needed by Ubuntu.
I don't know if it is important.

Thanx in advance.
Walter
:guitar:

---

### Post by rich.bradshaw on 2007-10-08
Any software you like - don't remove system things though- Ubuntu doesn't have many pointless system things...

You can remove openoffice, the games, etc etc etc etc.

---

### Post by rich.bradshaw on 2007-10-08
Oh, there's not much point though, unless you really need hard drive space - it won't make it faster.

---

### Post by por100pre1 on 2007-10-08
You can remove already installed packages:

```
sudo apt-get clean
```

That should free some good space.

---

### Post by Walter_Crankite on 2007-10-08
Thx for your reply.

Won't it go faster?

With XP , you kick off useless progz, etc. 
Defragment the HD
Install tweakUI
Choose light Antivirus prog.

But with Linux, I once read (long time ago though), that there is no need to defragment. Do you know if this is the case?

So it won't go faster, damn.

I run a dual boot XP/Feisty and I must admit my XP box runs a little bit smoother.
Stability is not an issue on both of the OS's

wkr,
Walter

---

### Post by rsambuca on 2007-10-08
You can deactivate services you don't need by going to "System -> Administration -> Services"  Turn off anything you don't use.

As for defragmentation, you shouldn't really have to with ext3 under regular use.  By design, it more or less defrags itself just by regular use, so unless you have mega size files, you shouldn't have to worry about this.  You can also try the 'noatime' option in your /etc/fstab so you don't write to the drive just for accessing files.

---

### Post by Walter_Crankite on 2007-10-08
So how do you speed thing sup without adding extra hardware?

---

### Post by Walter_Crankite on 2007-10-08
I must correct this. 

Ubuntu is heavily packed with compiz fusion, kiba-dock lot of options enabled. So I guess it runs faster, XP just is less attractive.:lolflag:

---

### Post by Shazaam on 2007-10-08
When you uninstall some programs it will tell you that ubuntu-desktop will be removed. DON'T PANIC! lol. It's ok, the only problem you will have is during an UPGRADE. Then just go to Synaptic and re-install it before you upgrade (ie. Dapper to Feisty or Feisty to Gutsy).
XP is smoother? How? ATI video card? Video drivers installed?
Turn off unneeded services. Bluetooth if you dont have wireless, cupsys if you dont print; samba if you aren't on a network, etc.
No need to defrag. Different file system (journalizing)
No need for anti-virus. Well, maybe for any emails you forward to Windows users.
Sit back, relax and enjoy your freedom.

---

### Post by FuturePilot on 2007-10-08
> **Walter_Crankite said:**
> Thx for your reply.

Won't it go faster?

With XP , you kick off useless progz, etc. 
Defragment the HD
Install tweakUI
Choose light Antivirus prog.

But with Linux, I once read (long time ago though), that there is no need to defragment. Do you know if this is the case?

So it won't go faster, damn.

I run a dual boot XP/Feisty and I must admit my XP box runs a little bit smoother.
Stability is not an issue on both of the OS's

wkr,
Walter
No it won't got faster by removing programs. *But* it won't go slower if you install more programs. Hehe:D

---

### Post by bodhi.zazen on 2007-10-09
In my experience it is best to start with a minimal install and add only what you need.

If you are new to Ubuntu, take some time to familiarize yourself with the OS and options.

Next, take a look at light weight alternates. Why use open office when abiword will do. Why abiword when gedit will do. Or nano. Or, dare I say, vim ?

Next. light weight window managers like Fluxbox, Openbox, ICEWm, Enlightenment ...

Next you can look at something like Fluxbuntu, due out in a few days (with gutsy).

See these links : 

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

[http://users.skynet.be/six/gpure/tech/linux/apps.html](http://users.skynet.be/six/gpure/tech/linux/apps.html)

Arch Linux Forums : [http://bbs.archlinux.org/viewtopic.php?id=18880](http://bbs.archlinux.org/viewtopic.php?id=18880)

---

### Post by hostinghunts on 2007-10-09
here is what you can do:

search for nlite on googles , download it and insall it.

through this software you can make xp, vista installation fast 

and you can also remove uneccessary files which you do not need which will make your pc fast after installation.

you can compact xp to 300 mb and vista to 700 mb after this

remove uneccessary driver, files, default programes, and make your installation automated.


try it its free

---

### Post by rsambuca on 2007-10-09
> **bodhi.zazen said:**
> In my experience it is best to start with a minimal install and add only what you need.

If you are new to Ubuntu, take some time to familiarize yourself with the OS and options.

Next, take a look at light weight alternates. Why use open office when abiword will do. Why abiword when gedit will do. Or nano. Or, dare I say, vim ?

Next. light weight window managers like Fluxbox, Openbox, ICEWm, Enlightenment ...

Next you can look at something like Fluxbuntu, due out in a few days (with gutsy).

See these links : 

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

[http://users.skynet.be/six/gpure/tech/linux/apps.html](http://users.skynet.be/six/gpure/tech/linux/apps.html)

Arch Linux Forums : [http://bbs.archlinux.org/viewtopic.php?id=18880](http://bbs.archlinux.org/viewtopic.php?id=18880)

Well why stop there?  Why bother installing a Desktop Environment or Window Manager at all?  Just stick to a command line terminal.  :)

---

### Post by bodhi.zazen on 2007-10-09
> **rsambuca said:**
> Well why stop there?  Why bother installing a Desktop Environment or Window Manager at all?  Just stick to a command line terminal.  :)

[http://ubuntuforums.org/showthread.php?t=387598&highlight=Command+line+edition](http://ubuntuforums.org/showthread.php?t=387598&highlight=Command+line+edition)

---

### Post by rsambuca on 2007-10-09
> **bodhi.zazen said:**
> [http://ubuntuforums.org/showthread.php?t=387598&highlight=Command+line+edition](http://ubuntuforums.org/showthread.php?t=387598&highlight=Command+line+edition)

Yeah, that will be waaaaay faster than Windows!

---

### Post by tankertuff on 2007-10-09
I just recently got back to Ubuntu. I have noticed it boots a lot faster, and runs faster, if you're having problems, have you checked to make sure your graphics drivers are up to date, and like someone else mentioned, disabling any services you don't need. I can't really think of any other reason it'd run slower, every linux I've installed (save Linspire....yuk ['twas to see if it really was that bad]) has been much faster than windoze.

---

### Post by Walter_Crankite on 2007-10-09
Hello, 

I know my way arround in ubuntu, especially via command line. (I'm used to run the server edition).
Now I want the desktop edition on my laptop, because it just looks better and it is a good excercise to get really familiar with the advantages of the desktop.
 use Windows for a very long time and in there it's like, installing it and afterwards breaking it down and make it faster. 
I guess when I read the replies; It is not necessary to do that in Ubuntu. (all linux)

thx
Walter

---

### Post by bodhi.zazen on 2007-10-09
> **rsambuca said:**
> You can deactivate services you don't need by going to "System -> Administration -> Services"  Turn off anything you don't use.

Well, this is the best advice to speed up Ubuntu ^^^

Unnecessary services will slow you down , why run bluetooth if you have no bluetooth devices ?

etc ...

---

