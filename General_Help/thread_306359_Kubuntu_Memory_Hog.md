---
title: "Kubuntu Memory Hog?"
date: 2006-11-24
forum: General Help
---

### Post by LinLenLap on 2006-11-24
I installed Kubuntu the other day to give it a try, and I really, really like the look of it as compared to gnome. But I don't have the best system, and so while I had a nice looking desktop with Gnome taking up about 150Megs of RAM, Kubuntu is currently using about twice that on a normal install.

I've already disabled all the themes eye-candy, and it's starting to look more gnomish, but the memory usage is remaining high. I've disabled all sort of services too, even some I think I might like to use.

Am I doing something wrong here? I'm thinking I'm going to switch back to ubuntu for this reason, and also because the forums here are really geared toward Gnome.

Any advice?

LLL

---

### Post by aysiu on 2006-11-24
Try *kde-core* instead of *kubuntu-desktop*:
[http://psychocats.net/ubuntu/kde-core](http://psychocats.net/ubuntu/kde-core)

---

### Post by LinLenLap on 2006-11-25
Thanks for the suggestion... I gave it a quick look, but on first loading my desktop was messed up. Unfortunately, I only had one night to play around with this... so ubuntu is back on for now. 

Maybe come Feisty I'll give KDE another try.

L.

---

### Post by louieb on 2006-11-25
Linux is set up to use all available memory. After it has been running for a while most if not all memory is used by a program or it holds the content of some file. The reason is if you got it use it. Not really a problem. If you open another program Linux just frees up some of the file cache.
Here is a page that explains it better than I can. []("http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Swappiness_.282.6_kernels.29")
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management)
It also shows how to use the free -m command to find your real memory usage.

---

### Post by LinLenLap on 2006-11-25
> **louieb said:**
> Linux is set up to use all available memory. After it has been running for a while most if not all memory is used by a program or it holds the content of some file. The reason is if you got it use it. Not really a problem. If you open another program Linux just frees up some of the file cache.
Here is a page that explains it better than I can. []("http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Swappiness_.282.6_kernels.29")
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Overview_of_memory_management)
It also shows how to use the free -m command to find your real memory usage.

Doh! Thanks for the link. I feel dumb. Looking at that it seems like KDE was actually running better than my gnome desktop is. Thanks for the link louieb, that's pretty different than how windows does it huh?

L.

---

### Post by msak007 on 2006-11-25
> **LinLenLap said:**
> Doh! Thanks for the link. I feel dumb. Looking at that it seems like KDE was actually running better than my gnome desktop is. Thanks for the link louieb, that's pretty different than how windows does it huh?

L.
Don't feel dumb...it's a result of years of abuse by M$ :). Lots of us are still learning about how Linux works, and just have to get used to seeing things from a different (better) perspective. If you want to hear something funny, I had an old 500 MHz / 128 MB Compaq that I put Xubuntu on, thinking that it couldn't handle Kubuntu. Well Kubuntu ran faster on it! It was still slow and (to me) unusable for normal day-to-day usage, but KDE did run faster than XFCE. BTW, you never mentioned how much memory you have in your system.

---

### Post by LinLenLap on 2006-11-25
> **msak007 said:**
> Don't feel dumb...it's a result of years of abuse by M$ :). Lots of us are still learning about how Linux works, and just have to get used to seeing things from a different (better) perspective. If you want to hear something funny, I had an old 500 MHz / 128 MB Compaq that I put Xubuntu on, thinking that it couldn't handle Kubuntu. Well Kubuntu ran faster on it! It was still slow and (to me) unusable for normal day-to-day usage, but KDE did run faster than XFCE. BTW, you never mentioned how much memory you have in your system.

528MB of RAM on a celeron M. KDE actually felt really snappy, even with the bouncing icons and all the nice looking stuff turned on. I just saw how much RAM it was (apparently not) eating up and panicked.

I'm writing this from a clean install of Ubuntu right now, but come christmas I think I'll apt-get install kde-desktop as a christmas present to myself. ;) 

L

---

### Post by CGW on 2006-12-08
> **LinLenLap said:**
> 528MB of RAM on a celeron M. KDE actually felt really snappy, even with the bouncing icons and all the nice looking stuff turned on. I just saw how much RAM it was (apparently not) eating up and panicked.

I'm writing this from a clean install of Ubuntu right now, but come christmas I think I'll apt-get install kde-desktop as a christmas present to myself. ;) 

L

I recently switched from Gnome to KDE.  First I performed the kubuntu-desktop install and then ended up performing a fresh install of Kubuntu Edgy.  There's no looking back for me at this point.

---

