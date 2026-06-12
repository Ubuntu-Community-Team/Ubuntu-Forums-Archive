---
title: "USB stick size for Live USB Op Systems?"
date: 2013-06-16
forum: General Help
---

### Post by TNFrank on 2013-06-16
I've read that 16GB is preferred as the size to run a Live Op System from a bootable USB drive. I have Ubuntu 12.04LTS on an 8GB stick and it seems to work fine and as a matter of fact I'm only using about 3GB total on my laptop hard drive right now running 12.04LTS so I wonder if an 8GB USB stick wouldn't be ok.  
 I feel that the 32GBKingston USB  that I have is way too much and the Sandisk 8GB has a much faster benchmark time then the 32GB, not sure if it's a matter of size or just that SanDisk runs faster then the Kingston.
 Anyway, having had some luck with Ubuntu 12.04LTS on the 8GB stick I wonder if I could run Kali Linux and PinguyOS on 8GB sticks as well or if 16GB would work better?   I've only got a 32 bit system which If I understand correctly will only access 2GB of RAM but running the OS on a USB might be a different story. 
Anyway, long story less long, are ya'll and can you comfortably run an OS on an 8GB USB stick or would 16GB be better and why? Thanks.

---

### Post by Cheesemill on 2013-06-16
You can use any size stick as long as it's big enough for the OS image. A 1GB stick will do for all of the Ubuntu variants, you'll need a 4GB stick for Kali as the OS image is about 2.5GB.

Obviously if you want to use persistence then you'll need to leave some room for the persistence file, how much is up to you.

---

### Post by C.S.Cameron on 2013-06-16
For a non persistent Live install, anything over 1GB is waisted.
For a Persistent install 4GB does a good job unless you are installing lots of apps and saving vacation photos.
8GB is not that bad for a Full install unless you are running stuff like Vbox.

---

### Post by TNFrank on 2013-06-16
That's great news because I'd really like to get the 8GB USB sticks instead of the 16GB because they're quite a bit cheaper and I could get more of em' to keep more Op Systems in storage and ready to boot. 
For my 8GB USB stick with Ubuntu 12.04 on it I set 2GB aside for persistence which should be plenty since, like I said, I'm only using about 3GB on my 60GB hard drive in my laptop now. 
 Maybe later, after I've learned more about Linux I can partition the 32GB stick that I have into 4, 8GB sections and put 4 different distros on it but that's still a little to advanced for me to do right now. 
 My one attempt failed even though I split the 32GB into two 16GB sections and loaded two different Linux Op Systems onto it successfully I had no way to pick way to pick which distro to boot to on start up so it simply went to the one distro without letting me make a choice. 
I'm sure the more I play around with Linux and the more I get comfortable with what can be done I'll get it figured out. 
  Having my ol' iMac die on me might have been somewhat of a blessing in disguise because it has totally renewed my interest in computers and learning more about them and Linux has been a God Send because there's so many free Op Systems to pick and choose from that it'll let me learn pretty much for free.

---

### Post by TNFrank on 2013-06-17
I found a multi boot program that runs under Linux that's all in French that I heard Darren Kitchens talk about on HAK5 but I couldn't get it to "see" the USB drive that was installed. I guess I could download WINE and use one of the Windows multi boot programs if worse comes to worse. I'd just really like to put 2 or 3 op systems on that 32GB USB so I'd have options from a single USB stick. Oh well, I'm sure I'll find a program that'll do it one way or the other.

---

### Post by TNFrank on 2013-06-17
This looks like a way to make up a multi boot USB using UNetbootin.
[http://tazbuntu.blogspot.com/2009/05/multibootin-with-unetbootin.html](http://tazbuntu.blogspot.com/2009/05/multibootin-with-unetbootin.html)
Still need to read through it a few times to get it squared away in my head since I'm still pretty new at this kind of stuff but it does look like it's pretty straight forward cut and paste kind of stuff.
I'd really love to use my 32GB USB for more then just a single distro.

Here's another option that might work ok.
[http://www.sarducd.it/multiboot-usb-builder.html](http://www.sarducd.it/multiboot-usb-builder.html)

---

### Post by TNFrank on 2013-06-17
Now this guy makes it look really easy:
[https://www.youtube.com/watch?v=MH-khdiXqYs](https://www.youtube.com/watch?v=MH-khdiXqYs)
I'm going to give this a try to make a multi boot USB using UNetbootin.

---

### Post by TNFrank on 2013-06-17
That guy makes it look so easy in the YouTube video,LOL  Tried it a couple times, can't really get it to work right. Guess I'll just wait for an English version of the French Multi-Boot software to hit the interweb. ;)

---

