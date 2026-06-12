---
title: "Really messed up BIG TIME"
date: 2006-11-30
forum: General Help
---

### Post by bugboy on 2006-11-30
Ok i was stupid first off.

i was removing some orphaned packages using synaptic and then the desktop just went now when i boot up i go straight into command line.

When i try to install the desktop i keep getting:

```
Some packages could not be installed. this may mean that you have requested an impossible situtation or if you are using the unstable distribution that some requied packages have not yet been created or have been moved out of Incoming
]ubuntu-desktop: Depends: gedit

E: Broken packages


```

when i try gedit i get:

```

gedit: Depends: gedit-common (=2.14.2-0ubuntu3) but 2.14.4-0ubuntu1 is to be installed

```


I'm using this machine as a webserver and file server but had the gui on for convenience. This is all working fine still but the gui and vncserve is not working.

I'm runing ubuntu 6.06 server.

Please help me its freaked me out

---

### Post by bugboy on 2006-11-30
bump as i need help

---

### Post by taurus on 2006-11-30
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by bugboy on 2006-11-30
wicked that seems to be working.

But when i tried sudo apt-get it didn't want to work whats the difference?

---

### Post by taurus on 2006-11-30
Aptitude handles dependencies better than apt-get...

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by bugboy on 2006-11-30
well so far it seems to be installing great.

What did i do wrong then to make that mess up so much?

---

### Post by taurus on 2006-11-30
I guess you removed some files you were not supposed to...  Just be careful next time you want to remove something.

---

