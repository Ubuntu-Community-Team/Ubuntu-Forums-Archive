---
title: "CLoneZilla v3.12.8 on 14.04 lts: Automatic boot countdown restarts cannot initiate"
date: 2016-04-07
forum: General Help
---

### Post by CrashAbbott on 2016-04-07
Brainiacs!  I need some help!
My Clonezilla machine on Ubuntu 14.04 had to be rebuilt.  I was successful in getting everything running, retrieving the backed up images and I went to test>>> FAIL!

My system is multihomed, with Eth1 going to the world and Eth2 going to a private range, on start up, the laptop to be imaged is found, the image title is correct in the DRBL fields and the Automatic boot counts down from 7.. HOWEVER,, it will NOT initiate, it cycles the countdown endlessly,, if I hit ENTER.. it restarts the countdown.. it will not initiate the cloning process,,
I have tried to send an image, and tried to make an image, I have used two separate machines to see if there was a hardware error.. the behaviour is the same on both

Would anyone have an idea as to WHY the system will not initiate?.. I have no errors on the CLoneZilla computer, everything is green and Success and OK.. it finds the computers to image but will not begin..

HELP?????

---

### Post by RobGoss on 2016-04-07
Hello and welcome, I use clonezilla  all the time I have never encounterd this problem

It might be a good idea to just download another ISO file and install it USD or CD, maybe that one you have some how got corrupted

---

### Post by CrashAbbott on 2016-04-07
Thank you Rob, greatly appreciate you taking a look.. I have "re-done" this machine a number or times..everything works but the initiation.. while typing this I just had a thought.,., on the second NIC, my scope may be limiting.. hmm.. will continue to look.. this has to be something silly I am overlooking or missed.. 

Cheers!
R

---

### Post by RobGoss on 2016-04-07
I use Clonezilla just for basic backups so I'm sure there are many options I've never even seen I know Clonezilla can alot. 

How are you booting Clonezilla from a USB or CD?

I don't ever remember seeing any countdown when I run Clonezilla.

---

### Post by CrashAbbott on 2016-04-07
I am actually using CZ on another computer (server) and storing the images for multiple deployment on that .. I do have a "backup" system that is slower,, that works, and have checked settings against it,, they are the same.. 

So I have a multihomed PC.. with a switch on the second NIC that uses the DHCP private scope.. from that I connect to the machines that I wish to take or deploy an image to.. 

everything works, until it comes time to initiate the CZ client connection on the peripheral computer.. at that point it just loops on the countdown.. does not begin the backup/deploy..

I just know this is something small.. the proverbial.. "needle"

cheers!

---

### Post by RobGoss on 2016-04-07
Have you try a new ISO install of Clonezilla it might be something wrong with your current one,  just a thought

---

### Post by CrashAbbott on 2016-04-07
I installed CZ via DRBL via Ubuntu.. I do not have an ISO of CZ?.. nor would I know how to install that on Ubuntu :(  

but it may be an avenue to pursue.. 

any directions?

thanks
R

---

### Post by RobGoss on 2016-04-07
It's pretty much the same method as you would do when burning a Ubuntu ISO file nothing different only thing is your using Clonezilla instead of Ubuntu

Here is a nice help guide that might make the process a bit easier 

Clonezilla Live Usb
[http://clonezilla.org/liveusb.php](http://clonezilla.org/liveusb.php)

---

### Post by CrashAbbott on 2016-04-07
Thanks Rob,, 
checking it out :)

---

