---
title: "File shares from Ubuntu are goig very slow"
date: 2008-03-04
forum: General Help
---

### Post by zac_haryy on 2008-03-04
I just setup Ubuntu and have a RAID 5 configuration setup up and am sharing that mounted folder on the network through SAMBA. For some reason transfers to and from this are very slow. I have a xbox hooked up and if I try to stream a video from the Ubuntu machine it will not play at normal speed and will slow down a lot. I know the xbox is working because I can stream from Windows PC's and it works fine. 
Even when I transfer from Windows PC to Ubuntu it goes really slow. The Ubuntu machine just sits there with nothing running besides the Ubuntu desktop (gnome, and the other process's that run for it). Please help me out on what I can do to get my network bandwidth from Ubuntu to full speed. Thanks!

---

### Post by fjgaude on 2008-03-04
What's your computer setup, CPU, LAN speed, etc.?

---

### Post by moonlightcheese on 2008-03-07
i have the exact same problem and i've been looking for the solution for a while.  my setup:

4x320GB 7200.10's (RAID5 mdadm)
Athlon 4000+
1GB DDR400
Gutsy 7.10 A64 server
DFI Lanparty UT nForce4 Ultra-D

i'm using the Marvel Yukon 88E8001 Gigabit nic with the appropriate default driver that ubuntu assigns (don't have access to it at the moment).  there's also a Vitesse VSC8201 Gigabit Phy on board.

what data can i provide that will help?  i'll have an iperf test up in this thread by the end of the day if no one else does.  anything else?

on a side note, if you do a forum search, you'll notice that slow samba speeds are incredibly common to many ubuntu users.  i wonder when the developers will actually take this as a serious concern and do something about it... currently i'm getting much faster network speeds in windows than with linux...

EDIT (addition):

i've already tried changing txqueuelen to 100000 for the interface but all that did was produce errors but speeds were faster.  haven't tried anything else.

---

### Post by fjgaude on 2008-03-07
Are you going through a router? One gigabit NIC seems plenty fast enough if your have a gigabit router. Perhaps you are going from computer NIC to xbox NIC?

Need more details... I don't have any experience with "streaming", just data transfer. <smile>

---

