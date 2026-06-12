---
title: "Synaptic MD5Sum failure"
date: 2005-07-11
forum: General Help
---

### Post by Nylira on 2005-07-11
Hi there. I am fairly new at linux and since I had no idea where else to post it I guess I will drop it in the other forum. :)

I am trying to compile something for which I need libpng. Now via Synaptic I am getting libpng12-dev. All nice and good. But when I try to install this I get the following:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb)
  MD5Sum mismatch

This of course is not good. However I have no idea to whom to report this or how to fix this. So I guess my questions are:
a. how can I fix this / get this fixed or
b. how can I circumvent this

Any help that can be given is appreciated.
Thanks

---

### Post by ChodeNode on 2005-07-11
[QUOTE=Nylira]Hi there. I am fairly new at linux and since I had no idea where else to post it I guess I will drop it in the other forum. :)

I am trying to compile something for which I need libpng. Now via Synaptic I am getting libpng12-dev. All nice and good. But when I try to install this I get the following:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb)
  MD5Sum mismatch

This of course is not good. However I have no idea to whom to report this or how to fix this. So I guess my questions are:
a. how can I fix this / get this fixed or
b. how can I circumvent this

Any help that can be given is appreciated.
Thanks[/QUOTE]
 I thought I read somewhere that those repositories were having problems. I ran into this but with other apps.

The thread that I had read said to edit your /etc/apt/sources.list file and remove the "us" part of your repository addresses. It seemed to work for me.

So just [http://archive.ubuntu.com](http://archive.ubuntu.com) instead of [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)

Hope that helps you.

---

### Post by cobelloy on 2005-07-11
just in case you are as much of a noob as me:

1) as root, open /etc/apt/sources.list (if you don't know how - scroll to the end)

2) save as sources.bak

3) delete it all and paste in everything between the lines (not the lines though):
-----------------------------------------------------------------------------------------------------------------------------
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted  

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary-updates main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe  
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 

# deb [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sarge main 
# deb-src [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sarge main 
-----------------------------------------------------------------------------------------------------------------------------

4) then save as sources.list

then try again, I have been using synaptic and apt-get with no trouble today, and remember you have your original list saved as /etc/apt/sources.bak

** if you don't know how to open it as root try this:

$ sudo gedit /etc/apt/sources.list

then enter your password when prompted

---

### Post by Nylira on 2005-07-12
Hi and thanks for the feedback. I editted the sources.list and changed them as suggested to the gb archive. But this seemingly doesnt produce much luck with regards to the updates.

When I start Synaptic after I changing sources.list I get the following message:
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)

However after I went into the Repository editting option in Synaptic and had it changed there again and had the system save it and reload it. That did work. So I am guessing I made an error somewhere while editting. 

I must admit I did not use gedit since I prefer joe as standard editor instead :)
But problem is fixed now.  Thanks

---

