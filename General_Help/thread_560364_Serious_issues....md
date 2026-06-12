---
title: "Serious issues..."
date: 2007-09-26
forum: General Help
---

### Post by ceduriki on 2007-09-26
So I put together a new computer. I was installing XP pro on it, But quit and decided to use Ubuntu instead. For some reason, that particular motherboard won't read the CD, to I put the IDE drive in a converter for usb, plugged it into my laptop and installed it from there. I put the drive back into the other comp and it starts booting but then gives me something like "Kernel error: killed the idle task". Any suggestions on how to get it booting?

---

### Post by Arwen on 2007-09-26
Do you have 2 or more RAM chips or a dual core CPU?

---

### Post by PmDematagoda on 2007-09-26
Did you check the CD for errors after burning it? And at what speed did you burn the CD? If it's too fast then the CD may not be properly made.

---

### Post by wpshooter on 2007-09-26
> **ceduriki said:**
> So I put together a new computer. I was installing XP pro on it, But quit and decided to use Ubuntu instead. For some reason, that particular motherboard won't read the CD, to I put the IDE drive in a converter for usb, plugged it into my laptop and installed it from there. I put the drive back into the other comp and it starts booting but then gives me something like "Kernel error: killed the idle task". Any suggestions on how to get it booting?

I don't think you should be trying to install via another computer.  You need to find out what the problem is with the original computer.

What exactly do you mean when you say "**that particular motherboard won't read the CD**" ?

Thanks.

---

### Post by notwen on 2007-09-26
Could you give us the specs of your newly built system? =]

---

### Post by ceduriki on 2007-09-26
608 mb ram (1x512, 1x128, 1x256) and a 2.5 ghz pentium 4.

---

### Post by strabes on 2007-09-26
We need the hardware information (vendors), not the speed.

---

### Post by Arwen on 2007-09-27
I've somewhere read it's memory issue,I've experienced it myself in a friend's old desktop with kubuntu 6.10,had 2  RAM chips (256 and 512 MB) of differend brands and that error came up when installing kubuntu.I took one chip off and everything was fine.I don't know what the problem was,I tried with the other chip on and still it worked.I've googled a bit and found this [http://www.linuxquestions.org/questions/showthread.php?t=347997.Why](http://www.linuxquestions.org/questions/showthread.php?t=347997.Why) don't you try with one chip on only,let's say the 512 MB one..?

---

### Post by PmDematagoda on 2007-09-27
It might be because very often, RAM modules of different brands, speeds and timings don't work together, this is especially true in Dual-Channel Mainborads.

One thing about getting RAM modules is, try to make them the same, the same brand, speed, timings and even capacity. If you satisfy these then you won't get a problem with the RAM modules unless of course one of them becomes defective.

---

### Post by ceduriki on 2007-09-27
Ok, the RAM thing worked, now it boots properly but I have another problem. The GUI won't load, so I'm stuck in command based. The error log tells me "screen not found". Should I just type the command for it and run it? If so, what command?

---

### Post by bigken on 2007-09-27
try this sudo dpkg-reconfigure phigh xserver-xorg 
and select vesa as your video driver 
then type startx

---

### Post by ceduriki on 2007-09-27
Thanks. I won't get to try it until I get home. I'll tell you how it goes.

---

### Post by bigken on 2007-09-27
you could also try 

sudo dpkg-reconfigure xserver-xorg 

this is a full system configuration just go with the defaults  except the video driver again select vesa this should at least get you to desktop good luck :)

---

### Post by PmDematagoda on 2007-09-27
What's the video card you have?

---

### Post by ceduriki on 2007-09-27
It's an nVidia geForce 4.
btw, does ubuntu have a partitioner i can use? I want to split the HD in half so i can run windows on one partition and ubuntu on the other. Save me having to use another HD.

---

### Post by bigken on 2007-09-27
you need to install windows 1st yes it does have a partitioner gparted you can run it from the live disc on unmounted drives but your best bet is to use gparted liveCD its in my signature

---

### Post by ceduriki on 2007-09-27
> **bigken said:**
> you need to install windows 1st yes it does have a partitioner gparted you can run it from the live disc on unmounted drives but your best bet is to use gparted liveCD its in my signature

ok, so i install windows, then install ubuntu with live CD. So clear the ubuntu partition, get my windows on, THEN re-install ubuntu.got you.

---

### Post by bigken on 2007-09-27
you can partition your drive when you install win xp ubuntu will pickup the whats left of the hdd 

I would manually edit my ubuntu partition

/ 10 gig (system)
1 gig swap twice your ram 
whats left /home

good luck

---

### Post by ceduriki on 2007-09-27
The xp install is giving me some weird data on the partitions. There's one around 4 GB, which I know are the linux prog files. But the rest is a separate partition that seems to be on its own. Do I just delete it and redistribute the space?

---

### Post by bigken on 2007-09-27
what size is it ?

---

