---
title: "Help with Motion"
date: 2016-09-17
forum: General Help
---

### Post by parly2 on 2016-09-17
Hi,

I recently had a hard drive corrupt on a computer I use for my motion webcams. I have just done a fresh install of 10.04 and I am trying to get motion back setup but keep running into issues. When I attempt to apt-get motion the following error comes back: 
```

user@dt:~$ sudo apt-get install motion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package motion

```

I have now tried to download the .deb file and install it manually and receive this error:
```

**_*Package Installer*_**
Package: motion
Status: Error: Dependency is not satisfiable: libavcodec1d (>= 0.cvs20070307)

```

I know when I did this before there were a few things that needed to be changed because motion hadn't been updated in awhile but I cannot remember what they were. If anyone can tell me why I am getting these errors and a work around, it would be greatly appreciated.

Thanks in advance!

---

### Post by Impavidus on 2016-09-17
Ubuntu 10.04 is obsolete. Its repositories have closed, and therefore you cannot use apt-get to install anything. Better install a supported release of Ubuntu. If the hardware is old, consider a lighter flavour.

---

### Post by parly2 on 2016-09-17
so is there no way to fix this?

Status: Error: Dependency is not satisfiable: libavcodec1d (>= 0.cvs20070307)

---

### Post by ajgreeny on 2016-09-17
> **parly2 said:**
> so is there no way to fix this?

Status: Error: Dependency is not satisfiable: libavcodec1d (>= 0.cvs20070307)
Not in a simple way, no, there isn't.

The repositories for 10.04 do still exist but already have not been updated for over a year so everything that you could find in the old repos would be out of date and therefore potentially insecure, and the web address for 10.04 is now not where it was when then OS was still supported.
You would need to rewrite your sources.list file with
```
deb http://old-releases.ubuntu.com/ubuntu/ lucid-main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse
```
and use that, but as I say the packages will all be out of date.

I would also advise you to re-install with a more up-to-date version, 14.04 or 16.04 depending on your hardware; if you have an AMD graphics card I suggest that for now you use version 14.04.3 or lower point version as 14.04.4 and 14.04.5 both suffer the same difficulties with AMD cards and drivers.

---

### Post by parly2 on 2016-09-17
I just hate the layout change ubuntu 11 brought but I guess thats my only option. Thanks for the help

---

### Post by ajgreeny on 2016-09-18
Why not use a different flavour of *ubuntu if you don'r like the unity desktop; there are plenty of them.

I am not a fan of unity either, but there is no point moaning about it as Ubuntu now means unity, which is why I changed to Xubuntu when gnome-2 disappeared, and I have never regretted doing so.

Have a look at Xubuntu, Kubuntu, Lubuntu, etc etc and use the DE you like best and which works for you.

---

