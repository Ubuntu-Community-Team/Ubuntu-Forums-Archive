---
title: "slow graphics"
date: 2008-06-10
forum: General Help
---

### Post by Gespenster on 2008-06-10
Hi, this weekend I've installed ubuntu for the first time. The version is Hardy Heron x86_64.

My PC specs are the following
Pentium D 3 GHz
2 GiB RAM
Asus P5WD2E main board
Asus Geforce 8800GT

I was really amazed by the low graphics performance. Scrolling in firefox is very sturdy, when I move windows over each other they produce a lag effect, windows restore very slowly after being minimized, etc. It's a bit like using windows with 2D graphics acceleration disabled.

The first thing i figured was to download and install the latest nvidia drivers. After a lot of trouble (the installer needed to compile a kernel module and it said it did but actually it didn't because I lacked some libraries) I managed to install version 173.14.05.

Those new drivers did not help.

Then I've uninstalled everything related to compiz figuring this was maybe the performance killer, but that didn't help either.

I'm out of ideas and this bad performance is killing me. Which files can I post that can help analyzing this problem?

---

### Post by raozuzu on 2008-06-10
I think we have the same or the same part of the problem :P I posted it just 2 minutes ago

---

### Post by Gespenster on 2008-06-10
> **raozuzu said:**
> I think we have the same or the same part of the problem :P I posted it just 2 minutes ago

I've just read your post and I think it's a different problem. Overall my system is very fast: boot up time is good, programs start really fast, firefox starts even considerably faster than in windows, ...

It's just the "drawing" of graphics components that is really sluggish.

---

### Post by redonwhite on 2008-06-10
Hello,  Go to "System", "Administration", "Hardware Drivers"  And see if theres a driver there installed and if so.  Make sure its enabled.

---

### Post by robinc on 2008-06-10
install envy..

---

### Post by Gespenster on 2008-06-10
> **redonwhite said:**
> Hello,  Go to "System", "Administration", "Hardware Drivers"  And see if theres a driver there installed and if so.  Make sure its enabled.

It shows an empty list, there's nothing to enable.

I've also tried this [old fix]("http://ubuntuforums.org/showpost.php?p=4412617&postcount=1") and the scrolling in firefox is improved but I still have the problem. 

Especially nautilus restores very slowly from minimization.

edit: I've tried envy but that tried to install another nvidia driver. That failed however because the other nvidia driver is not compatible with the kernel module i've compiled for the driver I've installed.

---

