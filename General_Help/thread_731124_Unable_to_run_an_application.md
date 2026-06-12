---
title: "Unable to run an application"
date: 2008-03-21
forum: General Help
---

### Post by rmaries on 2008-03-21
Hi,

I am new to Linux,

I installed a broadband client. While running I am facing the following problem.

$ sifyconnect
sifyconnect: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory

Can any one give me a solution for this

---

### Post by forrestcupp on 2008-03-21
Make sure it is installed.
```
sudo apt-get install libssl0.9.8 libssl-dev
```
You may have the main lib installed, but you probably don't have the dev installed.  That's probably what it is needing.

---

### Post by rmaries on 2008-03-21
Thanks.

But yet the problem didnt get solved.

While typing the above command, I got the following error


$ sudo apt-get install libssl0.9.8 libssl-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libssl0.9.8 is already the newest version.
E: Couldn't find package libssl-dev


Moreover while startine my system  with ubuntu linux, I got the following message

The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet"

My system is too slow when operating in ubuntu linux. 
How can I rectify this problem

---

### Post by forrestcupp on 2008-03-22
> **rmaries said:**
> 
E: Couldn't find package libssl-dev


Weird.  I have it in mine.  Do you have the Universe and Multiverse repos enabled?  Open up Synaptic and go to Settings->Repositories.  In the 'Ubuntu Software' tab, make sure they're all checked and close the window.  Click the Reload button, then do a search for **libssl**.

Hopefully the libssl-dev package is in there now.  If so, install it with Synaptic and try what you were doing again.

---

### Post by rmaries on 2008-03-23
Thanks. Problem got solved

---

