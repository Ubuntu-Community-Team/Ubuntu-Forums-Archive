---
title: "lsb_release -a help"
date: 2018-01-17
forum: General Help
---

### Post by chancuu on 2018-01-17
Okay, so i'm not sure where to put this. It also isn't that big of a deal, but it just bothers me. So a while back i installed some of elementary os on top on my ubuntu 16.04. Well recently I changed my theme and icons for unity and what not, and so i decided to uninstall the elementary theme. i removed the repository and as far as i know i removed everything elementary. The thing is when i do lsb_release -a it shows 

No LSB modules are available.Distributor ID:	elementary
Description:	elementary OS 0.4.1 Loki
Release:	0.4.1
Codename:	loki


so i was just wondering how i could fix this. only reason this bugs me is i would like to see if i have 16.04.3. i'm guessing i do seeing how everything seems up to date. but any insight into this would be great. sorry if this is in the wrong place, wasn't really sure where to put it. also sorry i know this is kind of a silly question. but i'm still kind of new to dealing with all this kind of stuff, i have decent knowledge of linux, mainly ubuntu, but i still have a lot to learn, and i don't want to dig to deep and end up messing something up and have to reinstall, i'm not sure where my disc is at, and i don't want to lose everything again. i have a bad habit of getting over my head and breaking something and having to do a fresh install, and i don't want to have to do that again ha. Thanks for any help.

---

### Post by Frogs Hair on 2018-01-17
You might start by reinstalling the ubuntu-desktop package. Chances are there are a number of Elementary packages on the computer.  

```
sudo apt install ubuntu-desktop  
```

```
sudo apt-get autoremove --purge elementary-desktop

```

See PPA Purge section if needed:

[https://askubuntu.com/questions/825306/how-to-remove-pantheon-de-from-ubuntu-16-04](https://askubuntu.com/questions/825306/how-to-remove-pantheon-de-from-ubuntu-16-04)

---

### Post by deadflowr on 2018-01-17
What does
```
apt-cache policy base-files
```
show?
Post the full output, please.

---

### Post by chancuu on 2018-01-17
this is what it shows

base-files:
  Installed: 9.4ubuntu4.5+elementary12~ubuntu0.4.1.1
  Candidate: 9.4ubuntu4.5+elementary12~ubuntu0.4.1.1
  Version table:
 *** 9.4ubuntu4.5+elementary12~ubuntu0.4.1.1 100
        100 /var/lib/dpkg/status
     9.4ubuntu4.5 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
     9.4ubuntu4 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
     7.2ubuntu5 500
        500 [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) trusty/main amd64 Packages

---

### Post by howefield on 2018-01-17
Just out of curiosity, what is the output of..

```
cat /var/log/installer/media-info
```

---

### Post by deadflowr on 2018-01-17
I'm not sure if a quick reinstall will revert the base-files package back to the Ubuntu version.
(And I am 100% positive trying to remove it will cause major issues, so DO NOT try to remove it)

Do you know which elementary repository you used?
Perhaps you can run ppa-purge and revert all packages back to the Ubuntu default settings.

---

### Post by chancuu on 2018-01-17
heres the out put

heres the out put
~$ cat /var/log/installer/media-info
Ubuntu 16.04 LTS "Xenial Xerus" - Release amd64 (20160420.1)

and i think i just used the offical repository for elementary, but i did remove all the ppas i found on the list by just going settings and then software and updates. all the ppas on there are all ubuntu xenial, and then one trusty tahr, that i added to run something i dont quite remeber. i think i added the trusty one for my runescape client to work right

---

### Post by chancuu on 2018-01-17
heres the out put

heres the out put
~$ cat /var/log/installer/media-info
Ubuntu 16.04 LTS "Xenial Xerus" - Release amd64 (20160420.1)

and i think i just used the offical repository for elementary, but i did remove all the ppas i found on the list by just going settings and then software and updates. all the ppas on there are all ubuntu xenial, and then one trusty tahr, that i added to run something i dont quite remeber. i think i added the trusty one for my runescape client to work right

---

### Post by deadflowr on 2018-01-17
Thjis seems to be the one, correct?
[https://launchpad.net/~elementary-os/+archive/ubuntu/os-patches?field.series_filter=xenial]("https://launchpad.net/~elementary-os/+archive/ubuntu/os-patches?field.series_filter=xenial")
If so, I would re-add it again and run the update command,

But
instead of running any upgrade commands install the package ppa-purge
```
sudo apt install ppa-purge
```
then run the ppa-purge command
like so (all together now)
```
sudo add-apt-repository ppa:elementary-os/os-patches
sudo apt-get update
sudo apt install ppa-purge
sudo ppa-purge ppa:elementary-os/os-patches
```
that should revert the packages and then it will disable the ppa.

Hope it helps

---

### Post by chancuu on 2018-01-17
i'll try it out real quick. will let you know the outcome

---

### Post by chancuu on 2018-01-17
heres the outcome of it

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial

thank you for the help! even though it wasn't a big deal, it was just a small detail that bugged me. but that seemed to do the trick for me. once again, thanks to everyone for their help. i'll try and not get in over my head anymore haha. but this was all a great learning experience, i at least know a little more than when i started :)

---

