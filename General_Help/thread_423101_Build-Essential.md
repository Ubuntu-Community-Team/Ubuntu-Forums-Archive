---
title: "Build-Essential?"
date: 2007-04-25
forum: General Help
---

### Post by nckinfn04 on 2007-04-25
My build-essential package is missing. When I type in the
   sudo apt-get install build-essential, 
it says that there is no such package. What should I do?

---

### Post by taurus on 2007-04-25
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by nckinfn04 on 2007-04-25
Didn't work. I have Ubuntu 7.04 and no internet connection anyway. I'm trying to install ndiswrapper so I can get my wireless card drivers. It just keeps giving me error messages.

---

### Post by ashz on 2007-04-25
i suggest u download the packages u need manually...

[http://packages.ubuntu.com/feisty/devel/build-essential](http://packages.ubuntu.com/feisty/devel/build-essential)

then download the dependencies from there

put them on a cd and transfer them to the pc without internet..

cheers
ash

---

### Post by jocko on 2007-04-25
If you have the feisty CD build-essential should be there.

---

### Post by taurus on 2007-04-25
The package is on the CD.  Insert the CD into a drive and run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by nckinfn04 on 2007-04-25
Where do I extract the MAKE file? (make-dfsg_3.81.orig.tar)

---

### Post by stchman on 2007-04-25
> **nckinfn04 said:**
> Didn't work. I have Ubuntu 7.04 and no internet connection anyway. I'm trying to install ndiswrapper so I can get my wireless card drivers. It just keeps giving me error messages.

7.04 has the network-namager installed so just take your laptop and plug it into your router.  This will establish an internet connection.  Then you can apt-get.  Ubuntu is very internet oriented.

---

### Post by nckinfn04 on 2007-04-25
Sorry, I wasn't clear enough. I have a desktop and I use a USB wireless card to connect to a router we have.

---

### Post by stchman on 2007-04-25
> **nckinfn04 said:**
> Sorry, I wasn't clear enough. I have a desktop and I use a USB wireless card to connect to a router we have.

Take the RJ-45 cable from your desktop and plug it into your laptop temporarily and then you can get the packages you need.

---

