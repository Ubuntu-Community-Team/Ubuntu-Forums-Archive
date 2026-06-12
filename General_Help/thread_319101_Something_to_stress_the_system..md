---
title: "Something to stress the system."
date: 2006-12-15
forum: General Help
---

### Post by Blindraven on 2006-12-15
Ok,
Save for a weird mouse freeze (but then when I click it unfreezes) issue, and the fact that I am "not quite" sure weather this edgy is picking up the fact that I am running 2 (duo64 4200+) cpu ' I am happy with the system.

Running in 1440x900 on a 1gigddr2/am2 4200+/geforce7600gt I am hoping one of you wiser sorts would be able to direct me in the way of some decent games available for Linux.

I Synaptic searched by using the search terms "Open GL" and was able to obtain some very entry level games and other misc stuff that was pretty to look at, but I'd really like to see some stress or at least something that can utelise this system running in Linux.

See its all very appealing to me yet, As I have never even been able to get Linux to run Tux Racer, yet alone work pretty much up to par as a whole.

Thanks in advance,
Tony.

---

### Post by xopher on 2006-12-15
> I am hoping one of you wiser sorts would be able to direct me in the way of some decent games available for Linux.

Well there is Doom3 and Quake4, which both should be able to stress your system -- at least more than tuxracer or frozenbubble ;)

These aren't free though..

People have run different versions of 3Dmark on linux (via wine) too, this might be something worth looking into too..

---

### Post by yabbadabbadont on 2006-12-15
Just install all the dev tools and then rebuild glibc and gcc from source...  That will stress your hardware.  ;)

---

### Post by xopher on 2006-12-15
> Just install all the dev tools and then rebuild glibc and gcc from source... That will stress your hardware. 

That won't stress the GPU, so is won't show you the big picture..

But for the CPU, compiling will do the trick just fine yeah ;) And -- there's always **superpi**. ([http://www.ubuntuforums.org/showthread.php?t=60264]("http://www.ubuntuforums.org/showthread.php?t=60264"))

---

### Post by yabbadabbadont on 2006-12-15
> **xopher said:**
> That won't stress the GPU, so is won't show you the big picture..

But for the CPU, compiling will do the trick just fine yeah ;) And -- there's always **superpi**. ([http://www.ubuntuforums.org/showthread.php?t=60264]("http://www.ubuntuforums.org/showthread.php?t=60264"))

I didn't think of the video card... oops.  The rebuild would stress the CPU, memory, and disk drive.  (All things I've seen fail while helping people out in the Gentoo forums ;))

---

### Post by xopher on 2006-12-15
> All things I've seen fail while helping people out in the Gentoo forums 

You mean fail, as in hardware failure? :) I don't understand why they are so eager to torture their systems that much..

---

### Post by yabbadabbadont on 2006-12-15
> **xopher said:**
> You mean fail, as in hardware failure? :) I don't understand why they are so eager to torture their systems that much..

Yes, hardware failures.  It doesn't really torture the system, it just exposes the already existing problems with the hardware that other distributions fail to find.  (which usually show up as random lockups in games)  I wiped Ubuntu last night and restored my Gentoo backups.  I was getting the shakes from "Gentoo withdrawal" after two months of using Ubuntu.  :lol:

Now I'll probably install Edgy into the free space on my second harddrive.  (or maybe Feisty if the repos already exist)

---

### Post by xopher on 2006-12-15
Feisty repos do exist, so that's probably what you'll choose ;)

I've had nothing but problems with gentoo every time I've tried installing it, but I still keep telling myself I need to try it out some day. So, some day I will. When, is a question no one knows the answer to ..

Sorry for going a bit off-topic.

---

### Post by yabbadabbadont on 2006-12-15
> **xopher said:**
> Feisty repos do exist, so that's probably what you'll choose ;)

I've had nothing but problems with gentoo every time I've tried installing it, but I still keep telling myself I need to try it out some day. So, some day I will. When, is a question no one knows the answer to ..

Sorry for going a bit off-topic.

Always do a manual stage3 installation by following (exactly) the instructions in the installation handbook.  (Read twice, follow once.  :D)  Using the GLI (gentoo linux installer) is a good way to loose all the partitions on your drive...  even the ones you told it to leave alone.  (yes, really)  :roll:  If you aren't comfortable manually configuring your kernel, use the genkernel method as it will produce a kernel setup similar to that used by Ubuntu.  Most importantly, *stick with the stable packages*.  Only unmask an unstable package if you really, really, need it.  (or have used Gentoo for multiple years and aren't afraid to break things ((like me)))

I also apologize for going off-topic.  (but installing Gentoo will stress your system too ;))

---

