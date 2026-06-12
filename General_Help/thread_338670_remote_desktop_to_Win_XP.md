---
title: "remote desktop to Win XP"
date: 2007-01-14
forum: General Help
---

### Post by eXidos on 2007-01-14
Is there a way to remote desktop to my windows XP box frome my Ubuntu 6.10 box  like you would with xp's remote assistance? if so does anyone know where a good how-to would be? Both are in my lan.

Would wireless cards give enough bandwidth?

---

### Post by maxamillion on 2007-01-14
Yes wireless will be enough bandwidth.

```
sudo aptitude install rdesktop
```

```
rdesktop <ip or url to machine (url is server)>
```

```
man rdesktop
```
to see other options ...

I will warn that the colors are grainy, i think something like 16-bit color and every now and then there is a lag and you will have to minimize a window and re-maximize it when scrolling, but its a small annoyance.

Enjoy :)

---

### Post by Marsolin on 2007-01-15
You want [tsclient]("http://linuxappfinder.com/package/tsclient").  It gives you a graphical interface to rdesktop.  I find that I need to use 16-bit color for everything to display correctly.

---

### Post by pak33m on 2007-01-15
I connect from my Ubuntu 6.06 laptop to my work Windows XP desktop all the time with rdesktop. You don't even have to use the Terminal Services Client. I run a script that I created with the following:

rdesktop -ujharris -p -g1028x768 172.x.x.x

There are quite a bit more parameters that I could add here, but mostly care to connect with a 1028x768 resolution & my user name.

You should read the man rdesktop for more info for sure.  

I would not recommend Gnome-RDP, as I have had several bad experiences with it freezing up & crashing my connection.

Good luck.

---

### Post by vgrisham on 2007-02-11
When I try to install rdesktop (either through adept or through apt-get), I hit a wall. The terminal gives me this error: jenny@ubuntu:~$ sudo aptitude install rdesktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  rdesktop
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 101kB of archives. After unpacking 397kB will be used.
Writing extended state information... Done
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main rdesktop 1.4.1-1.1
  Could not resolve 'us.archive.ubuntu.com'
Setting up libstdc++6-4.1-dev (4.1.1-13ubuntu5) ...
Setting up g++-4.1 (4.1.1-13ubuntu5) ...
Setting up g++ (4.1.1-6ubuntu3) ...

Setting up build-essential (11.3) ...

Any ideas what I might be doing wrong?

Thanks,
Vaughn

---

