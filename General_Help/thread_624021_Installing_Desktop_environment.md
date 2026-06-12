---
title: "Installing Desktop environment"
date: 2007-11-26
forum: General Help
---

### Post by nikhil_rathod on 2007-11-26
Hi guys,

I installed ubuntu 6.04 server. I know I can install GNOME desktop environment, but is there any way I can Install KDE. Nothing against gnome, but I love amaroke. 

It can be installed on GNOMe but better to keep things where they belong. :D

---

### Post by qqzhenyi on 2007-11-26
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

or if you want a cleaner KDE installation, run this:

```
sudo apt-get update
sudo apt-get install kde-core xorg kdm
sudo /etc/init.d/kdm restart
```

---

### Post by qqzhenyi on 2007-11-26
Argh sorry double post

more info here:
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)

---

### Post by nikhil_rathod on 2007-11-26
so if on top of Ubuntu 6.04 server I install kubuntu-desktop, means i'm converting by installation to Kubuntu 6.04 desktop. 

server is supported till 2011. So in this case till when my server installation going to get support, till 2011 or 2009?

---

### Post by qqzhenyi on 2007-11-26
Urgh... sorry I don't know. -__-

I'll switch to another LTS, Ubuntu 8.04 Hardy Heron

---

### Post by aysiu on 2007-11-26
What's 6.04?

Is that Dapper (6.06) or Feisty (7.04)?

The server will be supported as long as it's supposed to be supported, but any bugs or security issues involved with the GUI on top (Kubuntu, in this case) will not be addressed past the eighteen or thirty-six month cycle.

---

### Post by mikewhatever on 2007-11-26
> **nikhil_rathod said:**
> so if on top of Ubuntu 6.04 server I install kubuntu-desktop, means i'm converting by installation to Kubuntu 6.04 desktop. 

server is supported till 2011. So in this case till when my server installation going to get support, till 2011 or 2009?

You'll get support for server packages till 2009 and for desktop ones till 2009.

---

### Post by nikhil_rathod on 2007-11-26
my wrong its 6.06. 

So which verson of KDE will get install.

is there any way to install KDE 3.5.8. :D

---

### Post by nikhil_rathod on 2007-11-27
I installed ubuntu desktop over 6.06 server. And when I checked for the updates all the updates were for server, none of them were for GUI. So I guess it'll be supported till 2011.

thanks to all.

---

