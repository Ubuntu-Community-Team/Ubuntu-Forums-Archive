---
title: "Help getting Amarok!"
date: 2005-10-29
forum: General Help
---

### Post by mokeyjoe on 2005-10-29
How do I install Amarok? In Synaptic I mark it for installation but it says that amarok-arts and amarok-engines are dependencies. If I try to install these it tells me amarok is a dependency. It seems like a catch-22, so what do I do??

---

### Post by aysiu on 2005-10-29
[QUOTE=mokeyjoe]How do I install Amarok? In Synaptic I mark it for installation but it says that amarok-arts and amarok-engines are dependencies. If I try to install these it tells me amarok is a dependency. It seems like a catch-22, so what do I do??[/QUOTE] That's weird. Maybe your /etc/apt/sources.list contains conflicting repositories. Try following these instructions: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by mokeyjoe on 2005-11-06
OK, I copied the repository info from that site, which was different to what I had (backports address). Synaptic gave me an error message when it started but it seemed to download Amarok OK. So how do I get it to start up? There's nothing in the gnome menu that says Amarok. :???:

---

### Post by psyguy92 on 2005-11-07
Maybe try exiting and restarting Gnome (or KDE)?  It worked for me.  By the way, I just tried out Amarok (was using Rhythmbox), and within the first 30 seconds, I fell in love ;)

psyguy92

---

### Post by mokeyjoe on 2005-11-07
I've tried restarting everything. By the way it doesn't help things when you tell me how great Amarok is! Lol. I really want to try it but its just not working.

:(

---

### Post by psyguy92 on 2005-11-07
[QUOTE=mokeyjoe]Synaptic gave me an error message when it started but it seemed to download Amarok OK. So how do I get it to start up? There's nothing in the gnome menu that says Amarok. :???:[/QUOTE]

Hmm. Have you tried from the command line?


```
amarok
```

Check if it's installed?
```
dpkg -s amarok
dpkg -s amarok-engines
```

If they aren't installed, then perhaps manually downloading the .deb files (search for them) and installing manually would help.  I've overcome dependency problems like this using RPM-based distros by installing the base package and it's dependency on the same line.  It would be something like this:
```
dpkg -i *base_package_name*.deb *dependency_name*.deb
```

That's about all I know to try, except using the -f (force) option in dpkg with manually downloaded files.  It's my understanding that that can be risky though.  If that fails, maybe installing from source would work.  It's odd.  Mine installed nicely with synaptic.  

Good luck!

psyguy92

---

### Post by mokeyjoe on 2005-11-10
I think I tried it from the command line - I don't entirely remember. I'll check if its installed like you suggest. Hm, I don't trust synaptic much. Can I apt-get it?

---

### Post by psyguy92 on 2005-11-10
[QUOTE=mokeyjoe]I think I tried it from the command line - I don't entirely remember. I'll check if its installed like you suggest. Hm, I don't trust synaptic much. Can I apt-get it?[/QUOTE]

Synaptic is the same thing as apt-get, only with a GUI (graphical interface).

To manually download, go here: [http://kubuntu.org/packages/amarok-1.3.5/]("http://kubuntu.org/packages/amarok-1.3.5/")
Be sure to grab the correct files for your system (probably you need the 386 deb files).

If base + engine doesn't do it for you, grab the gstreamer deb and try to install in conjunction with the base:
[http://www.kubuntu.org/announcements/amarok-1.3.5.php]("http://www.kubuntu.org/announcements/amarok-1.3.5.php")

If all else fails, "Use the source, Luke" (stealing someone's sig ;) )

---

