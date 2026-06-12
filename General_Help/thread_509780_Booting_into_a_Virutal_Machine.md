---
title: "Booting into a Virutal Machine?"
date: 2007-07-25
forum: General Help
---

### Post by TrompeLaMort on 2007-07-25
Hi,

Is there any way to have a windows installation run inside a virtual machine, so that I could run it inside Linux, but when needed, boot into Windows to get all the performance without the overhead?

It seems like most virtual machines require a file to put the entire Windows filesystem into, which does not seem like it could be booted off of.

I guess I'm looking for the equivalent of parallels for Linux?

Thanks in advance!

Dan

---

### Post by x86fix on 2007-07-25
[http://www.vmware.com/download/](http://www.vmware.com/download/)

I have not done this in Linux but I am sure it will work.  They have a tool that will convert your existing Windows installation if you would like to use it.  The server is free.  There is also a Workstation product that has a free 30 day trial.  You can use it to create your own virtual pc and then load the software to it.
MS has VM for windows but everything I have read points out that this is better.  

I am a bit new to using Virtual and it is a learning process but it works well enough that major corps use it for their data centers.

I tried installing a Vista image on a linux distro a few months ago.  The distro was not installing as I wanted and I tossed it aside and never went back to it.  I think I am going to try again on an Ubuntu desktop install.  

If you want the details -Last time I was using the server and the Linux Terminal Server.  I was wanting to install Vmware server on the linux box and then put a Windows image and then login from multiple Linux or Windows boxes (could even be dumb terminals that boot from flopppy, Cd or Network).  I couldnt get the LTS installed and I had other things to get done so I dropped it.  I am a bit inspired right now and I converted my XP system to Virtual the other night- took about an hour.  I tried it in Vista and it works slowly.  I didnt expect to get a very good host job from Vista but I would expect that to change soon. I think I will install ubuntu on a couple computers , my old dell c-600 laptop and my Intel Core Due 2.4GHZ 3 GB Ram desktop- and try running vmaware server under linux.  Then I just have to start the server with my VM that I already have.

I have also downloaded appliances from the VM library.  They are just other peoples VM files.  It is all very coll since you can run multiple OS's in the VM server program at the same time.

---

