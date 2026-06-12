---
title: "Has anyone got one of these to Ubuntu"
date: 2006-11-05
forum: General Help
---

### Post by bobpur on 2006-11-05
I just finished a new machine over the weekend and installed WinXP in it for gaming, video and whatnot.
The specs are: AMD 64 +4400 dual core, 2048 mb ddr400 memory, SLI (two XFX 7600 GT XXX videocards), two 200 gb SATA hard drives RAID 0 (striping), and a 200gb PATA hard drive for additional storage (Maybe Ubuntu Edgy or Dappers new home).
I searched the Wiki and couldn't find anything about dual core processors, SLI or RAID. I remember seeing posts about these things (separately, but not all in one machine) and didn't bother to read at the time. At the time, I wasn't concerned about RAID, SLI or Dualcore processors.
Has anyone got a machine like this to run Ubuntu? What problems might I encounter or should I not bother with it. I have two other Ubuntu machines.

---

### Post by chriscando on 2006-11-06
I have used dual core and RAID under Ubuntu with no problems.
To take advantage of dual core I just installed (via Synaptic) the linux-686-smp kernel package (easy!). Its cool, right away the system monitor shows both processors.
I have used software RAID in ubuntu (where I dont think you even need a card, right?) where I set it up while installing. I have also used it where I have a card and the RAID0 is setup before installing and then Ubuntu already sees the 2 hard drives as one during installation. Pretty straight forward. In both cases I did not encounter any problems.
But sorry no experiance with SLI.

---

### Post by David Corrales on 2006-11-06
You shouldn't have any problems. Edgy comes with SMP by default and sata drivers.
SLI is enabled in the latest nvidia drivers I think so that shouldn't be a problem either.
Finally, if it's hardware RAID, it'll be transparent to the OS.

---

### Post by bobpur on 2006-11-06
Thanks for the positive responses. My RAID is thru the motherboard, which is an ASUS A8N32 SLI Deluxe. It looks like I forgot to mention that in my original post.

---

### Post by thexaspect on 2006-11-11
I haven't checked yet on Edgy, but in Dapper SLi did not come enabled by default, and I had to do it manually. i forget the command, but if you do a quick search on the forums you should find it. i'm also running 64bit, smp, and sli, and it was a pain in the @$$ to get it all working properly for some reason, asus a8n-sli, 4800+ amd x2, and dual geforce 7600 Gt's. a lot of the trouble was just rewriting the xorg.conf file for dual widescreen support, so be warned if you want to use the dual monitor option on your video cards. twinview and sli don't work together, so you have to use either xinerama or two separate x sessions linked together, either is a pain, so happy hunting if you want dual monitors, there's no real guide, just trial by fire =)
edit:
forgot to add, SLI and dual monitors dont work together, it's a flaw in the drivers that nvidia acknowledges, so you'd either have to run one monitor on each video card(possible), or set up another pci video card just for the second monitor, and since you can only play one game at a time ....

---

