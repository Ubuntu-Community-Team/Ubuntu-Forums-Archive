---
title: "Is it unsafe to run Ubuntu without firewall?"
date: 2005-07-13
forum: General Help
---

### Post by SlugO on 2005-07-13
I was just wondering how safe it is to run Ubuntu, or Linux in general
without a firewall? I doubt that it's anywhere as dangerous as with Windows,
but are there some risks?

I just found this handy looking firewall, [Firestarter](http://www.fs-security.com/) and concidered installing it.
But I'm not sure if I even need it. Is there some firewall daemon in the kernel or something?

---

### Post by arnieboy on 2005-07-13
Most flavors of linux (including ubuntu) has a firewall called iptables running in the background all the time. However it is not a trivial task to configure it. Firestarter is not a firewall by itself but merely a GUI frontend to iptables which u can easily configure.
It is very important to have a firewall working on ur machine even if u are using linux and having firestarter to do the job for u is what u want. To install firestarer from terminal do a 
```
sudo apt-get install firestarter
```
and then follow the instructions on [http://ubuntuforums.org/showthread.php?t=26483](http://ubuntuforums.org/showthread.php?t=26483) to make firestarter run on startup.

---

### Post by az on 2005-07-13
On a default install, nothing is listening to anything from the outside world, so there is no need for a firewall.

If you are running software like ssh or any other kind of software where you get incoming traffic, you may want to consider a firewall.

---

### Post by rosslaird on 2005-07-13
But isn't it true that if you have a router (i.e. for a home network), it provides a firewall?

---

### Post by ProNoblem on 2005-07-13
[QUOTE=rosslaird]But isn't it true that if you have a router (i.e. for a home network), it provides a firewall?[/QUOTE]

I also thought this, I've also got a router and was thinking i was protected from the outside (i've got some portmappings for http, ftp and p2pstuff) but there's no DMZ active.

Should I also consider using a firewall now?

---

### Post by az on 2005-07-13
[QUOTE=ProNoblem]I also thought this, I've also got a router and was thinking i was protected from the outside (i've got some portmappings for http, ftp and p2pstuff) but there's no DMZ active.

Should I also consider using a firewall now?[/QUOTE]
A router typically acts as a firewall, yes.  A dmz is just a computer on your LAN that you put outside of your router so that it is exposed to the internet.

---

### Post by fatsi on 2005-07-13
At first i want to say that there are different kinds of routers. My one does its job good and my friend made a portscan on my ip and could only see the ports that i forwarded. I did not configure the ubuntu firewall, just 
running on default settings. (my router: smc barricade VBR7004)

To make your system as safe as possible choose passwords with numbers, letters and signs like:

b(H5/kU.! 

If someone wants to get in your system he needs at first the usernames and than the matching password. If you choose a easy word or better the same like user:admin password:admin its really easy for someone who knows what he does to get in your system.

If you use sshd you should set the port on a different than the dedault port. This is the config file where you have to change it. /etc/ssh/sshd.conf 

You should also check your auth.log almost once a week. /var/log/auth.log Also very usefull to see if somebody else hacked your system is chrootkit. a rootkit scanner! type chrootkit in the console.

But at last, for the normal linux using guy like me Ubuntu is safe enough in default settings ;)

---

### Post by amrust on 2005-07-13
[QUOTE=arnieboy]It is very important to have a firewall working on ur machine even if u are using linux and having firestarter to do the job for u is what u want. To install firestarer from terminal do a 
```
sudo apt-get install firestarter
```[/QUOTE]
Doing this gives me the following error:

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter
```

Any ideas how I can correct?

---

### Post by fatsi on 2005-07-13
Why dont u use synaptic? Maybe you didnt write it correctly ;)

---

### Post by amrust on 2005-07-13
I'm sorry. I'm new to Linux, and I don't know how to use Synaptic to load Firestarter or anything else, really. I just don't want to make a mistake and hose my system. Just now got Ubuntu installed properly.

So how do I set Synaptic to install/update Firestarter?

---

### Post by fatsi on 2005-07-13
synaptic is a gui for apt-get. you will find it taskbar - system. there you can search for firestarter and install it with one click ;)

---

### Post by amrust on 2005-07-13
I found and ran Synaptic, but when I search for firestarter, it can't find a package. I don't have it currently installed, maybe I need to find out how to tell Synaptic where to look?

I think I'm almost there.

---

### Post by Morimando on 2005-07-13
[http://ubuntuguide.org](http://ubuntuguide.org) <= look for 'adding extra repositories' and follow the instructions. Should be fairly easy.  There's also a section about firestarter, as far as i remember :)

---

### Post by veruus on 2005-07-13
You might have to edit your sources.list file

From a terminal:
```

