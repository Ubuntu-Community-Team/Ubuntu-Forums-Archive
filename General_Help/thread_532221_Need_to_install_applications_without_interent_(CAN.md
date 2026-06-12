---
title: "Need to install applications without interent (CANNOT HAVE INTERNET)"
date: 2007-08-22
forum: General Help
---

### Post by bone2006 on 2007-08-22
I've done some searching on this, but I can't find an answer.  I have a computer system that's in a secured place that cannot have internet access period.  So please don't post anything about getting my network card or internet to work, no internet will be on this computer or even the location the computer is at.   
So I need to install applications on this computer and I'm not sure what is the best way about going about it.  I'm on a windows machine now and would like an easy way or easiest way to install applications.  After searching for awhile it seems most people just talk about getting your internet or network working, which is useless to me.

Is there a CD that I could possible get that would have a lot of packages even if it's a few CDS?  Somebody said that debian has some extra cds, which this link didn't really help me or how to do it
[http://www.debian.org/CD/](http://www.debian.org/CD/)

Also this has been posted a few times [http://packages.ubuntu.com](http://packages.ubuntu.com) how would you download say VLC and it's 20 dependies on a windows machine, burn it to a CD and then is there a command that will install everything that's in a directory?

It's just that I'm going to probably have to take a lot of packages over and a lot of walking, but as I said internet is not even a consideration, there will not be internet on that system.

---

### Post by manimal on 2007-08-22
Can you connect an external (USB) drive?  If so, you cal always mirror the ubuntu repositories and put the files on the USB drive. 

[http://www.ubuntu.com/getubuntu/mirror]("http://www.ubuntu.com/getubuntu/mirror")

It would take a mighty long time to put all that on CD/DVD though.

---

### Post by logos34 on 2007-08-22
There IS the [ubuntu DVD]("http://www.ubuntu.com/getubuntu/downloadmirrors") (4GB worth of pkgs).  You could add that as a source in Synaptic.

There is also APTonCD, but you'd need to use  linux to install it, download the deb pkgs along with dependencies, then make a cd/dvd.  Maybe you could do that on Wubi inside your windows machine.

Wish I could be more help.

---

### Post by forestpixie on 2007-08-22
Have a look at this it might help - 

[http://wubdepends.sourceforge.net/](http://wubdepends.sourceforge.net/)

it says it does this 
> 
Wubdepends enables a user of an offline ubuntu computer to download packages and all their dependencies on another computer, to then be transferred to their ubuntu pc and installed without issue.

I have no idea if it's any good as such just saw it in a post yesterday and thought it might help someone and bookmarked it

---

### Post by rsambuca on 2007-08-22
Since you have the packages.ubuntu site, it is actually very easy to install programs this way.  Like you said, just go to any computer with web access and download the .deb files you need, including dependencies just in case you don't already have them.  Burn them to a cd, and go to your ubuntu pc.  Just double click on the .deb files and they will be installed onto your system.  You will have to install the dependencies first, and then the main package.  Sometimes you could have problems if you are missing a dependency of one of the dependencies!  Just write the name of the file down, and go download that one and install it first.

The deb packages will be automatically installed via a program in ubuntu called GDebi, and then they will also show up in your Synaptic package manger.

---

### Post by stchman on 2007-08-22
> **bone2006 said:**
> I've done some searching on this, but I can't find an answer.  I have a computer system that's in a secured place that cannot have internet access period.  So please don't post anything about getting my network card or internet to work, no internet will be on this computer or even the location the computer is at.   
So I need to install applications on this computer and I'm not sure what is the best way about going about it.  I'm on a windows machine now and would like an easy way or easiest way to install applications.  After searching for awhile it seems most people just talk about getting your internet or network working, which is useless to me.

Is there a CD that I could possible get that would have a lot of packages even if it's a few CDS?  Somebody said that debian has some extra cds, which this link didn't really help me or how to do it
[http://www.debian.org/CD/](http://www.debian.org/CD/)

Also this has been posted a few times [http://packages.ubuntu.com](http://packages.ubuntu.com) how would you download say VLC and it's 20 dependies on a windows machine, burn it to a CD and then is there a command that will install everything that's in a directory?

It's just that I'm going to probably have to take a lot of packages over and a lot of walking, but as I said internet is not even a consideration, there will not be internet on that system.

Go to another Ubuntu machine and go to Synaptic.  Select the packages you want.  Select the download only check box.

I believe that the .deb packages will be downloaded to /var/cache.  Copy those onto a CD and go to your island machine.

---

### Post by bone2006 on 2007-08-22
stchman this is the exact thing I did, except something like VLC there was too many dependencies and on the machine I had it was already installed.  It was a pain to find all 20 for instance.

I was looking at the link to setup the mirror and it is 170 GB, which isn't something I'm looking to download to be honest.

It looks like either [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) or a DVD seems to be my best option.  How can I tell what packages are included on the DVD?  I think I'll try out this aptoncd, which looks like it would do the job exactly.  I'm looking for about 10-20 applications to install and their dependencies, which would be nice to get on a CD and aptoncd looks really promising.

---

### Post by logos34 on 2007-08-22
> **bone2006 said:**
> How can I tell what packages are included on the DVD?

[http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/feisty/release/ubuntu-7.04-dvd-i386.list](http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/feisty/release/ubuntu-7.04-dvd-i386.list)

---

### Post by rsambuca on 2007-08-22
> **bone2006 said:**
> stchman this is the exact thing I did, except something like VLC there was too many dependencies and on the machine I had it was already installed.  It was a pain to find all 20 for instance.


On the ubuntu packages website, all of the dependencies are listed with links.

---

### Post by stchman on 2007-08-22
> **bone2006 said:**
> stchman this is the exact thing I did, except something like VLC there was too many dependencies and on the machine I had it was already installed.  It was a pain to find all 20 for instance.

I was looking at the link to setup the mirror and it is 170 GB, which isn't something I'm looking to download to be honest.

It looks like either [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) or a DVD seems to be my best option.  How can I tell what packages are included on the DVD?  I think I'll try out this aptoncd, which looks like it would do the job exactly.  I'm looking for about 10-20 applications to install and their dependencies, which would be nice to get on a CD and aptoncd looks really promising.

You don't have to find them.  You can hit properties in Synaptic and it will list all the dependencies.

---

### Post by bone2006 on 2007-08-23
hum...... I've always known that I can hit properties and see the dependencies, but how does this help if I'm taking it over to another system?  I still need to find them

I tried out the APTonCD, but it wasn't 100% what I was expecting.  It seems to just look in your archive folder and create a CD from that, which I did put a checkmark on dependences, but I'm not sure if all the dependences are in the archive folder or not.

I took a look at the DVD list and did a quick search for the words like wine, k3b, vlc and it came up with nothing, so the DVD isn't going to work.

---

### Post by rsambuca on 2007-08-23
> **bone2006 said:**
> hum...... I've always known that I can hit properties and see the dependencies, but how does this help if I'm taking it over to another system?  I still need to find them

Did you see my last post?  On the [http://packages.ubuntu.com](http://packages.ubuntu.com) site, all of a program's dependencies are indicated WITH LINKS!  Not too hard to find.

---

### Post by bone2006 on 2007-08-23
Yes, but if I do a search for something like VLC and I find the VLC package such as this
[http://packages.ubuntu.com/feisty/graphics/vlc](http://packages.ubuntu.com/feisty/graphics/vlc)

It has more dependencies than I care to download each, which would probably take half an hour or more.  I can download  vlc_0.8.6.release-0ubuntu4_i386.deb, but taking this over to a clean install system, won't it ask me for the dependences?

---

### Post by rsambuca on 2007-08-23
Yes you will need to install the dependencies first (which I indicated earlier in post #5).  I can't imagine it would ever take 30 minutes to download these files.  I installed VLC in less than a minute.

There are a bunch of dependencies for some programs.  That is life.  Frankly, as much as I hate to say it, if you don't have any internet connection, I wouldn't recommend ubuntu.

---

### Post by christhemonkey on 2007-08-23
I would re echo forestpixie's sentiment and say try out wubdepends.
Does exactly what you want.

Try it! Check out the link in my sig.

---

