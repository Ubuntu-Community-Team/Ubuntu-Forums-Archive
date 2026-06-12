---
title: "My repo problem"
date: 2007-10-22
forum: General Help
---

### Post by sdil on 2007-10-22
Hello... is anybody can help me with my repo .... I can't install any software now.

 After upgrade from ubuntu feisty fawn to gutsy gibbon, i can't install any software meanwhile i can use internet comfortably.

 I hope anyone can copy your /etc/apt/sources.list to this forum ... i hope your help .... please ...

---

### Post by forestpixie on 2007-10-22
You can get a source list from [here]("http://www.ubuntu-nl.org/source-o-matic/") if that helps

---

### Post by Partyboi2 on 2007-10-22
Here is a copy of my /etc/apt/source.list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by sdil on 2007-10-22
> **Partyboi2 said:**
> Here is a copy of my /etc/apt/source.list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```


i think, there is something wrong with it ... i think the server is damage ( maybe ) or something strange with my internet or ubuntu ... during download the ubuntu 7.10 alternate installation version, i chose German version ( maybe, i forget, but it's europe )

any idea to solve my problem ?

---

### Post by forestpixie on 2007-10-22
what problems do you actually get when you try to install - what happens with an apt-get update?

---

### Post by sdil on 2007-10-22
it show :

razi@ubuntu:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg                             
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Translation-en_US                  
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Translation-en_US            
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Translation-en_US              
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
razi@ubuntu:~$

---

### Post by forestpixie on 2007-10-22
try changing the server in software sources - and did you not have a sources.list in the first place?

---

### Post by sdil on 2007-10-22
it show this :

W: Failed to fetch [http://ubuntu.csie.nctu.edu.tw/ubuntu/pool/universe/c/compizconfig-python/python-compizconfig_0.5.2+git20070912-0ubuntu1_i386.deb](http://ubuntu.csie.nctu.edu.tw/ubuntu/pool/universe/c/compizconfig-python/python-compizconfig_0.5.2+git20070912-0ubuntu1_i386.deb)
  Could not connect to ubuntu.csie.nctu.edu.tw:80 (1.0.0.0), connection timed out

When i installing Advance Dekstop Effect using Add / Remove Application ...

any other idea ?

---

### Post by forestpixie on 2007-10-22
clicking the link in your post worked for me?

I guess you're still getting the problem - what does you're sources.list look like or did you just copy partyboi2 post

did you try changing the server or not

---

### Post by sdil on 2007-10-23
i copy portboy's repo .... and then change the server because doesn't work ... i am tried server from Taiwan ( Best Server ), Australia and America but ... it's still does't work ... :-(

Any other ideas ?

---

### Post by sdil on 2007-10-24
anyone ? please ........

---

### Post by forestpixie on 2007-10-24
all I could suggest would be redoing you're sources.list with the link I gave earlier. If you're connecting to the net ok and it's just apt which doesn't ssem to work I can't think of anything else myself.

Never had to sort a connection problem out - you could have a search of the forums for similar - or google.

---

### Post by sdil on 2007-10-24
> **forestpixie said:**
> all I could suggest would be redoing you're sources.list with the link I gave earlier. If you're connecting to the net ok and it's just apt which doesn't ssem to work I can't think of anything else myself.

Never had to sort a connection problem out - you could have a search of the forums for similar - or google.


I use it ... still doesn't work ... I used the Taiwan server ( Best Server ) ....

---

### Post by forestpixie on 2007-10-24
sorry then - it's beyond me :(

---

### Post by sdil on 2007-10-24
what do you mean ?

---

### Post by Scareface on 2007-10-24
Hi
And how it is with other programs, that are using internet. I mean Evolution, Pidgin. Because I have maybe similiar problem like you. I can only to browse internet pages in firefox.

---

### Post by forestpixie on 2007-10-24
> **sdil said:**
> what do you mean ?

I mean I can't help :(

---

### Post by sdil on 2007-10-25
maybe i need to re-install ubuntu on my computer or buy new PC :-(

---

### Post by forestpixie on 2007-10-25
I have been looking on the forums to see if I can find anything that might help you but I'm not getting very far. The only thing I did see was someone having problems with repos using a proxy - or at least I think that was the problem - it was late.

Perhaps you're right - a reinstall could fix it, I wouldn't go so far as to buy a pc though. I'm sure it's really frustrating - wish I could be more help.

Maybe a clean install of gutsy will do the trick.

---

### Post by mike.x on 2007-10-29
I am getting the same problem, DNS is not working for Synaptic.  Initally it was not working for Firefox either until I made another recommended change (alias net-pf-10 off in /etc/modprobe.d/aliases).

I am still investigating the problem with aptitude.

---

### Post by sdil on 2007-11-07
did you get the answer now ?

---

### Post by shurikr on 2007-11-13
I've just found the short-term solution!!!
Try to "ping" all the addresses written in your /etc/apt/sources.list

> ping ubuntu.com
> ping us.archive.ubuntu.com
> ping security.ubuntu.com

And then "apt-get update" should work for the short period of time. Unfortunately after a while some internal caches are cleaned and the problem persists.

---

