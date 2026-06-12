---
title: "ATI Radeon Xpress 200M and Ubuntu"
date: 2016-04-25
forum: General Help
---

### Post by dyosoft on 2016-04-25
I use my Ubuntu from portable HDD on 2 PCs, I have a problem with one of them that has "ATI Radeon Xpress 200M" GPU, I found a website claiming my GPU is fully supported but I don't think it's installed.


CS 1.6 on Wine has the picture all messed up, and one Linux FPS game (saube-something-something) doesn't run, it starts and closes without even showing black screen.


So I went on this forum to search for help...[and I did find something]("http://ubuntuforums.org/showthread.php?t=1654240"), but since that topic is closed I have to make this new one.


I'm now logged out on the Ubuntu and I'm on the terminal, did the 

```
sudo service gdm stop
sudo apt-get purge xserver-xorg-video-ati 
sudo apt-get install xorg-driver-fglrx
```


but it showed me a error on the last line:  "E: Unable to locate package xorg-driver-fglrx".
I'm still on the terminal, dunno if I have any graphic driver atm so I'll stay on it till I figure this out, can anyone help me? :)

PS: I dunno anything about Ubuntu...or anything Linux-related, I was Windows guy for more than 10 years

---

### Post by bapoumba on 2016-04-25
Moving this out of Multimedia Software to General Help.
The thread you linked to is in Multimedia, we did reorganize the forums structure last year and it was created in a forum originally not dedicated to software only. 
Free bump !

---

### Post by grahammechanical on 2016-04-25
It helps if you tell us what version of Ubuntu you are using. If you are using Ubuntu 16.04 then there are no AMD proprietary video drivers in Ubuntu 16.04. It is explained in the release notes.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Regards

---

### Post by yoshii on 2016-04-25
[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)
[http://fossbytes.com/ubuntu-16-04-features-linux-gamers-with-amd-radeon-no-fglrx-driver/](http://fossbytes.com/ubuntu-16-04-features-linux-gamers-with-amd-radeon-no-fglrx-driver/)

There are some other articles that describe this as well.  PCworld has a good article.  I can't find it at the moment though.  

AMD support for Linux is supposed to get better later on in the year (hopefully!).  

I have an AMD computer with a Radeon R7 series graphics unit, so I'm affected too.

---

### Post by QIII on 2016-04-25
Actually, AMD support for Linux is getting better right now.  This is a frustrating interlude before the revolution.

---

### Post by richardsdma on 2016-04-26
there is nothing you can do. the driver for your ati GPU is included in kernel. so, make a clean install and leave it as it is. 
i tell you this because i have almost the same gpu, ati radeon express x1270.

---

### Post by mörgæs on 2016-04-26
> **richardsdma said:**
> there is nothing you can do. the driver for your ati GPU is included in kernel. so, make a clean install and leave it as it is. 


Correct. Besides, the GPU is old and fine for standard computer use but for gaming I suggest something stronger.

---

