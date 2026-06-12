---
title: "Livecd loads and screen goes black"
date: 2004-11-27
forum: General Help
---

### Post by mikeymouse on 2004-11-27
Live cd loads,the ubuntu screen comes up while loading then  the monitor goes black 
the cd continues to load and then nothing.
 computer dell 4600, 768 meg of ram, nvidia fx5200 video card, 80 gig drive.
I checked the hardware out with Ubuntu and everything is supposed to be ok.
 Any help would be appreciated.
 If the live cd will not load does that mean the  install would not work?
  thanks  Mikeymouse [-o<

---

### Post by snipes420 on 2004-12-01
I am also having this problem with the live cd. but the install cd worked great. I installed ubunto on my drive then installed windows. windows ate my mbr so I had to download the live cd to try to fix it. but when I booted the default option of the live cd it came up blank like you said. Maybe we need to load a different option because of the nVidea video card? My hardware is an Athlon XP +2500, Asus A7N8X-X, GForce FX-5200, 512MB RAM
Edit: the nv option worked fine for me.
Edit: another thread that may be similar. [Here](http://www.ubuntuforums.org/showthread.php?t=6103)

---

### Post by fluxy on 2004-12-03
Hello, 
I think Ubuntu Live doesn't work with GeForce FX5200 Cards, coz I also have been facing these problems. Here's my configuration:
GForce FX-5200, 256MB RAM

The OS Loads, but finally my screen goes black :sad: .

The install works though, I had tried it, and it rocks. it would be nice if support would be received concerning this problem.

Thanks,
fluxy

---

### Post by mage.merlyn on 2004-12-09
I concur with your observation that the live CD does note work with the nVidia FX5200, having experienced the same problem.
   
   There is also another thread on this subject , [no video on LiveCD]("http://www.ubuntuforums.org/showthread.php?t=6103") where the original 'poster' also had the same problems.
   
   The message that I get displayed is something like 'unknown card (as yet)'. Not the full message obviously. 
   
   I am encouraged by the mention from snipes420 earlier that the 'install' version does not have the same problem.
   
 All I can say is, that it is just as well that forums like this exist as I was almost going to allow my 'liveCD' experience prevent me from installing Ubuntu.
   
   Regards
   
   David

---

### Post by mjb on 2004-12-09
I had the same problems with the livecd (and knoppix/gnoppix) it turned out that the fault was with the screen resolution, even though my monitor does make 1280x960(ir 1024) something in the modeline was wrong, screen=1024x768 at boot solved the problem (well, of course it isn't in 1280x960 then)

---

### Post by Guy2 on 2004-12-12
Same blank screen problem with Ubuntu Live CD and some older Knoppix and Mandrake releases. Recent Mandrake and Ubuntu Install work fine.

I have a SiS motherboard with integral SiS graphics chipset and AMD Duron. Just the sort of cheapo box that Ubuntu is likely to find its way onto, I guess.

Dell LCD monitor (using analogue input), runs happliy at 1280x1024.

Screen doesn't actually go pitch black, but flicks between charcoal and black before settling on charcoal. At least I get the initial Ubuntu startup screen, and Knoppix gave me a few clues before dying - things seem to go wrong after the install kernel has booted successfully.

---

### Post by wulf on 2004-12-13
[QUOTE=Guy2]Same blank screen problem with Ubuntu Live CD and some older Knoppix and Mandrake releases. Recent Mandrake and Ubuntu Install work fine.

I have a SiS motherboard with integral SiS graphics chipset and AMD Duron. Just the sort of cheapo box that Ubuntu is likely to find its way onto, I guess.

Dell LCD monitor (using analogue input), runs happliy at 1280x1024.

Screen doesn't actually go pitch black, but flicks between charcoal and black before settling on charcoal. At least I get the initial Ubuntu startup screen, and Knoppix gave me a few clues before dying - things seem to go wrong after the install kernel has booted successfully.[/QUOTE]
 Can you change the settings at the initial boot prompt? I haven't tried the Ubuntu LiveCD but others have given the option of specifying a wide range of settings, including failsafe video modes.

Wulf

---

