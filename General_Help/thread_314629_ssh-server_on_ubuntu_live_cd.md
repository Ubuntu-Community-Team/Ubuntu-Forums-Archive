---
title: "ssh-server on ubuntu live cd?"
date: 2006-12-07
forum: General Help
---

### Post by Batwomansman on 2006-12-07
hi,

i'm quite new to linux and this forum here. I would like to use an ubuntu live cd to grant me remote access to this machine. how can I give ssh access to other machines on a live cd?
Ideally I would like to have a customized live cd that allows me to access the machine running it without asking for a password using my public key. but first things first...

thanks you in advance!

cheers
batwomansman

---

### Post by taurus on 2006-12-07
I guess you can install it into the RAM and enable it!!!

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install openssh-server
```

---

### Post by lemonsCC on 2006-12-07
Dont forget that you may want to force a static ip from the liveCD so you dont have to ifconfig everytime.

---

### Post by taurus on 2006-12-07
But I guess as long as the machine is running (from LiveCD), the IP should be the same for the whole session.

---

### Post by engla on 2006-12-07
If installing it after boot isn't an option (it should work) there is a tool for making livecds called reconstructor:

[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by SyvanX on 2006-12-07
You would also need to copy the correct keys to your server every time you boot if you want password less logins.

---

### Post by lemonsCC on 2006-12-07
I figured he would be using the liveCD on multiple machines, else why not install ubuntu.

---

### Post by Batwomansman on 2006-12-08
thank you for your replies. 

yes, i need the cd for multiple machines. 

i'm using a program that can do parallel processing on a battery of workstations. The only requirement is that I need password free SSH access to the workstations. Linux is of course another requirement. I have access to a couple of computers (100 in fact) that are not in use. the only problem is that they are running with windows and i'm not allowed to mess with the installation... 
a reconstructed live cd with my application on it and the ssh settings will do the trick for me hopefully.


thx anyway!

batwomansman

---

