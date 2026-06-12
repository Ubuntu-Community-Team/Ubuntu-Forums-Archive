---
title: "XDMCP and local sound"
date: 2008-05-26
forum: General Help
---

### Post by gonehiking on 2008-05-26
I am running gutsy on my main desktop which I wanted to make into LTSP server for an LTSP client as well. I installed ltsp packages on my server and built the ltsp client root filesystem, and updated pxe boot configuration to allow booting ltsp kernel. My LTSP client booted the kernel using pxe just fine and then it went to a gdm login screen. After I logged in, I was surprised to find that I was logged in using xdmcp on my main server and the LTSP client didn't seem to have mounted its root filesystem using NFS from the server at all. It turns out I like this setup because I can install all apps on just my server and access them from any LTSP client, plus the clients can use the more powerful CPU on the server. The problem I am running into is that clients do not seem to access their local resources, like sound card, USB and CDROM, If I run any software on the client that plays sound, sound comes out of speakers on the server.

I would prefer to be ble to continue logging in with xdmcp but be able to access local devices on client, especially sound. If that is not doable, I would like the client to mount its root fs from server and access all local resources. Any ideas on how to achieve this?

Thanks!

---

### Post by kingtiger01 on 2008-10-17
same problem here, its great and all for a soundless, diskless, (almost) useless streamlined system. but beyond that worthless...

i wish to do the same, with a diskless system, but with DVD-rom drive, Audio, and USB devices. using XDMCP for X on a server, and Local devices from the client for rendering/playback...

has anyone been able to appropriately do this...

i assume you could*Possibly*, build a Live-cd with a new xclient, and Y-sound server/client and have it use the inderect broadcast/connect method. and set up youre server to connect to the clients Y-sound server by default, for audio for that X session. 

But, i wouldnt even know how to do that... just theory for me...


Big BUMP... **going to Copy this over to Linuxquestions, and see if i can get any help there.. if so, ill copy my results here as well.**

---

