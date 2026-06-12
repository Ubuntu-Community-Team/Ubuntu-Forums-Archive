---
title: "Problem installing variety"
date: 2017-08-12
forum: General Help
---

### Post by christon74 on 2017-08-12
Good morning fellow ubuntersO:)_ Variety has disappeared! Yesterday, I uninstalled "Phatch" and "ImageMagic", simply because I do not need them. Perhaps I have inadvertently uninstalled variety packages in the process? But I do not see how any software could be attached to another. A few minutes ago, I tried re-installing variety and here is what I get on the terminal display:

```
christophe@hp1:~$ sudo su
 [sudo] password for christophe:  
 root@hp1:/home/christophe# sudo add-apt-repository ppa:peterlevi/ppa
  Contains packages for the Variety wallpaper changer
 [http://launchpad.net/variety](http://launchpad.net/variety)
  More info: [https://launchpad.net/~peterlevi/+archive/ubuntu/ppa](https://launchpad.net/~peterlevi/+archive/ubuntu/ppa)
 Press [ENTER] to continue or ctrl-c to cancel adding it
 
 
 gpg: keyring `/tmp/tmp18e4qy26/secring.gpg' created
 gpg: keyring `/tmp/tmp18e4qy26/pubring.gpg' created
 gpg: requesting key A546BE4F from hkp server keyserver.ubuntu.com
 gpg: /tmp/tmp18e4qy26/trustdb.gpg: trustdb created
 gpg: key A546BE4F: public key "Launchpad PPA for Peter Levi" imported
 gpg: Total number processed: 1
 gpg:               imported: 1  (RSA: 1)
 OK
 root@hp1:/home/christophe# sudo apt-get update
 Get:1 [http://ppa.launchpad.net/peterlevi/ppa/ubuntu](http://ppa.launchpad.net/peterlevi/ppa/ubuntu) xenial InRelease [17.5 kB]
 Ign:2 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease
 Hit:3 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release
 Get:4 [http://ppa.launchpad.net/peterlevi/ppa/ubuntu](http://ppa.launchpad.net/peterlevi/ppa/ubuntu) xenial/main i386 Packages [848 B]
 Get:5 [http://ppa.launchpad.net/peterlevi/ppa/ubuntu](http://ppa.launchpad.net/peterlevi/ppa/ubuntu) xenial/main Translation-en [548 B]
 Fetched 18.9 kB in 0s (24.4 kB/s)                                  
 Reading package lists... Done
 root@hp1:/home/christophe# sudo apt-get install variety
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Some packages could not be installed. This may mean that you have
 requested an impossible situation or if you are using the unstable
 distribution that some required packages have not yet been created
 or been moved out of Incoming.
 The following information may help to resolve the situation:
 
 
 The following packages have unmet dependencies.
  variety : Depends: python-configobj but it is not installable
            Depends: python-pyexiv2 but it is not installable
            Depends: python-requests but it is not installable
            Depends: gir1.2-gexiv2-0.10 but it is not installable
            Depends: variety-slideshow but it is not going to be installed
            Depends: imagemagick but it is not installable
 E: Unable to correct problems, you have held broken packages.
 root@hp1:/home/christophe# 
```


I must say I  understand very little about repositories, and if they have been jumbled or muddled, I really have no idea how to fix this.
I sometimes get the message that "Ubuntu has encountered an internal error", but I hardly ever worry about this and I just  click "continue"

Anyway, thank you all in advance for help and advice.

Chris.

---

### Post by QIII on 2017-08-12
Hello!

Please enclose all terminal commands and their results in code tags.  This will make your posts easier to read and also preserve the formatting.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

Cheers!

---

### Post by vasa1 on 2017-08-12
And please don't use **sudo su** without really knowing what you want to do.```
christophe@hp1:~$ sudo su
```In your example, you certainly don't need **sudo su** just to install a ppa or most any software for that matter!

---

### Post by christon74 on 2017-08-14
OK. It seems that I will never fully acquire all the rules and etiquette relevant to posting to this forum. I have found out that Variety is indeed linked to Imagemagick which I have unfortunately uninstalled. Since I am no developer or programer/analyst, perhaps it is high time I hire the services of a psychic who will keep me from doing anything stupid in the future.
Good day to you Sirs.

---

### Post by christon74 on 2017-08-16
Solved! No kidding! I finally re-installed both Imagemagick and variety. Heavens, even dummies like me can successfully fix their problems!

---

