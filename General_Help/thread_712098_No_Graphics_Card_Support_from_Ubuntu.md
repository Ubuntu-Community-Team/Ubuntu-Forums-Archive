---
title: "No Graphics Card Support from Ubuntu"
date: 2008-03-01
forum: General Help
---

### Post by xMikeL on 2008-03-01
Hi,

I recently changed to ubuntu. everything seems fine except:

I cant get my video card work on ubuntu.

Okay, if i go to 'Restricted Drivers'

It shows the driver i need to install

If i try to enable it, it comes up with

'The software source for the package nvidia-glx-new is not enabled'

So what do i do next?

---

### Post by taurus on 2008-03-01
Sounds like you don't have any repos enable in /etc/apt/sources.list.  Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark in front of all the lines except the last one, Source code, and Cdrom in the window below.  Close it and press Refresh.  Close synaptic and see if you can install nvidia driver for your graphic card this time.

---

### Post by mips on 2008-03-01
Go into synaptic and enable the universe, multivers & 3rd party repositories.

---

### Post by xMikeL on 2008-03-01
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i typed dpkg --configure -a into the terminal but it said

dpkg: requested operation requires superuser privilege

damm.....

i am the only account

---

### Post by taurus on 2008-03-01
```
**sudo** dpkg --configure -a
sudo apt-get update
```

Even though you are the only account on your machine doesn't mean you are root.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by duncan.hawthorne on 2008-03-01
superuser privilege just means start the command with sudo
dpkg interrupted, means you closed some windows in the middle of installing something

---

### Post by xMikeL on 2008-03-01
thanks so much guys

problem solved

---

