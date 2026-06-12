---
title: "Restart puts BIOS in safe mode"
date: 2008-04-26
forum: General Help
---

### Post by blazerte on 2008-04-26
This problem started months ago when I upgraded my cpu from AMD Athlon 64 3200 to Athlon 64 X2 4800 and got an Ubuntu kernel oops. For more details:
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4554124]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4554124")

So I tried the newer kernel in Hardy Heron alphas and eventually switched to AMD64 version. But now my problem is that booting is fine, and shutting down is fine, but restart does NOT. Ubuntu shuts down, the cpu fan goes nuts, and I need to hold down the power button for the thing to die. 

When I then start up, the Bios is in safe mode and says "please resetting cpu frequency in cmos settings" (sic, that's exactly what it says). But the bios settings are all default, no over-clocking here.

Currently at Ubuntu 64AMD kernel 2.6.24-16. It's a Shuttle SN95G5 with the bios upgraded to SN95S1XD

My main OS on this PC is Debian, and all the Debian kernels run fine, including my own specially compiled ones like 2.6.25 and earlier; though they are 32bit.   

Any ideas?

---

### Post by rbmorse on 2008-04-27
I was going to suggest replacing the mobo battery, but if the Debian installation works the problem is almost certainly something else.

---

### Post by blazerte on 2008-04-27
Right, it's not a hardware problem if my Debian and Windoze installations are to be believed.

It's just something different that the Ubuntu Heron AMD64 kernel or modules are doing to reboot the PC. 

And it's something to do with that new AMD 64 X2 and the new bios I put into the Shuttle support it. 

So far everything else is working just fine.

---

### Post by danwood76 on 2008-04-27
Have you reset the CMOS settings after you updated the BIOS and installed you new CPU?
Stray settings can cause issues.

---

### Post by blazerte on 2008-04-27
> **danwood76 said:**
> Have you reset the CMOS settings after you updated the BIOS and installed you new CPU?
Stray settings can cause issues.

Oh yeah, all default.

But it must be some interaction between the bios and Ubuntu during restart. It's just that it only happens with Ubuntu's kernel and not Debian's or Windoze.

Now that Hardy Heron is out, I'm going to try a 32 bit live cd and see if that works. It didn't used to, thus my switch to the AMD64 version.

---

### Post by blazerte on 2008-04-27
Just tried the Heron 32 bit live.

Same problem. Works fine until I hit restart then hangs (in the bios?) on reboot with the fan racing away. Just like with the installed 64 bvit version. So 32-64 bits is not the problem.

---

