---
title: "broken dependency in Ubuntu 12.04.5"
date: 2017-07-20
forum: General Help
---

### Post by kpapadim on 2017-07-20
command "sudo apt-get check" gives me the following

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libnss3-1d : Depends: libnss3 (= 2:3.15.4-1ubuntu7) but 2:3.26.2-0ubuntu0.12.04.1 is installed
E: Unmet dependencies. Try using -f.
```

"sudo apt-get install -f" does not correct the problem

below is my /etc/apt/sources.list :

```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security universe main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed universe main
```

Moreover, I had texlive installed previously. I did some purge/remove, so I think I messed it up. Now latex does not build 

thanks
kyprianos

---

### Post by howefield on 2017-07-20
Might be worth knowing what is in your sources.list.d folder as well.

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

In any event Ubuntu 12.04 is a dead as the dodo, better to update to a supported version.

---

### Post by kpapadim on 2017-07-20
ok, >  egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*  gives


```
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security universe main
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe main
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed universe main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-talkplugin.list:deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
/etc/apt/sources.list.d/google-talkplugin.list.save:deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
/etc/apt/sources.list.d/oneiric-partner.list.distUpgrade:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner #Added by software-center
```

---

### Post by kpapadim on 2017-07-20
Moreover, it seems that I cannot install anything new now
Ubuntu software center says
>  Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?

Aand when I try to repair, I get the following message
>  Package operation failed. The installation or removal of a software package failed

---

### Post by vasa1 on 2017-07-20
Pay attention to this:
> **howefield said:**
> ...
In any event Ubuntu 12.04 is a dead as the dodo, better to update to a supported version.
:(

---

### Post by Yellow Pasque on 2017-07-20
[https://askubuntu.com/a/91821](https://askubuntu.com/a/91821)

---

### Post by deadflowr on 2017-07-20
Ubuntu 12.04 is mostly dead, to quote Miracle Max.
But still alive for those willing to pay for the extended support:
[https://insights.ubuntu.com/2017/03/14/introducing-ubuntu-12-04-esm-extended-security-maintenance/]("https://insights.ubuntu.com/2017/03/14/introducing-ubuntu-12-04-esm-extended-security-maintenance/")

That said +1 to upgrading to a supported release (14.04 comes to mind) if you do not have the paid support option.
(It's also not been very clear on how long said ESM support will actually run for: 6 months? A year? Or will it end tomoorow?)

---

