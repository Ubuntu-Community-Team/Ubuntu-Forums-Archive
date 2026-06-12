---
title: "synaptic problem - &quot;dpkg was interrupted, you must manually run 'dpkg --configure -a'"
date: 2007-05-27
forum: General Help
---

### Post by maxepad on 2007-05-27
the message i recieve any time i try to run a package manager is

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." 

also, im not sure if its related rythmbox crashes on start-up.

---

### Post by christhemonkey on 2007-05-27
Sounds like something has happened to interrupt synaptic whilst it was installing something.

Easy to fix, just do what it says and type into a terminal:
```
sudo dpkg --configure -a 
```

---

### Post by leopard6661 on 2007-05-30
I had the same problem with this error messege, I did what *christhemonkey* said 

Code:

sudo dpkg --configure -a

Then I re-opened synaptic and got this new messege:

E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I did try to install second life and it was installed but doesnt work though
I dont know what to do
Please help

---

### Post by JohnKopf on 2007-09-05
I have the same problem...

I ran update manager, which failed;  I had to reboot, which found a number of bad files - fixed those, and now when I try to run update manager I get:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

(I have no idea who to "report" this to!)

I found I had to use sudo (instead of su as instructed), but I get back:

johno@Mark:~$ sudo dpkg --configure -a
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
johno@Mark:~$ 

...So, what do I need to do next?  Can I reinstall it using the CD I originally booted from?  OR, do I have to download something and do it myself?  If the latter, can someone give me a list of instructions on downloading it and installing?

John Kopf

---

### Post by BlueEraser on 2007-10-18
thanks leopard6661 i ran the :

"sudo dpkg --configure -a"

and after a few seconds things were cleared up, and gibbon went on installing.  my error came about because my laptop crashed immediately after completing the update downloads, but before anything was installed..... gotta watch that battery life closely....thanks again

---

### Post by drtvasudevan on 2007-10-20
> **leopard6661 said:**
> I had the same problem with this error messege, I did what *christhemonkey* said 

Code:

sudo dpkg --configure -a

Then I re-opened synaptic and got this new messege:

E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I did try to install second life and it was installed but doesnt work though
I dont know what to do
Please help

similar problem.did anyone succeed in solving it?
problem it tries to go on downloading something and that is not getting done.

> --07:23:24--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
  (try: 3) => `./install_flash_player_9_linux.tar.gz'
Connecting to fpdownload.macromedia.com|1.0.0.0|:80... 
why cant it quit after a few trys?

tv

---

### Post by g2g591 on 2007-10-20
you need to go and get the secondlife.deb that you installed it with,
 "E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it."

---

