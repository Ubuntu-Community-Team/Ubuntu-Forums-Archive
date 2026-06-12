---
title: "Beryl for Ububtu Edgy VMware image on Windows XP"
date: 2006-12-05
forum: General Help
---

### Post by pak33m on 2006-12-05
Hello,

Can Beryl run on an Ubuntu Edgy VMware image on Windows XP? If so, how do I go about doing it? I cannot find info about this in the forums or elsewhere.

So far I've installed Beryl on the Ubuntu Edgy VMware image, per the instructions here:

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

I believe that I am not configuring my xorg.conf correctly for the correct driver.  The driver is currently set to "vmware", but changing it has produced poor results and/or the Ubuntu Edgy VMware image not to finish loading.

Has anybody had an experience with the same?

---

### Post by Shatrat on 2006-12-05
I doubt it, Beryl needs to be hardware accelerated and VMware doesnt do that afaik.

---

### Post by beerorkid on 2006-12-05
I do not think 3D or graphics acceleration works in vmware.  I know you can do some stuff to get around it.  but I think you might be out of luck.

---

### Post by pak33m on 2006-12-05
WOW! The replies come in with the quickness.  That is why I love this community.  I know that sounds cliche considering that is one of the main reasons for Ubuntu being the well-oiled machine that it is.  

Thank you very much for you quick replies.  And to think, I'm just trying to install Beryl for the heck of it here...

I will watch for other replies and maybe there is a way to accomplish what I am after.

Thanks again.  In my noobiness I will try to offer the same for our community.

---

### Post by beerorkid on 2006-12-05
from here: [http://www.vmware.com/community/thread.jspa?messageID=477606&#477606](http://www.vmware.com/community/thread.jspa?messageID=477606&#477606)

> If you want to interact with the VM and play games, Player will most likely be your better bet of the two, as the graphics code is more optimized. I asked because you posted this question in the Server forum, but then talked about Player.

Player and server do not play nicely together (can/t have both installed AFAIK)

I remember while messing with workstation there was a hack you could do to get accelerated graphics working.  but, I think it was for windows only on a linux version of workstation.  I created a few VM's with workstation but now use them in player.

After searching through the forums it does not look like it is possible in server.  Which vmware product are you using?

---

### Post by pak33m on 2006-12-05
beerorkid,

I am using the following:

Product: VMware Server Console
Version: 1.0.1 build-29996

I am running VMware Server at work with several or more images for testing our software and I wanted to get Beryl working on the Ubuntu Edgy image just to get it working.  It won't work on the Fedora Core 6 image either even in the provided Beryl install.  This is why I assumed it was the driver in my xorg.conf.

It is no biggie if Beryl does not work in VMware Server.  I just like to give it a good hack!

Thanks again.

---

### Post by pak33m on 2006-12-05
> **beerorkid said:**
> from here: [http://www.vmware.com/community/thread.jspa?messageID=477606&#477606](http://www.vmware.com/community/thread.jspa?messageID=477606&#477606)



Player and server do not play nicely together (can/t have both installed AFAIK)

I remember while messing with workstation there was a hack you could do to get accelerated graphics working.  but, I think it was for windows only on a linux version of workstation.  I created a few VM's with workstation but now use them in player.

After searching through the forums it does not look like it is possible in server.  

I checked the link that you posted and it makes since the VMware Server would not have accelertaed graphics, well, because it is for server applications!

---

### Post by beerorkid on 2006-12-05
yup.  i think that is why workstation is the one that can be hacked since it is more of an user environment.  bummer it costs $ though.

We use all sorts of vmware products here at work.  i administor a couple ESX VI3 servers with 30 or so VM's.  It is quite fun.  I use server for a XP vm so I can have my workstation be ubuntu (with beryl of course).  I am going to install edgy here sometime this week, and I will just use player for now on.  I have created enough XP VM's for personal use.

It would be nice to be able to show off beryl in a Vm though.  making people drool is fun ;)

---

### Post by pak33m on 2006-12-05
I have asked for Ubuntu to be my desktop at work, to no avail.  The Ubuntu Edgy image that I installed is for me to play while not on my laptop (Dapper) or home PC (Edgy).

I was considering installing Beryl on the Ubuntu Dapper Virtual PC image for the folks in my Cisco Academy program to drool over.  That may shake them from "Vista" buzz that they have going on at the moment!

Nice talking with you beerorkid.

---

### Post by msgyrd on 2006-12-10
If you just want to see the Beryl effects on your computer, check out [http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)  It's a livecd based on Gentoo, and includes the nonfree graphics drivers, beryl and aiglx or xgl.  I've not personally tried it, but as far as I know, it's the only way to test beryl without installing linux.

---

