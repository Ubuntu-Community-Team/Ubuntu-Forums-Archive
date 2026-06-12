---
title: "686 Kernel slow on Centrino laptop"
date: 2006-07-04
forum: General Help
---

### Post by isenalim on 2006-07-04
Hi,
I have an HP Pavillon DV1535 equipped with Centrino 1.6 GHz,512 MB RAM and integrated i915 graphics card.
The problem is this one: when running the 686 kernel X is extremely slower that when running on 386 kernel. I mean that windows are drawn slowly and animations are slow and the most striking effect is with 3ddesktop which is extremely slow on the 686 kernel, and pretty fast on the 386...
What's happening?
I am not a complete newbie but neither an expert, I dont' even know which kind of information to provide you...
I may just stay well with the 386 kernel... but shouldn't 686 be optimized for Centrino too?

---

### Post by reacocard on 2006-07-04
it should be faster. I have a similar system (HP dv4000, 1.7 Ghz, 1GB, i915) and the 686 kernel is faster for me. no idea why you'd be having trouble.

---

### Post by kpkeerthi on 2006-07-04
@isenalim
Run the top command and see what your idle cpu usage is. If it is pretty unusual (like 40-50%), then fix it per the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=194833"). Its probably because the SMP support is enabled by default in the kernel and you have an incompatible cpu - centrinos are not dual cores.

---

### Post by isenalim on 2006-07-05
Hi, thank you for the suggestion, now it seems a little faster, but with 386 kernel in my opnion is even faster. This is my glxgears- printfps output

3797 frames in 5.0 seconds = 759.209

in the standar very small window.
And this is in full screen

3797 frames in 5.0 seconds = 759.209 FPS

Is it possible to use compiz with such a low FPS in your opinion?
Now I reboot in 386 and post the new output
Bye

---

### Post by isenalim on 2006-07-05
So, the value of the output is more ore less similar, but, for example, 3ddesk is much faster with the 386 kernel, and anyhow isn't it a bit low as an FPS for my system?
Bye

---

### Post by reacocard on 2006-07-05
i run compiz on my i915 graphics no problem. just be sure to use aiglx instead of xgl.

---

### Post by isenalim on 2006-07-05
So, the final outcome of my experience is this:
386 kernel is definitely faster than 686 on my laptop, so I will stay with that for the moment, should I report this in some bug place?
Compiz is almost unusable with the 686 kernel while with the 386 is amazingly wonderful!
I'm looking forward to show this to my brother who is a Mac fan !
Thank you
Bye

---

### Post by hvbakel on 2006-07-06
You're probably suffering from the bug described here: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557). The solution is to add: 

echo 1 > /sys/module/processor/parameters/max_cstate

to /etc/rc.local.

In short, the underlying problem is that the processor does not function good in the low-power idle states with the 686 kernel. The above command puts the processor by default in the full-power state (even when it is idle). Please note that this has the side-effect that the processor temperature remains higher since it doesn't switch to low voltage when the processor is idle. To be honest, I haven't noticed any speed difference between the 686 and the 386 kernel so unless you have a dual core processor you might just want to stick to the 386 kernel .

---

### Post by zneastman on 2006-07-12
Unfortunately, this workaround doesn't seem to solve all of the problems with the 686 kernel on Centrino -- desktop responsiveness seems normal, but the system otherwise still drags, especially where disk I/O is concerned (at least for me).  Booting takes almost a minute on 686 vs. just under 30 seconds on 386, and program startup's similarly slowed.  So I'll be sticking with the 386 kernel for now and hoping the devs figure out what's what.

Nate

---

### Post by Bokonon on 2006-07-12
With the 2.6.15-26 kernel update and continued problems, I searched around and found this thread.  Good info and I have to report that this seems to have fixed my sluggishness issue with the newer 686 kernels.  2.6.15-23 was fine for me and I was actually still using that due to the responsiveness, but I wanted the fixes in the newer kernel.

My temps seem about the same and the CPU is throttling itself well so I am happy with the rc.local hack.  I tried the 2.6.15-26 386 kernel and that was also very good but in the end, I wanted to have the 686 kernel.  It seems slightly faster on startup, but about the same during normal use.

I hope they fix it, but since my temps are still good, I am not too concerned about using the above max_cstate hack.

FWIW, Dell XPS m170 with 2.0 Dothan CPU.  None of my other computers had trouble with the newer kernels.

Thanks!!!:-D

---

### Post by Cannedbread on 2006-07-13
yeah, i have an almost identical system. Pentium M 1.6 with TWO GIGS of ram and a 915 graphics chip, im getting some terrible performance with grapics i tried every sort of tweak with the xserver but it makes no diffy. 

_diffy_... what a good word..

im going to try the 386 kernel
686 was totally fine with 2.6.12 but now it just sucks

---

### Post by Toufik on 2006-07-14
I'm not sure it is related. I have a Vaio laptop with Centrino.  I was using kernel 2-6-15-23-686, everything was great.  I've upgraded the kernel yesterday to 2-6-15-26-686 and now the booting time is really slow.  It takes about 30 seconds for "mounting root file system".  I don't see any other differences...  Do you have the same problem during booting?

---

### Post by zneastman on 2006-07-14
Toufik:  That's exactly my sistuation.  686-23 works great, but it looks like everything later is really slow.

---

### Post by Toufik on 2006-07-14
I've looked around in a lot of forum.  I've found nothing interesting except compiling a custom kernel... I'll keep 23-686! :)

---

### Post by Toufik on 2006-07-18
Finally I recompile a kernel...

I first try, for training, to recompile the kernel 2-6-15-26-686 with the same original config (with "make oldconfig").  There, I discover 2 strange things: 
* the processor is chosen to be Pentium-Pro and not Pentium M
* the symmetric multiprocessing is active
Is it normal?

Changing these resolves my problem (slow boot)

---

### Post by tocnon on 2006-07-18
I've been watching this thread looking for a solid solution, or at least a confirmed reason for the problem.

My HP nc6220 (Pentium-M with Centrino) also has the same problem with higher CPU usage when using the 686 kernel.  But I discovered something interesting today... the 686 kernel worked just fine when the notebook was plugged into the port replicator.  When I reboot disconnected from the replicator, it's back to higher processor usage.  I'm not sure if this is ACPI-related because the notebook was plugged into power at all times, both connected and disconnected from the replicator.

Any thoughts on what could be making the difference with the kernel based on this?

---

### Post by jerinjoy on 2006-08-25
has this problem been fixed in the 2.6.15-26-686 kernel?

---

### Post by matthew on 2006-08-26
For the record, the 2.6.15-26-686 kernel is working great for me on my Pentium M.

---

