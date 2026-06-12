---
title: "Truecrypt on Gutsy"
date: 2007-10-18
forum: General Help
---

### Post by mbgb14 on 2007-10-18
Does anyone have an appropriate .deb package that will make Truecrypt work on Gutsy? 

Right now it can't find the kernel module... 

> FATAL: Module truecrypt not found.
Failed to load TrueCrypt kernel module


I'd prefer to **NOT** change my kernel, or compile anything.

---

### Post by thirddeep on 2007-10-18
If you don't want to (re)compile anything, then you will have to wait a little for the people to update the packages.

Thd.

---

### Post by mbgb14 on 2007-10-18
Well, I did say *prefer*... but I suppose I could be persuaded to if there was  no other way. 

Thing is, I have no idea how to. I ran build.sh included with the Truecrypt source, and: 


```
mbrown@eris:~/Desktop/truecrypt-4.3a-source-code/Linux$ sudo ./build.sh 
Checking build requirements...
Linux kernel (2.6.22-14-generic) source directory [/usr/src/linux]: 
Error: /usr/src/linux does not exit
mbrown@eris:~/Desktop/truecrypt-4.3a-source-code/Linux$ sudo ./build.sh 
Checking build requirements...
Linux kernel (2.6.22-14-generic) source directory [/usr/src/linux]: /usr/src/linux-headers-2.6.22-14-generic
Error: Kernel source code is incomplete - /usr/src/linux-headers-2.6.22-14-generic/drivers/md/dm.h not found.
mbrown@eris:~/Desktop/truecrypt-4.3a-source-code/Linux$ 

```

I only have these two dirs there: 

/usr/src/linux-headers-2.6.22-14
/usr/src/linux-headers-2.6.22-14-generic

---

### Post by thirddeep on 2007-10-18
You don't have the kernel source installed.

I *think* it's just:
```
sodu atp-get install linux
```

But there will be others here who actually know more about ubuntu kernel install ...

Thd.

---

### Post by bodhi.zazen on 2007-10-18
You need the kernel headers ;

```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by mbgb14 on 2007-10-18
Believe it or not, that still doesn't work. 
Same error: 

Error: Kernel source code is incomplete

---

### Post by DazzaL on 2007-10-18
Hi,

I installed truecrypt a month ago and had the same issue..you will need the linux-source package as the linux-headers are incomplete for some reason.

---

### Post by cojoco on 2007-10-19
Believe it or not, that doesn't work either ...

$ sudo ./build.sh 
[sudo] password for ...:
Checking build requirements...
Error: Kernel source code is incomplete - /usr/src/linux/drivers/md/dm.h not found.

Boo-hoo!

---

### Post by Camino on 2007-10-19
try this

> 
sudo aptitude install dmsetup


If this is not working have a look in synaptic for **dmsetup**

Regards:popcorn:

---

### Post by cojoco on 2007-10-19
I followed the instructions in the truecrypt forums, here, which worked for me.
It took a while, though!

<http://forums.truecrypt.org/viewtopic.php?p=30145#30145>

---

### Post by mahousaru on 2007-10-19
Bleh I don't have an account on the TC forums so I don't know if I am repeating....

Ubuntu seems to download the Linux source as a tar file so u need to uncompress it and then symlink it to linux

I'm pretty new to ubuntu so please use this at your own risk, but it is what I have done and seems to work fine.

Check /usr/src and if you see just linux-source-2.6.22.tgz there you need to expand it with

sudo tar -zxvf ./linux-source-2.6.22.tgz

oh if the file is ends with bz2 then the flags are:

sudo tar -jxvf ./linux-source-2.6.22.bz2

then 

sudo ln -l linux-source-2.6.22 linux

Then you need to in the /usr/src directory: 

sudo make oldconfig

(This uses your current config to answer all the kernel questions)

then sudo make -C linux modules_prepare

For dependencies you need build-essential which installs a load of ****. 

You can now run in the tc/Linux directory and then:

./build 

sudo ./install

---

### Post by dayvy on 2007-10-19
You might want to give cryptkeeper a try. It is very similar to truecrypt and works like a charm in Gutsy.

[http://linux.softpedia.com/get/Desktop-Environment/Tools/Cryptkeeper-26924.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Cryptkeeper-26924.shtml)

Note: fuse is usually running as a module already once encfs is installed. Just make sure you are part of the fuse group.

---

### Post by mahousaru on 2007-10-19
Good thing about TC is that you can transport your encrypted data between Windows and Linux (although in terms of security opening your data on a MS box is asking for trouble :p)

---

### Post by der_joachim on 2007-10-20
> **cojoco said:**
> Believe it or not, that doesn't work either ...

$ sudo ./build.sh 
[sudo] password for ...:
Checking build requirements...
Error: Kernel source code is incomplete - /usr/src/linux/drivers/md/dm.h not found.

Boo-hoo!

Here's what I did. It works.
```

sudo -s
apt-get install linux-source
cd /usr/src
tar xvjf linux-source-2.6.22.tar.bz2
ln -s linux-source-2.6.22.tar.bz2 linux
cd *path/to/your/truecrypt/source/code*/Linux
./build.sh
./install.sh

```
Good luck. :)

---

### Post by rclark68137 on 2007-10-21
Gutsy 7.10 version of TrueCrypt is now available to download at [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

---

### Post by b20963a2 on 2007-10-21
Can't we request truecrypt to be included in the next release? One can find almost everything in the repo's nowadays, but not truecrypt.

Or is there a specific reason for ti not being included?

---

### Post by PacShady on 2007-11-10
Until the guys at Ubuntu decide whether to add TrueCrypt to the repositories, I've got it up on my own repository for Gutsy. Actually, so far it's the only thing ON my repository LOL, my own little project to collect orphaned debs for open source proggy's I use.

Just add *[COLOR="Red"]deb [http://download.tuxfamily.org/shadyrepo](http://download.tuxfamily.org/shadyrepo) gutsy main[/COLOR]* to the end of your sources.list and update!

'Shady

---

### Post by mbgb14 on 2007-11-10
Nice. You know the folks at Truecrypt updated their .deb for Gutsy and it now works flawlessly eh?

---

### Post by skralljt on 2008-01-19
I tried installing the new 7.10 deb that the truecrypt.org site offers, but I am getting the same error of the kernel module not loading in xubuntu.  When I rebooted and went into gnome all of a sudden it works.

---

