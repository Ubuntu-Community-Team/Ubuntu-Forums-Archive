---
title: "New Harddrive"
date: 2007-04-30
forum: General Help
---

### Post by Mike.83 on 2007-04-30
Hi there.

I got a new 320GB hard drive for my PC today, I installed it fine, setting it as the slave, and formatted it in windows.  Then I thought "I have so much room, I could install a duel boot with linux"  Having used ubuntu Live CD's in the past, and enjoying doing so, thats the version of linux for me.

Anyways, I've never actually installed it, I am assumeing if I put a partition on my new HD, say 15GB, I should be able to just run the live CD and install it on the 15GB parition from there?

---

### Post by psusi on 2007-04-30
Yep.

---

### Post by Mike.83 on 2007-04-30
Swanky.  I'll give it a go then :D

---

### Post by SendDerek on 2007-04-30
I'm not sure about the entire setup, but I do know that it may be a good idea to create 2 partitions for linux from windows:

1GB - SWAP - swap
14GB - ext3 - file system root "/"

And then optionally, you could make a home directory:
1GB - SWAP - swap
5GB - ext3 - file system root "/"
9GB - ext3 - home

Sorry I can't be more detailed, but these are the basic steps I take when dual-booting.

---

### Post by Mike.83 on 2007-04-30
Ah right.  When making the paritions in windows, do I format them, or leave them?

Edit:  Ignore that, all became clear when I booted up Partition Magic. :)

Thanks for the help.

---