$ sudo cp /etc/apt/sources.list /etc/apt/sources.list-20050713
[that's today's date ;) ]
$ sudo gedit /etc/apt/sources.list

```

Remove the #s from the following lines.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

and add:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

You'll have a lot more applications avilable to you.  Then you should be able to install firestarter with apt-get or Synaptic.

Edit:  Forgot to mention - update either Synaptic or run *apt-get update* after you have changed the sources.list file.

---

### Post by Takis on 2005-07-13
[QUOTE=amrust]I'm sorry. I'm new to Linux, and I don't know how to use Synaptic to load Firestarter or anything else, really. I just don't want to make a mistake and hose my system. Just now got Ubuntu installed properly.

So how do I set Synaptic to install/update Firestarter?[/QUOTE]
Dude you're new and you know how to use apt-get but not Synaptic? Respect. That's seriously cool.

Even though you can get Firestarter or Shorewall or whatever, I'd recommend getting a dedicated [firewall](http://www.smoothwall.org)/router. Even though it may be overkill, I find I worry less about whether I've accidentally just opened a couple of ports to the outside world by installing a new program or changing a setting here or there.

Granted, you can check and make sure your Ubuntu box doesn't have anything open, but for me, I know I'd make a mistake somewhere and leave something open. My firewall has all ports closed permanently and that's plenty good for me.

My two cents.

---

### Post by jon_gunnar on 2005-07-13
[QUOTE=amrust]I'm sorry. I'm new to Linux, and I don't know how to use Synaptic to load Firestarter or anything else, really. I just don't want to make a mistake and hose my system. Just now got Ubuntu installed properly.

So how do I set Synaptic to install/update Firestarter?[/QUOTE]

Why don't you just start out with a look at the excelent "Unofficial Ubuntu 5.04 Starter Guide" at

[http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html)

This guide gives a lot of tip in a very clear way.

---

### Post by amrust on 2005-07-14
Thank you for the repository info, and for the link to the Starter Guide. Both were a big help. I got the repositories I needed, and I have Firestarter installed. I even found a link how to get it to start automatically, and drop to taskbar on startup. At home, I do connect from behind a firewall/router, but for my wireless connection on the road, I wanted to get a software firewall up ASAP.

Excellent... Thanks again everyone!

---

### Post by arnieboy on 2005-07-14
[QUOTE=amrust]I'm sorry. I'm new to Linux, and I don't know how to use Synaptic to load Firestarter or anything else, really. I just don't want to make a mistake and hose my system. Just now got Ubuntu installed properly.

So how do I set Synaptic to install/update Firestarter?[/QUOTE]
since u are new to linux your first lesson would be to bookmark the following site:
[http://ubuntuguide.org](http://ubuntuguide.org)
u will find answers to most of your questions there. If not u can search in the forums on [http://ubuntuforums.org](http://ubuntuforums.org) and u will find more.
the reason why u cant install firestarter is because u dont have the correct repositories added or uncommented. U need to go to ubuntuguide.org and search for "How to add extra repositories". That will bring up the small and tidy section on how to add repositories on ubuntu so that installing and removing software becomes a breeze. After u successfully install firestarter u can refer to the following thread: [http://www.ubuntuforums.org/showthread.php?t=26483](http://www.ubuntuforums.org/showthread.php?t=26483)
This will tell u how to load firestarterat startup without typing in your sudo password everytime

---

