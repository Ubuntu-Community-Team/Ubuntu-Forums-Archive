---
title: "flash player update in firefox"
date: 2017-03-16
forum: General Help
---

### Post by missmoondog on 2017-03-16
i have the flashplayer plugin installed in firefox and it usually updates correctly through synaptic, which it did on one computer yesterday, to the current version of 25.0.0.127.

on a different computer today and checked for updates but did not get flashplayer updated, so still on 24.0.0.221.

was the newest version pulled or something?

thank you

---

### Post by howefield on 2017-03-16
Have both computers been flash enabled with the flashplugin-installer package ? This should provide version 25.0.0.127 which you have on one machine, whereas the adobe-flashplugin package is still delivering flash version 24.0.0.221 and has yet to be updated.

If both machines are using the flashplugin-installer package, perhaps it is phased updates, where updates are drip fed to users over the course of a day or so.

---

### Post by missmoondog on 2017-03-16
i installed flash using these commands:


    sudo add-apt-repository ppa:nilarimogard/webupd8

    sudo apt-get update

    sudo apt-get install freshplayerplugin

which i found here [http://www.pcworld.com/article/2993902/browsers/how-to-get-the-latest-version-of-flash-on-firefox-for-linux-after-adobes-abandonment.html](http://www.pcworld.com/article/2993902/browsers/how-to-get-the-latest-version-of-flash-on-firefox-for-linux-after-adobes-abandonment.html) quite some time ago and it has worked perfectly since on all 5 machines.

synaptic shows flashplugin-installer package is installed on here.

thank you

---

### Post by howefield on 2017-03-16
Oh, right.

I can't speak to that ppa in terms of why it would update on one machine and not the other. Sorry.

Just as an aside, as I understand it, there is no need for a ppa anymore to keep flash up to date, the flashplugin-installer package will keep flash on Firefox up to date now that Adobe is once more supporting flash on the linux platform. 

```
precise (12.04LTS) : 25.0.0.127ubuntu0.12.04.1 [security]: amd64 i386
precise-updates     : 25.0.0.127ubuntu0.12.04.1: amd64 i386
trusty (14.04LTS)   :25.0.0.127ubuntu0.14.04.1 [security]: amd64 i386
trusty-updates       : 25.0.0.127ubuntu0.14.04.1: amd64 i386
xenial (16.04LTS)   : 25.0.0.127ubuntu0.16.04.1 [security]: amd64 i386
xenial-updates       : 25.0.0.127ubuntu0.16.04.1: amd64 i386
yakkety (16.10)     : 25.0.0.127ubuntu0.16.10.1 [security]: amd64 i386
yakkety-updates     : 25.0.0.127ubuntu0.16.10.1: amd64 i386
zesty                     : 25.0.0.127ubuntu1: amd64 i386 
```

---

### Post by missmoondog on 2017-03-16
thank you, howefield!

don't know why, but after double checking that the flashplugin-installer was installed, and reinstalling it, it removed a couple things such as adobe-flashplugin and adobe-flash-properties-gtk. then flash totally quit working. went back and reinstalled those 2 items and flash worked again although with the previous version. just reinstalled the flashplugin-installer and now flash is working again and is updated to the newest version.

don't have a clue as to why or what i really did that made it work, but it does, great!!

thanks again! :)

---

### Post by howefield on 2017-03-16
> **missmoondog said:**
> don't have a clue as to why or what i really did that made it work, but it does, great!!

That'll do for me and you're welcome :)

---

