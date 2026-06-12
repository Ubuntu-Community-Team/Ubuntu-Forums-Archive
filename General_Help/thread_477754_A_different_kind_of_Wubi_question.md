---
title: "A different kind of Wubi question"
date: 2007-06-18
forum: General Help
---

### Post by Protagonistics on 2007-06-18
I use wubi fairly happily and have been playing around with linux for about 3 weeks. My question is: Ubuntu is running awfully buggy and I'm looking for fixes, workarounds, and answers to these things on the forums but I want to know if it may be Wubi that increases the GENERAL bugginess of my computing experience or if Ubuntu just isn't there yet. I honestly can't believe that so many users are using linux as a main OS because so much nonsense goes on all the time. Is it just me and my Wubi, or what?

A.L.

---

### Post by gwon on 2007-06-18
> **Protagonistics said:**
> I use wubi fairly happily and have been playing around with linux for about 3 weeks. My question is: Ubuntu is running awfully buggy and I'm looking for fixes, workarounds, and answers to these things on the forums but I want to know if it may be Wubi that increases the GENERAL bugginess of my computing experience or if Ubuntu just isn't there yet. I honestly can't believe that so many users are using linux as a main OS because so much nonsense goes on all the time. Is it just me and my Wubi, or what?

A.L.

To be honest, you'll probably need to be more specific on the kinds of bugs you're talking about. However, to the best of my understanding the only difference between your ubuntu install in wubi, and the next guy's install on a partition is the virtual disk, which shouldn't have any effect on your installed system other than disk access speed.

---

### Post by shadow01 on 2007-06-18
>  I use wubi fairly happily and have been playing around with linux for about 3 weeks. My question is: Ubuntu is running awfully buggy 

I'm also using Wubi for ~3 weeks now, but for me the only known bug is that hibernation thing, wich is really awfull, but I haven't had any other problems, Ubuntu itself is running very smoothly...

---

### Post by varchar255 on 2007-06-18
> **shadow01 said:**
> I'm also using Wubi for ~3 weeks now, but for me the only known bug is that hibernation thing, wich is really awfull, but I haven't had any other problems, Ubuntu itself is running very smoothly...

I am an ex-Wubi user. I had two major problems with Wubi--the hibernation issue ([http://ubuntuforums.org/showthread.php?t=436910](http://ubuntuforums.org/showthread.php?t=436910)) and every so often, my machine would just freeze completely. It happened most often when running Update Manager ([http://ubuntuforums.org/showthread.php?t=454893](http://ubuntuforums.org/showthread.php?t=454893)) but would also happen at other times, and I never figured it out. I installed a full installation using the alternate ISO and my full installation doesn't have any problems whatsoever.

Best of luck to you.

---

### Post by Protagonistics on 2007-06-19
Well, I tried to install Ubuntu 7.04 on a new partition I created with Partition magic. Apparently I didn't know what I was doing and ended up deleting windows (really, I was quite careful and I don't understand it). Anyway, I just decided to forego the typical 6 hour reinstallation of windows xp pro with updates and reinstallation of software and just wiped the disk and installed an ISO i had of Feisty. It is incredible how big of a difference there is. No disappearing toolbars, no freezing, no Firefox search bars not responding to whatever I'm typing, and ESPECIALLY no messages about lack of space (I had  9 gigs allotted to my Wubi install). Wubi was nice to try an installation of Ubuntu on for about 2 weeks. it's better than using a live cd, that's for sure.  But I am now convinced that it was Wubi that made Linux unstable- not Linux itself. I am now much happier with Ubuntu's behavior though it is a little early to say that I'm completely satisfied. CONCLUSION: Wubi = a little unstable. A clean feisty install is definitely better.

Thanks for the agreements. I think we've ended up with a helpful conclusion for developers.

A.L.

And speaking of developers, I hope they'd visit my blog on a new user's perspective with Ubuntu to get a better idea of what should be developed: [www.noobuntu.blogsavy.com](www.noobuntu.blogsavy.com)
thanks.

---

### Post by CrazyGuy123 on 2007-06-20
If you say there were messages about you running out of disk space, that could be the cause of all the rest of the stuff.  Linux OS's don't like running out of space.

The disk space message itself could have been caused because while wubi might allocate say 10gb itself, it devides this up into virtual disks, and any one could be full.  In particular, with 9GB allocated to wubi, the "home" folder is only 1GB maximum.

As a note to devs, I think particularly for the home folder, the allocated size is limiting.  Most average users won't understand that they need to save things on the host drive to avoid running out of space.  There needs to be either:

A. a way to make it clearer to users
B. a way to expand the home disk by say 1GB each time it's nearly full
C. a way to mount the home folder as a real folder in ntfs, to effectively take the limits off what can be saved there - that brings back a few permissions problems though. (although not so bad as having the whole thing on ntfs)

---

### Post by Protagonistics on 2007-06-21
I completely agree and now understand that that was what was indeed happening with me. I might have to make mention of that in my blog...

---

### Post by ago on 2007-06-21
> **CrazyGuy123 said:**
> A. a way to make it clearer to users
B. a way to expand the home disk by say 1GB each time it's nearly full
C. a way to mount the home folder as a real folder in ntfs, to effectively take the limits off what can be saved there - that brings back a few permissions problems though. (although not so bad as having the whole thing on ntfs)

I was thinking of creting a C:\wubi\shared, and symlink that to /home/shared, people that run out of space could simply move folders in there. 

Tuxcantfly has a tool to migrate a virtual disks to a real partition. 

As for expanding an existing image, the trick is to expand the image file with dd via the seek option, and then resize the filesystem within the file. For home that is simple since you can umount home and then run a normal offline resizer (resize2fs) then mount it back, for / you really need an online resizer (see for instance ext2resize, google for online ext3 resize). I played briefly with that with partial success, but did not have much time to do it properly.

---

