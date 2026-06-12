---
title: "Getting Driftnet to work"
date: 2007-03-27
forum: General Help
---

### Post by Hank_61 on 2007-03-27
Hey there, brand new to Ubuntu 4.10. Been running it for about a week or so and I can't tell you how much I'm enjoying it.

Got a small issue that no amount of googling or forum-browsing has been able to resolve. I downloaded Driftnet from the Add/Remove Programs application. It installs fine and appears in my Applications>Internet folder, but when I try to start it nothing happens.

I double checked and made sure that I had installed every lib file that it needed to run. Can't seem to find anyone else who's got the same problem.

I have a feeling the solution is something embarrassingly simple that'll make me feel like the Ubuntu n00b I am. Any ideas?

---

### Post by leftcase on 2007-03-27
Hi there, 

What are you trying to accomplish with driftnet ? For instance - if you stick it on a proxy server, you'll see all of the pictures going through it. If you put it on a unswitched network - you'll also see piccies through it. If however you're on a port on a switch, you'll see nothing.

What's your setup like?

Cheers

---

### Post by Hank_61 on 2007-03-27
I was considering bringing my laptop to work and using Driftnet for managerial purposes. We just use a typical wireless LAN setup (using IEEE 802.11b). Does it not work over a wireless LAN? Is that why the program doesn't even open?

---

### Post by leftcase on 2007-03-27
Try it - As far as I know, driftnet can only monitor traffic that passes across the network interface of the computer your are running it on.

I'm guessing that this means it'd work if you had your computer patched into a cheap hub device, where the network traffic goes across every port at once. It won't however work in a switched device, where network traffic is directional and is sent only to the port/s requesting it.

So the answer really is - it depends on the WiFi AP. I don't know if traffic across it is switched traffic or not...

---

