---
title: "Ran into a little problem with crashed windows partition!"
date: 2008-05-15
forum: General Help
---

### Post by brett11808 on 2008-05-15
Ok this all started when I was trying to set up a dual boot with ubuntu and Windows XP. But I forgot to defrag windows so when I shrunk it down (with partition magic8) it crashed. Now I have installed ubuntu 7.10 and this is what my partitions look like...
250Gb HDD 
237G ish Windows XP  only 100 is used  (40G movies and music)
10G ubuntu only 4 are used
1G swap
I want Windows gone, but I want all my movie and music off of that windows ntfs partition first, but there isn't enough room for it on the ubuntu partition to move them straight there.
I have tried to shrink the windows partition so i could make the ubuntu one bigger but I can't because windows is still marked as in use because it never cleanly shutdown. 
So long story short how do I make this happen. I hate windows I just need my stuff back from it before I can kill it for good!
Thanks for any help!

---

### Post by sweeneytodd on 2008-05-15
see what you can do with the live cd, gparted for instance, could be a mounting thing and this'll override mounting things to a degree

---

### Post by UnWarierMage224 on 2008-05-15
hmm... not sure if this will help but can you mount your windows partition from within linux? If you can, then you can navigate to your documents folder and pull what you need... If you have an external HD or some blank DVDs handy then you can transfer/burn copies of your info to them and then get rid of windows. 

You should be able to access your windows partition through the "Places" menu. 

Hope this helps. 

-'Mage

---

### Post by brett11808 on 2008-05-15
I've tried Gparted live CD and I can't resize the Windows partition. I can only move it 8mb left and 7mb right. Kind of frustrating!

---

### Post by brett11808 on 2008-05-15
> **UnWarierMage224 said:**
> hmm... not sure if this will help but can you mount your windows partition from within linux? If you can, then you can navigate to your documents folder and pull what you need... If you have an external HD or some blank DVDs handy then you can transfer/burn copies of your info to them and then get rid of windows. 

You should be able to access your windows partition through the "Places" menu. 

Hope this helps. 

-'Mage
 Yes I can access my windows partition but its 40 Gigs of stuff do I have any other options?

---

### Post by ccw127 on 2008-05-15
As a thought, use your trusty Windows CD to do a repair on the windows installation. Then once you have a working windows OS again, defrag and use gparted once again (it should work fine then).

As a side note, if you have never used your Windows install CD to do a repair (not a reinstall):
     Right after you accept the agreement, you are presented with 2 or 3 options, one of which is press R for recover. DO NOT press 'R'! Follow the next screen or two until is says it is detecting previous installations of Windows. It will then present you with an 'R'ecovory option again; now you can press it. After that it is pretty much automated.

Chris

---

### Post by brett11808 on 2008-05-17
> **ccw127 said:**
> As a thought, use your trusty Windows CD to do a repair on the windows installation. Then once you have a working windows OS again, defrag and use gparted once again (it should work fine then).

As a side note, if you have never used your Windows install CD to do a repair (not a reinstall):
     Right after you accept the agreement, you are presented with 2 or 3 options, one of which is press R for recover. DO NOT press 'R'! Follow the next screen or two until is says it is detecting previous installations of Windows. It will then present you with an 'R'ecovory option again; now you can press it. After that it is pretty much automated.

Chris

Yeah well I guess i hit the wrong R!!!! I got a fresh windows install when it was all said and done with so guess its time to start downloading.
Oh my the way i can't log into my ubuntu now it says error loading operating system....any ideas how to fix that????

---

### Post by teaker1s on 2008-05-17
knoppix live boot iso to fix ntfs corruption

```
fdisk -l
```
then ```
sudo ntfsfix /dev/sda
```change to appropriate location

---

