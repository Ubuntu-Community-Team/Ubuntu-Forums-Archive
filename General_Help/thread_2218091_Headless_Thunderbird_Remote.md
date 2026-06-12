---
title: "Headless Thunderbird Remote"
date: 2014-04-19
forum: General Help
---

### Post by JKyleOKC on 2014-04-19
For years now I've run my email client, a Windows-only program called "*The Bat!*", in a VBox installation of WinXP that loads automatically at boot time (via a set of scripts called *vboxtool*) and runs in background without requiring that I be logged into the host system. It uses VBox's built-in RDP server to allow me to connect to it from any station on my LAN, and I've created launchers for that on each station. The system runs 24/7 and has been quite satisfactory.

Unfortunately, something went wrong about three weeks ago, causing both ends of any LAN connection to freeze unexpectedly while scrolling or saving a large file from a remote connection. I've not been able to determine the cause of the problem -- it could be a flaky NIC, a corrupted copy of the program in the VM, a bug in VBox itself, or even a bug in the Linux kernel. That last seems most probable at the moment and I've filed a bug report that another user has confirmed, after I found an entry in */var/log/kern.log* showing a system crash during a file-splice operation after a timeout during the transfer!

All of this, though, is background for my **real** current question. I've decided to abandon the use of XP and *TheBat* entirely, moving my email to Thunderbird (which seens closest to what I've used for years). However I want to keep the 24/7 background operation, which need not be in a VM at all if I can automatically start TBird to run headless behind an RDP or VNC server on the machine currently being used to host the mail. Ideally I would want to run RDP so that my launchers on the rest of the LAN could operate with no change from the present rdesktop setup.

Searching the forums and via Google turns up lots of posts about TBird, and lots about headless operation, but I've not found any yet that answer my need for rather specific How-To data to set this up. Can someone show me the way?

Specifically, I need to create an upstart script to start TBird once the drives are up, the network is available, and the RDP or VNC server is running. I also need to know whether to run TBird as my usual user, or as a unique (newly created) user of its own. And finally, I need to know the security implications; I don't want any of this to be visible to the outside world, except for the necessary access to my outside mail servers. That last might change as I gain experience with using smartphones and tablets, but initially I want to keep the local system confined to my LAN. Have I missed anything so far?

---

