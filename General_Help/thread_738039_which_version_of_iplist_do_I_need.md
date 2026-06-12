---
title: "which version of iplist do I need"
date: 2008-03-28
forum: General Help
---

### Post by Despot Despondency on 2008-03-28
I am going to install iplists onto my computer, but I don't which version to download from sourceForge. Here's the list of options

 	iplist_0.19-0etch1_amd64.deb 
  	iplist_0.19-0etch1_i386.deb
  	iplist-0.19-0.fc7.i386.rpm
 	iplist-0.19-0.fc7.src.rpm
  	iplist-0.19-0.fc8.i386.rpm
	iplist-0.19-0.fc8.src.rpm
  	iplist_0.19-0feisty1_amd64.deb
  	iplist_0.19-0feisty1_i386.deb
  	iplist_0.19-0gutsy1_amd64.deb
	iplist_0.19-0gutsy1_i386.deb
  	iplist_0.19-0hardy1_amd64.deb
	iplist_0.19-0hardy2_i386.deb
	iplist_0.19-0lenny1_amd64.deb
  	iplist_0.19-0lenny1_i386.deb
  	iplist-0.19.tar.gz  

I've got an AMD athlon 64 processor, so I need an amd64 version, but I don't know which amd64 version to get. What do these names like lenny and gutsy mean? Which version do I need? I've got ubuntu 7.10 on my computer btw.

---

### Post by WearZeeP on 2008-03-28
You will then need this one:

iplist_0.19-0**gutsy**1_amd64.deb


**_Gutsy_** is just another name for Ubuntu 7.10

Hardy means Ubuntu 8.04 (currently under development), Feisty means Ubuntu 7.04, Lenny and etch are Debian versions, fc7 and fc8 I think means Fedora 7 and 8.
Then the last one is just a tarball, which usually means its a compressed archive containing the source code which you can compile yourself.

---

### Post by Despot Despondency on 2008-03-28
That's really helpful. Thanks.

---

### Post by Despot Despondency on 2008-03-28
I've just tried installing the iplist_0.19-0hardy1_amd64.deb version with the gebi-gtk GUI and I get the error

Error: Wrong architecture 'amd64'

I'm confused. I've have amd64 processor. Any ideas?

---

### Post by WearZeeP on 2008-03-28
Oh I'm really sorry!
I confused you there.
Hardy is the name for Ubuntu 8.04, the version that is currently being developed.

You should look for Gutsy, which is the name for Ubuntu 7.10.
Sorry about that.

And oh, did you install Ubuntu with the amd64 installer?
Because if you didn't, you should get the normal 32-bit version.

That is, 

iplist_0.19-0gutsy1_i386.deb

if you have an amd 64 processor but installed Ubuntu as 32 bit, or else,

iplist_0.19-0gutsy1_amd64.deb

if you actually did install Ubuntu as 64-bit.


Sorry again :)

---

### Post by Despot Despondency on 2008-03-28
Don't worry about it. Any comments are always welcome. I want to learn as much as I can, so the more the better. It seems to have worked anyway, thanks for that. Just need to get my lists going now.

---

