---
title: "VMWare and kernel headers"
date: 2007-12-13
forum: General Help
---

### Post by rustysail on 2007-12-13
Hey I'm trying to set up a vmware server, but I have run into a bit of an issue.  I have no kernel headers.  I tried apt-get them, but it doesn't work.

The oddest part is that I have kernel headers in /usr/src/ but they appear to be a new version than the one that I get when I do `uname -r` (2.6.20-16-generic).  Does this mean I have to upgrade my kernel? How do I do that?  

I'm not sure why I would be lacking kernel headers, but the ones I need are not even in the repositories so I am stuck.

---

### Post by fjgaude on 2007-12-13
Gosh, I've never had such a problem... I always simply install, update, even upgrade, and the kernel headers end up in the /boot directory, or wherever. I've never had to install any when installing VMware. Strange, maybe others have had the issues you face. Oh, maybe all you need do is install the build-essential group:

```
sudo apt-get install build-essential
```

That might do it.

---

### Post by rustysail on 2007-12-14
I already have build-essential, but I think I may have just found the issue because of what you said.  The VMWare installer was telling me to look in /usr/src/ but you say that I should be looking in /boot/.  Am I supposed to manipulate the files in /boot/?  There appear to be a few different files there so I'm not exaclty sure what I am supposed to do with them.  VMWare was complaining that it could not get a version.h file and I don't exaclty see on in /boot/ anywhere.  I can't try it out right now, but I will make a few attempts later.

Thanks a lot for the help.

---

### Post by fjgaude on 2007-12-14
Sorry, I misspoke about the /boot... lapse in memory... I can't suggest anything to do with your problem. I never had this issue with three or four installs of VMware and many installs of Ubuntu. Maybe someone else here has a solution.

I see that my headers are in /usr/src just as they should be.

---

### Post by rustysail on 2007-12-14
In that case, I think that it might help to upgrade my kernel.  That will allow me to find the correct kernel headers I believe.  Do you know where I can find a good tutorial on how to do that?  I just need a nudge in the right direction.

---

### Post by fjgaude on 2007-12-14
You might consider just doing an upgrade of your system... all your data and programs would remain. 

If you are up to it here it is, to compile kernels:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

If you are using Feisty, 7.04, it would be easy to upgrade through the repos, but I guess you have in the past only updated your kernel. Is that the case?

---

### Post by rustysail on 2007-12-14
nah I already used the updater so I'm running gutsy.  I never bothered to update my kernels though.  I suppose thats not good for the system, but I don't know how yet.

---

### Post by fjgaude on 2007-12-15
Try upgrade using apt-get. That might work, because the newest kernel is in the repository. Use man to see what apt-get can do.

---

### Post by djsroknrol on 2007-12-15
I've found that VMware will not compile with the 2.6.22-16 kernel and the kernel-headers are not in Synaptic for Gutsy...it functions just fine and installs without a hitch with the 2.16.22.14 kernel. I had to fallback to get mine installed.

---

### Post by ninja_unmatched on 2008-04-12
> **rustysail said:**
> Hey I'm trying to set up a vmware server, but I have run into a bit of an issue.  I have no kernel headers.  I tried apt-get them, but it doesn't work.

The oddest part is that I have kernel headers in /usr/src/ but they appear to be a new version than the one that I get when I do `uname -r` (2.6.20-16-generic).  Does this mean I have to upgrade my kernel? How do I do that?  

I'm not sure why I would be lacking kernel headers, but the ones I need are not even in the repositories so I am stuck.


I am new just jumping in on this thread but I have gotten i to work through a longer process.  I started off installing 7.10 gutsy then installing stuff including VMware server 2.0 then updated after and it stilled worked.

---

### Post by ninja_unmatched on 2008-04-12
As I read some of the threads I see this fact has been made known.  The kernel being used is the .14 kernel.  But I am sure adding repositories is a temp issue.  I will look into this...

---

