---
title: "Dropbox works only for some users"
date: 2016-08-06
forum: General Help
---

### Post by WDYSUN on 2016-08-06
Dear All,

all I have Ubuntu 14.04 on which it is installed nautilus-dropbox 1.6.1-1. I 
have several users on this machine and I usually work with the account that also 
does sudo operations. 

The strange thing is that while I am able to use dropbox with no problems on my 
account, when other users on this machine access dropbox it asks
for login/password and after that it says that I am using an old version
of Dropbox and an updated version is required.

How is that possible? Does not work the same for two accounts on the same 
machine. I also tried to do 

```
rm -rf   ~/.dropbox   ~/.dropbox-dist
```

on those accounts where this happens, but non way, It keeps asking for new 
software version.

I hope somebody can help

Best
Pierre

---

### Post by theonlytalkinggoat on 2016-08-06
How did you install Drop Box? Through apt, dpkg, tar or something else?

---

### Post by WDYSUN on 2016-08-07
> **theonlytalkinggoat said:**
> How did you install Drop Box? Through apt, dpkg, tar or something else?

To be honest I can't remember. When I installed dropbox I had to do several trials before to make it working but I think that finally I installed it through tar following this 

[http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/](http://www.srw2d.com/getting-dropbox-notification-working-in-elementary-os-freya/)

so I guess I installed with 

```
sudo apt-get install nautilus-dropbox
```

Regards
P

---

### Post by WDYSUN on 2016-08-17
Hello Dears,

nobody have a clue?

P

---

### Post by howefield on 2016-08-17
I'd suggest installing Dropbox via the .deb package downloaded from the Dropbox website after removing the existing dropbox package and ~/.dropbox, ~/.dropbox-dist folders.

What's the output from

```
cat /etc/os-release
```

---

