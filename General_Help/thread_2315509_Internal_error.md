---
title: "Internal error"
date: 2016-02-29
forum: General Help
---

### Post by Stefan_Lauritsen on 2016-02-29
Hi

I've been getting this error since an update: 
ubuntu internal error package linux image 3.19.0-51-generic 

This results in my computers inability to connect to the network trough wifi.
The ubuntu computer uses a Netgear A6100 dongle.

I've tried to manually clean, make, install and modprobe the driver, but it doesn't work.


The first problem was when I tried to do modprobe after a update, but it resulted in a "Exec format error" 
This is the code I run when this problem shows: sudo modprobe 8812au

I found someone who had tried to do:

sudo modprobe -r 8812au
sudo insmod 8812au.ko

And that worked.. a while...

It's after this I had the problem with the package package linux image 3.19.0-51-generic.

Yesterday I found someone who did:

sudo touch /var/lib/dpkg/lock
sudo rm /var/lib/dpkg/lock
sudo touch /var/lib/dpkg/lock
sudo dpkg --configure -a
sudo apt-get clean

And that worked.
Today another update came, and none of these temporary fixes are working.
I was hoping a update would come and fix this automatically, but I guess I have to find a permanent fix myself.

So any ideas?

PS: I'm using this computer as a home server. File server, media server etc.
I know there are probably better distros for server use, I tried debian and cent, I believe, but I had problems installing cent, and debian was just too hard for me without a GUI.

---

