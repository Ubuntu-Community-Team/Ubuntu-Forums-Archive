---
title: "Rsyncing 2 or more home computers"
date: 2014-02-03
forum: General Help
---

### Post by CrzPW74 on 2014-02-03
I finally am able to access all my laptops :)  thanx to openssh and server and this article
[http://www.maketecheasier.com/setting-up-a-home-network-](http://www.maketecheasier.com/setting-up-a-home-network-)... (wanted to give appropriate credit)
Anyway now I want or hope to be able to sync the files on the 2 main laptops.
 Both Laptops have a copy of our entire Music, photos, folders, etc.  
We both use the folders and files and many times make changes, and it would be nice to keep them the same using rsync.
We can access these files from both laptops to both laptops ( hope that makes sense lol)
Is this possible and where do we read... 
Also we are using simple password login should we be using ssh keys ? I seen that mentined when trying to search this topic.
Running pinguy on one and minton the other both are Ubuntu 12.04
All help greatly appreciated

---

### Post by Dennis N on 2014-02-03
Ignore this suggestion if you want to play with a network, but you can get the same result using rsync and a flash drive. Using a network you need both machines in range of each other, and also up and running to do any syncing (For me, they usually are not). No passwords or SSH involved. Works for all regular files.

rsync c1 to flash drive
then, when it is possible and convenient:
rsync flash drive to c2

repeat the last step if you have a third computer c3.

---

### Post by CrzPW74 on 2014-02-03
Thanx for the reply, However I would need an 85 gig flash drive lol. I was doing that with a spare harddrive (usb) but it got to be to much. Again thanx for taking time to respond.

---

### Post by Dennis N on 2014-02-03
> **CrzPW74 said:**
> Thanx for the reply, However I would need an 85 gig flash drive lol. I was doing that with a spare harddrive (usb) but it got to be to much. Again thanx for taking time to respond.

In that case, you clearly need to use a network. My entire OS installation on this laptop is only 25gb (with only 60% used). 

Good luck with rsync.

---

### Post by Dennis N on 2014-02-03
Almost forgot: Looking back at your questions:

> Is this possible and where do we read...
Also we are using simple password login should we be using ssh keys ? I seen that mentined when trying to search this topic.
Running pinguy on one and minton the other both are Ubuntu 12.04

Yes it is possible. rsync works in one direction at a time, so you would need to do it once in each direction. Or, there is a program called **unison** in the repositories that does both directions at the same time. You could try that out.

I have been using a password when needed, which is when I need to use SSH to access both computers simultaneously to work on them. If I had to rsync over my network rather than a USB flash drive, I probably would go to a key exchange.

Google "rsync tutorial" and you will find a huge amount of information on how it is all done over a network.

---

### Post by CrzPW74 on 2014-02-04
Thanx  I have indeed been googlin lol, some  articles are so old (2006 2008) it gets flustering lol. I did find one that used the command line but it was extremely detailed.. We are good for now as we can rsync the main laptop with the spare drive each week ( for a back up) but, I just want/hope to find some way fo syncing. As for unison I did try that some time ago I think I will revisit that one. Thanx again for your help...

---

