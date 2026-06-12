---
title: "How to give myself permission to write in /usr"
date: 2015-04-30
forum: General Help
---

### Post by rcstck on 2015-04-30
Encountered this error
 ```
 /bin/mkdir: cannot create directory ‘/usr/share/xfce4’: Permission denied 
```

How do I go about giving myself permission to write in that directory?

---

### Post by deadflowr on 2015-04-30
[sudo]("https://help.ubuntu.com/community/RootSudo")

but are you trying write in an existing directory, or make a new one?

---

### Post by rcstck on 2015-04-30
I found a tutorial at this site [http://www.linuxreaders.com/2012/05/install-xfce-using-source-fedora-ubuntu.html](http://www.linuxreaders.com/2012/05/install-xfce-using-source-fedora-ubuntu.html) about installing xfce4.10.  It seemed clear about everything except where to actually do the installation process.

the ./configure command for each package is just listed as

```
 ./configure &#8211;prefix=/usr &#8211;sysconfdir=/etc && make && make install 
```

I understood that to mean the /usr directory was where they were instructing me to install it.  Running sudo before that command did not do anything, unfortunately.

---

### Post by ajgreeny on 2015-04-30
Adding xfce-4.10 to what?

Why not just run ```
sudo apt-get install xfce4
``` or if you want to try the full xubuntu experience why not ```
sudo apt-get install xubuntu-desktop
```

---

### Post by rcstck on 2015-04-30
Deadflowr, thanks for your advice, I did not know I could run that command as

```
  ./configure &#8211;prefix=/usr &#8211;sysconfdir=/etc && make && **sudo** make install 
```

---

