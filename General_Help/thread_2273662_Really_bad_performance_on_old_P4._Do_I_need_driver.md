---
title: "Really bad performance on old P4. Do I need drivers?"
date: 2015-04-14
forum: General Help
---

### Post by synergy99 on 2015-04-14
Been a few years since I used Ubuntu, I installed today on an old P4 (it's an HP-D530) with integrated intel graphics and 2gb ram...  wow, it really runs like crap (and ps I hate this new desktop). What the heck has happened to Ubuntu? Do I need a modern computer to run it?

Anyways, I'm not giving up quite yet. I suspect my main problem is graphic drivers, everything graphical is crazy laggy. As I type this each letter comes out 5 seconds later. Can someone help me sort out my driver issues?

I suspect I need to install intel graphic drivers, from lshw I get:

[B]        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:f0000000-f7ffffff memory:fc400000-fc47ffff ioport:14e0(size=8)
[/B]

Does that mean my graphic driver is installed, or not? Everything graphical on the desktop is really laggy and slow, what else can be causing my problems? Any tips appreciated.

---

### Post by grahammechanical on 2015-04-14
What version of Ubuntu did you install? For several years Ubuntu has had the Unity interface and that requires a video adapter capable of doing hardware accelerated video rendering. If our video adapter is not capable of running Unity 3D then Ubuntu will load to an open source video driver called llvmpipe. And that does not give a fast response even on more powerful video adapters.

Run this command

```
[COLOR=#333333][FONT=Ubuntu Beta]/usr/lib/nux/unity_support_test -p[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta] 
```

[/FONT][/COLOR]If the answer is No, then you will need to install Xubuntu, Lubuntu or possibly Ubuntu Mate.

Regards.

---

### Post by synergy99 on 2015-04-14
Thanks grahammechanical,

I got rid of the horrible horrible screw-up they call "Unity" and replaced it with LXDE and all is right in the world again.

Death to Unity.

---

### Post by Mark_McDonald on 2015-04-15
Hey, I would like to give full props to Xubuntu, I initially installed Ubuntu 14.XX LTS used it for a few months, and didnt like the userability of it. Xubuntu on the other hand is better I find. X doesnt crash as much as Ubuntu did. My sys is an old Dell Inspiron 1525, from 2007. All I used it for now is downloading music files and movies and some programs. The main issue is for me, is my mouse will stop working (moving) while I have multiple actions going on (transfering files from HD to USB HD, D/L files off interweb, music playing), I think my issue is a Hardware related thing. But Xubuntu is working about 50% better. Its a medium sized thing, where as Lubuntu is minimum sized. I forget what you call it, whatever. My mind is fried when it comes to computers lately.

---

### Post by Bucky Ball on 2015-04-15
Please mark as solved (see second link in my signature). To try the desktop environment used by Xubuntu, xfce4, simply install xfce4, log out, choose the xfce4 session from the session menu, log in. You can change back to lxde by repeating the process and selecting lxde. Good luck. ;)

---

### Post by tgalati4 on 2015-04-15
I run Linux Mint MATE which works well on older hardware.  There is now an Ubuntu MATE distro that you can try.  Yes, there have been a few changes.

---

### Post by dino99 on 2015-04-15
Seems to be due to your cpu, not supporting PAE
on old hardware select distro that dont use 3D
or continue booting with 3.2 kernels, not newer

---

### Post by mörgæs on 2015-04-16
Please don't post if you are not sure about the facts. A Pentium 4 supports PAE, just as 3 and 2 did. 

As always: Use one of the recent kernels, at least 3.13.

---

### Post by mattharris4 on 2015-04-17
> **mörgæs said:**
> Please don't post if you are not sure about the facts. A Pentium 4 supports PAE, just as 3 and 2 did. 

As always: Use one of the recent kernels, at least 3.13.

I can confirm that Pentium 4 processors support PAE.  I was unaware that P2 processors did, however so thanks for adding that to your comment.  If someone is still using a processor that does not support PAE there is a work-around, though.  Here is a link with information complied by our own sudodus (who is a moderator here):  [https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---

