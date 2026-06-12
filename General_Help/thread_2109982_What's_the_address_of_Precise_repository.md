---
title: "What's the address of Precise repository?"
date: 2013-01-29
forum: General Help
---

### Post by TheHimself on 2013-01-29
I'm stuck with Ubuntu 10.10 and want to upgrade to Precise. Last time I was stuck with a no-longer-supported Ubuntu and wanted to upgrade, I added the new repository address to "Software Sources". But now that I've added
 ```
http://archive.canonical.com/ubuntu precise main
```
I get error massages. It seems that the format has changed. Can somebody help me?

---

### Post by vasa1 on 2013-01-29
Why don't you just do a new install? Back up your data files. I suspect config files may not be of much use. Make a live CD/USB. Try it out. See if you like it. See if your hardware likes it.

---

### Post by dino99 on 2013-01-29
> **TheHimself said:**
> I'm stuck with Ubuntu 10.10 and want to upgrade to Precise. Last time I was stuck with a no-longer-supported Ubuntu and wanted to upgrade, I added the new repository address to "Software Sources". But now that I've added
 ```
http://archive.canonical.com/ubuntu precise main
```
I get error massages. It seems that the format has changed. Can somebody help me?

set "precise" instead of the actual release inside /etc/default/sources.list, then update & yadda yadda ;)

---

### Post by ibjsb4 on 2013-01-29
```
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
```

Thats the way mine reads.

---

### Post by TheHimself on 2013-01-29
Thank you ibjsb4. I changed it to what you provided. But now when I want to upgrade I get the following error from Synaptic:

E: Could not perform immediate configuration on 'python-minimal'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)


My apt.config file is empty and I don't know what to do.

---

### Post by ibjsb4 on 2013-01-29
Before you go any further, maybe you should be sure your sources list is right.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by TheHimself on 2013-01-29
Thank you. I used that website and modified sources.list but I still get the same message.

If I want to manually upgrade python-minimal then it wants to remove some packages including rhythmbox, software center, aptdaemon, apturl, etc.

---

### Post by Dodeca on 2013-01-29
Is this a bug report on your same problem?

[https://bugs.launchpad.net/ubuntu/+source/python-defaults/+bug/990740](https://bugs.launchpad.net/ubuntu/+source/python-defaults/+bug/990740)

---

### Post by TheHimself on 2013-01-29
Yes, it seems to be the same thing. When I run the following (which is advised there)

```
sudo apt-get install -o APT::Immediate-Configure=false -f apt python-minimal
```

I get:

The following packages have unmet dependencies:
 libpango1.0-0 : Breaks: plymouth (< 0.8.2-2ubuntu19) but 0.8.2-2ubuntu5.1 is to be installed


If I want to upgrade plymouth, Synaptic wants to remove the packages I mentioned above.

---

### Post by TheHimself on 2013-01-29
OK, I did 
```
sudo apt-get install -o APT::Immediate-Configure=false -f  gdebi
``` 

because debi was one of the packages that was going to be removed. This went through solved the problem of broken packages so I was able to upgrade and have a running system now. Although the gnome applications look ugly now ...

---

