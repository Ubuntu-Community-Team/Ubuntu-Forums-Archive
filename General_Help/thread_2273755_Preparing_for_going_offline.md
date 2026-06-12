---
title: "Preparing for going offline"
date: 2015-04-15
forum: General Help
---

### Post by jonnyrobbie on 2015-04-15
I have a lubuntu 14.10 32bit which now works. But it is an old pc and I'll be moving it to a place without internet connection. I wanted to ask if there are some steps I should do before that. Should I downgrade to LTS, or even wait for 15.04 or just let it be? The only way it could get updated is via usb flash disk. If I wanted to install some packages in the future, how would I go downloading them (using another ubuntu64bit) to usb and then installing them on that lubuntu?

---

### Post by Holger_Gehrke on 2015-04-15
Use synaptic, it has an option to generate a download script and install the packages downloaded by that script.

---

### Post by nerdtron on 2015-04-15
Don't stay with 14.10. Downgrade to 14.04 which is a Long Term release supported until 2019.
Ubuntu 15.04 is not an LTS release so it's the same as staying with 14.10.

---

### Post by Bucky Ball on 2015-04-15
Well, 14.10 will be out of support and dead around July, 15.04 will have nine months support from a couple of weeks time, while 14.04 LTS is supported until 2019. I'd have to agree and say go for the LTS release for an offline machine. A lack of security updates will make no difference if offline. If you get it online, though, update pronto. Good luck. ;)

Ubuntu LTS releases = five years support (new LTS released April every second 'even' year, 2012, 2014, 2016, etc.); interim releases = nine months.

---

### Post by jonnyrobbie on 2015-04-15
well my point was that I don't think I would need a lts support. My idea was that if 14.10 works now, it would work even 2 years from now sice there wouldn't really be much change with that install.

---

### Post by Bucky Ball on 2015-04-15
True, it wouldn't matter about long-term support if the machine wasn't online. Only issue I can think of is if you get the opportunity to update the machine in a year at a friend's or wireless hotspot or somewhere else then you will be out of luck as the 14.10 repositories will be closed. If that's not an issue then you're home.

---

### Post by Frogs Hair on 2015-04-15
You might want look at the offline repository information while you still have an Internet connection. 14.10 won't be supported in two years, so the 14.04 suggestion is a good one. 

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by matt_symes on 2015-04-15
Hi

> If I wanted to install some packages in the future, how would I go  downloading them (using another ubuntu64bit) to usb and then installing  them on that lubuntu?

I would use 14.04 for the supported packages and then i would use 

```
apt-offline
```

to download the packages.

From man apt-offline.
> 
apt-offline  brings  offline  package management functionality to Debian based system.  It can be used to download packages
       and its dependencies to be installed later on (or required to update) a disconnected machine.  Packages can  be  downloaded
       from a different connected machine.

Another option is to use 

```
apt-mirror
```

This will mirror an entire repository so the download will be large as it will get *every package* from the repository (ie main or restricted or universe etc).

From man apt-mirror
> 
 A small and efficient tool that lets you mirror a part of or the whole Debian GNU/Linux distribution or any other apt
       sources.

I have used both in the past for offline machines. IIRC, I had to patch apt-online and write a post-mirror script for apt-mirror.

There are write-ups online. 

Like with all Internet tutorials though, don't follow then blindly. Make sure you know what they are doing.

Just my thoughts.

Kind regards

---

### Post by jonnyrobbie on 2015-04-15
I looked at the manpage of apt-offline and I found out stuff about updating, but what if I wanted to bring some new package (looging at man apt-get how would I use apt-get download foo)? Also if I wanted to downgrade to 04.lts, will it work if I just get 14.04 on usb and install it over 14.10, or do I have to backup and install fresh?

---

### Post by Rex Bouwense on 2015-04-15
If you wanted to installed Lubuntu 14.04 (which is only supported until April 2017 unlike its Ubuntu 14.04 brother which is supported for an addition two years) and you want to install it over Lubuntu 14.10 you must back up your data and do a fresh install.  A fresh install will erase all of your data and installed programs unless you install 14.04 along side of 14.10 in a dual boot fashion.

---

