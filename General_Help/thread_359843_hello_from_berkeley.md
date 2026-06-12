---
title: "hello from berkeley"
date: 2007-02-12
forum: General Help
---

### Post by BuddhaBubba on 2007-02-12
hello, ):P
i'm pretty much new to linux and ubuntu and I wonder if I should learn linux to help out with my on-site computer consulting business.  yeah, my dell inspiron 9300 is in need of a HD wipe so I figured I could do a dual boot with Ubuntu and Windows XP...how hard is this?  (to give you a hint of my techie level - I know how to partition, basic networking (ex: most of my jobs are setting up home wireless networks), and fixing infected windows xp systems (ex: registry cleaning, virus squishing).  

anyway, i'm excited :)  about this because I think open-source and mass-collaboration is the future in all aspects of it's implementation (ex: wikipedia, linux, prosper.com, youtube, flickr)

anyway, thanks in advance

---

### Post by taurus on 2007-02-12
Maybe this guide helps.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by kebes on 2007-02-12
The hardest part of learning Linux is being willing to give it a try!

So if you're interested in putting in some effort to learn something new, I think you'll be quite happy with the results.


Dual-booting with Ubuntu and Windows is very straightforward nowadays. The Ubuntu installer can even resize Windows partitions for you. Since you said you've done partitioning before, this should be quite easy for you.

If you're reinstalling Windows, the easiest is to:
1. Partition the drive:
-NTFS partition for windows
-free space for Linux (as much as you want... I'd say at least 6Gb, more if you're serious about using it/installing software, etc.).

2. Install Windows to the NTFS partition.

3. Boot the Ubuntu LiveCD. Start the installer. Follow the steps.
Select "use free space for Ubuntu." Follow the steps.

4. Done. Upon boot you should be presented with a screen giving the option to either boot Windows or Ubuntu.


As always, these forums are available should you have any questions or run into problems along the way.

Hope that helps!

---

### Post by BuddhaBubba on 2007-02-28
ok, so now I'm not reinstalling windows because I want to finish my taxes first...so I have about 12.5 gb of free space on the NTFS partition

However, when I try to resize it in the Linux installation (so Linux can have it's own, say, 10gb partition) it doesn't work...it stops on the resizing step

---

### Post by lamego on 2007-02-28
Have you run defrag on Windows ? You will not be able to use the free space if there are some files at the end of the current partition.

---

### Post by BuddhaBubba on 2007-03-01
> **lamego said:**
> Have you run defrag on Windows ? You will not be able to use the free space if there are some files at the end of the current partition.

thanks, I'll try that tonight :)

**Just to let you know, it worked!!!  Thanks :D

---

### Post by Asoke Basu on 2007-07-24
Hi,

Do any one of you physically live in the city of Berkeley, CALIFORNIA. (or within the 25 miles of its radius) to offer us your expertise in installing/partitioning UBUNTU/MSXP, and then connecting two laptops (LENOVO
T42 & DELL INSPIRON B130) to the Internet (AT&T DSL)? We'll PAY.

My wife and I have very little technical known how. Nonetheless, we want try this Open Service because it has been recommended for its hassle free operational schemes, especially in the the areas of data downloading/uploading with large book-length texts and documents.

Thanks.

Asoke Basu
[email]asoke.basu@csueastbay.edu[/email]

---

### Post by Seisen on 2007-07-24
> **kebes said:**
> The hardest part of learning Linux is being willing to give it a try!

So if you're interested in putting in some effort to learn something new, I think you'll be quite happy with the results.


Dual-booting with Ubuntu and Windows is very straightforward nowadays. The Ubuntu installer can even resize Windows partitions for you. Since you said you've done partitioning before, this should be quite easy for you.

If you're reinstalling Windows, the easiest is to:
1. Partition the drive:
-NTFS partition for windows
-free space for Linux (as much as you want... I'd say at least 6Gb, more if you're serious about using it/installing software, etc.).

2. Install Windows to the NTFS partition.

3. Boot the Ubuntu LiveCD. Start the installer. Follow the steps.
Select "use free space for Ubuntu." Follow the steps.

4. Done. Upon boot you should be presented with a screen giving the option to either boot Windows or Ubuntu.


As always, these forums are available should you have any questions or run into problems along the way.

Hope that helps!

You also forgot patience, lots and lots of patience.:lolflag:

---

### Post by kebes on 2007-07-24
> **Asoke Basu said:**
> Do any one of you physically live in the city of Berkeley, CALIFORNIA. (or within the 25 miles of its radius) to offer us your expertise in installing/partitioning UBUNTU/MSXP, and then connecting two laptops (LENOVO
T42 & DELL INSPIRON B130) to the Internet (AT&T DSL)? We'll PAY.

Sorry I don't live anywhere near Berkeley! However, for your request to gain more visibility, you should consider posting it in the "California Local Community" forum:
[http://ubuntuforums.org/forumdisplay.php?f=188](http://ubuntuforums.org/forumdisplay.php?f=188)

It's quite possible that someone who watches those threads lives in your area. (More info on the California team [here]("https://wiki.ubuntu.com/CaliforniaTeam").)

Also note that the [Community Market]("http://ubuntuforums.org/forumdisplay.php?f=38") sub-forum is a place where people can advertise Linux services. Checking those posts (or putting your request there) might work.

Good luck! (If you want to try installing by yourself, the community is here to help you...)

---

