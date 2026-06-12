---
title: "XOrg using +90% CPU"
date: 2008-05-01
forum: General Help
---

### Post by CD Baric on 2008-05-01
Hi:

Brand new install of 8.04 on the following hardware:

Asus M2N-VM DVI motherboard
AMD 6000+ dual core CPU
Geforce 8600 video card
  tried with stock nv driver
  and restricted nvidia driver
  and envy installed nvidia driver
4 gig DDR II low latency 800 MHz memory

After a few minutes xorg CPU usage runs up to +90% and stays there for one of the CPUs.

Also tried with 8.04 64 bit same result.

Very frustrating - WHAT IS THE DEAL?

Bar

---

### Post by CD Baric on 2008-05-03
Found the cause!

I have reproduced this problem on two different computers.

The problem is the 'System Monitor' application CAUSES the massive CPU consumption!

Reviewing the CPU use using 'top' in a console displays the difference between using 'System Monitor' and not using 'System Monitor'.

So there is a real problem but the problem looks to be caused by the very application that measures CPU useage.

Bar

---

### Post by Monicker on 2008-05-03
Weird.  You should probably file a bug report on that.  Good catch.

---

### Post by CD Baric on 2008-05-03
I filed a bug report on my initial findings and am now going to include this latest revelation.

I have since tried running 'System Monitor' on my legacy Ubuntu machine and note that it markedly increases CPU useage for xorg as measured by 'top' - from .5% noy running to 6% running. Not as bad as with the dual core systems but still worth looking into.

Bar

---

### Post by Th3Gh0st on 2008-09-26
Hello, I have the same problem with Ubuntu 8.04
I have tried this solution:

[http://www.redhatmagazine.com/2007/11/20/tips-and-tricks-why-does-xorgs-cpu-usage-shoot-up-when-using-nvidias-driver/](http://www.redhatmagazine.com/2007/11/20/tips-and-tricks-why-does-xorgs-cpu-usage-shoot-up-when-using-nvidias-driver/)

and it helped me just partially. Sometimes it is 5-6% when I am on desktop, but when I remotely connect (via vnc), it jumps to approximately 90%, and when I ssh, it is less then 1%. Does anyone have right solution for this problem?

Graphic card: PCI-E ATI X300
Processor: Intel E4500
Memory: 2GB ddr2


Sincerely,
Darko

---

### Post by Th3Gh0st on 2008-09-26
Omg, I think I found the problem, hardware tester told me that my graphic drivers are not in use, and I enabled them and now it is all ok.

---

### Post by soleblaze on 2008-09-28
> **Th3Gh0st said:**
> Omg, I think I found the problem, hardware tester told me that my graphic drivers are not in use, and I enabled them and now it is all ok.

Is that the 'hardware drivers' section and are you using ati/nvidia drivers now?  I'm having the same problem, however I have an intel chipset.

---

### Post by katon on 2008-09-28
okeyokey,,, sorry people but i can't understand , you bought a new computer , and you have a problem with the NVIDIA drivers? i thought nvidia uses opensource drivers and it is installed automatically....
i am afraid of buying a quadcore next month .....

---

### Post by soleblaze on 2008-09-28
> **katon said:**
> okeyokey,,, sorry people but i can't understand , you bought a new computer , and you have a problem with the NVIDIA drivers? i thought nvidia uses opensource drivers and it is installed automatically....
i am afraid of buying a quadcore next month .....


Teaches me to read the first post..looks like he's using an nvidia card and didn't have the nvidia supplied driver installed (using the nv open source driver)

Nvidia and ATI use proprietary drivers.  Ubuntu can't currently distribute them on disc, so you have to go and enable them, which causes it to download and set them up.  The drivers work great once you install them.

---

### Post by katon on 2008-09-28
okey,,,thanks soleblaze , there is one of ATI or NVIDIA that is MORE "open source like "  ? or is just the same when i will buy graphic card?

---

### Post by soleblaze on 2008-09-28
> **katon said:**
> okey,,,thanks soleblaze , there is one of ATI or NVIDIA that is MORE "open source like "  ? or is just the same when i will buy graphic card?

they're pretty much the same atm.  Last time I ran them, nvidia was the better card to use driver wise..but it's been a long time and I hear ATI has made major inroads to getting better drivers out there.

---

### Post by Th3Gh0st on 2008-09-29
> **soleblaze said:**
> Is that the 'hardware drivers' section and are you using ati/nvidia drivers now?

Yes, it is the hardware drivers section. When I first entered, I had an option to enable ATI driver.

[[IMG]http://img150.imageshack.us/img150/7533/ativu2.th.jpg[/IMG]](http://img150.imageshack.us/my.php?image=ativu2.jpg)[[IMG]http://img150.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

