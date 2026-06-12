---
title: "Drive Space Allocation / Partitioning Advice Needed"
date: 2007-02-23
forum: General Help
---

### Post by Icarus3000 on 2007-02-23
I am building up a computer from scratch.  I want to dual boot XP and Ubuntu.  

I have a 40 GB hard drive.

I want to allocate 10 GB for Windows, and ~ 10 GB for my documents/videos/pictures (shared with ubuntu and windows)

That leaves me ~20 GB for ubuntu, but I am not sure how to best partition this remaining space.  I have heard that it is better to have a separate partition for /home.  So was planning to create three linux partitions:  

1) / 
2) /home
3) swap

But, being a bit of a linux newbie, I don't have a good feel for what is installed in / vs /home.  Between "/" and "/home", which typically needs more space?  Can someone give me a very general idea of which files are installed in each?  Where are the applications located, in "/" or "/home"?

If it will help the answer, I also intend to install crossover office in linux to allow me to run Photoshop and Microsoft Office.

Thanks,
Icarus

---

### Post by antoz on 2007-02-23
Check this site for info

[M:\Ubuntu Linux Resources.htm ]("M:\Ubuntu Linux Resources.htm")

---

### Post by markitect on 2007-02-23
your scheme is pretty similar to my laptop, but instead of giving 20G to Linux do something like
1) Windows 10G  (windows will kill your hard drive fast if you put many newer games on it, I sometimes wish it was larger)
2) Swap 1.5G
3) / 10G
4) the rest as /home and shared with windows with fs-driver for shared files and overflow.


The Linux applications will all go under /bin, /usr, and /opt, but they tend to take a fraction of the space windows apps do.  Most of your windows apps running on linux will install in your home directory

---

### Post by annda on 2007-02-23
having a separate partition for home is a good idea if you like to experiment and you expect you will break your ubuntu install but still want to keep custom settings.

otherwise i see no need for separate home (it might not be so good for new users because if your system is broken and you reinstall, some bad configurations will be usen on new install and confuse you more). i would rather recommend backing up your important data just in case. other than that, use an additional partition to store you documents, music, videos, etc. make it larger than 10GB. 

use circa 10GB for ubuntu (enough for system and a lot of programs), and partition the rest of your disk to be used as storage. you can always resize the partitions if you need to.

---

### Post by antoz on 2007-02-23
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

Sorry about the previous link, this should work

---

### Post by Icarus3000 on 2007-02-23
> **markitect said:**
> your scheme is pretty similar to my laptop, but instead of giving 20G to Linux do something like
1) Windows 10G  (windows will kill your hard drive fast if you put many newer games on it, I sometimes wish it was larger)
2) Swap 1.5G
3) / 10G
4) the rest as /home and shared with windows with fs-driver for shared files and overflow.


The Linux applications will all go under /bin, /usr, and /opt, but they tend to take a fraction of the space windows apps do.  Most of your windows apps running on linux will install in your home directory

This seems like the most efficient approach, also in line to the recommendations from:  [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning).

I have a few additional questions though:

1.  If I share an ext3 drive with windows with fs-driver, can I use that drive as the location for Windows "My Documents"?
2.  If I use VMWare to load my physical XP installation, will I be able to access the files from an ext3 drive?
3.  If I create a virtual XP installation using VMWare, will I be able to access the ext3 drive natively, or will I need to use the fs-driver in the virtual XP OS?

Many thanks,
Icarus3000

Edit:
An additional question:
4.  Which, if any, of the "/", "/home", and "swap" partitions need to be made primary partitions?

---

### Post by markitect on 2007-02-25
1.  You can move your my documents folders location wherever you want see: [http://support.microsoft.com/kb/310147](http://support.microsoft.com/kb/310147)
4.  Doesnt really matter if anything is extended or primary, as far as i know there is no difference except where the size info is stored.

Not sure about 2 or 3

---

### Post by Icarus3000 on 2007-02-26
> **markitect said:**
> 1.  You can move your my documents folders location wherever you want see: [http://support.microsoft.com/kb/310147](http://support.microsoft.com/kb/310147)
4.  Doesnt really matter if anything is extended or primary, as far as i know there is no difference except where the size info is stored.

Not sure about 2 or 3

Thanks! 

I will test it out and see how it works :)

---

