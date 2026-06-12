---
title: "dmraid shows no RAID disks on Sil3112"
date: 2006-07-19
forum: General Help
---

### Post by hurr1k4ne on 2006-07-19
Hey i crawled this forum since yesterday to be able to install ubuntu to my server.
It has an SIL3112 Chipset pci-card inside...

I revealed from several threads that it should be possible to access this RAID0(2x 80GB Sata).

When i start the desktop live cd, after compiling dmraid
it always says : no raid disks....
What could be the problem...
do i need to install a driver?? (only feodora/suse available)


some sites i used to figure out the problem...
i wanted to start compiling a kernel but before i need to get the access to Raid done....

[http://ubuntuforums.org/showthread.php?t=2557](http://ubuntuforums.org/showthread.php?t=2557)
[http://unclean.org/howto/sii3114_linux.html](http://unclean.org/howto/sii3114_linux.html)
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

and several others....

Counting on your help... Thanks in advance...
I just started to play with ubuntu. I lke it much so i would like to use it on my server and kick that d**n Windows...

---

### Post by HAARP on 2006-07-20
Why compile dmraid? It's in the repos. Perhaps something went wrong while compiling?
No driver should be needed.

---

### Post by hurr1k4ne on 2006-07-22
Hey Thanxs for your answer...

I did a big mistake... the two raiddisks were connected to the onboard raid controller... i switched now raid disks to sil3112.

now /dev/mapper shows  sil_agahcfddaead

but not a second device... and it dows not show up in nautilus on Computer
](*,) 

What could this be...

and the third sata disk is connected to the onboard contoller.. Why doesn't the sata device doesn't show up?? on the CHIP is sth with SIL 976 i think.

The sata disk should show up right??

THX for Help

---

