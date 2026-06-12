---
title: "[SOLVED] How Do I install Iftop package?"
date: 2008-01-27
forum: General Help
---

### Post by Gillette on 2008-01-27
I downloaded the iftop package to my desktop (iftop_0.17.orig.tar.gz
I extracted it (iftop-0.17)
I opened a terminal and typed: sudo apt-get install iftop
Terminal said:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package iftop.017

Where do I put the package so it can be found?

---

### Post by ThrobbingBrain66 on 2008-01-27
If you're using Gutsy, 'sudo apt-get install iftop' will install iftop from the repositories (assuming you have universe enabled).  If you're running anything before Gutsy, you'll have to compile iftop on your own (with the .tar.gz file you have).  To do that, read the following link:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Gillette on 2008-01-27
> **ThrobbingBrain66 said:**
> If you're using Gutsy, 'sudo apt-get install iftop' will install iftop from the repositories (assuming you have universe enabled).  If you're running anything before Gutsy, you'll have to compile iftop on your own (with the .tar.gz file you have).  To do that, read the following link:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Is Gutsy a version of Ubuntu? I'm using Ubuntu 7.10. I just started using it in December.

I don't know about Universe. I'm still learning the basics of Ubuntu. I'll see if I can figure out if universe is enabled.

---

### Post by Gillette on 2008-01-27
I've done a bit of research and yes I'm using Gutsy. I poked around in Ubuntu and discovered Universe was not enabled. So I have enabled it. I haven't retried the install yet. So do I need to download iftop again before I try and install it?

---

### Post by ThrobbingBrain66 on 2008-01-27
Yes, Gutsy Gibbon is the code name for Ubuntu 7.10.

Always make sure to check the repositories first for a package you want to install.  Chances are it'll be there.  If for some reason it's not, then you'll have to download the source code from the website (the .tar.gz file you had) and compile the program yourself.

Package installation from the repositories can be done using Synaptic or the command line.

To install from the command line, copy and paste the following into a terminal:
```
sudo apt-get install iftop
```

To install graphically, go to System > Administration > Synaptic Package Manager
and search for iftop.  Right-click the package and choose 'Mark for installation'.  Finally, click the Apply button.

---

### Post by Gillette on 2008-01-29
Thanks for the help I got it installed. I had lots of updating downloads to do first.

---

