---
title: "Unable to boot custom kernels in Edgy"
date: 2006-11-13
forum: General Help
---

### Post by ico on 2006-11-13
Hi all,

After a series of positive experiences with past Ubuntu releases, I am stumped with the following problem.

Namely, I set out (as I have done in the past) to compile a custom rt kernel (with Ingo's patches). However, no matter which kernel I try to compile (even though I use make oldconfig), on my laptop which works fine with the generic Edgy kernel, all other kernels simply hang 5 seconds into the boot process (right around the time when the IDE stuff is being probed). I've followed Ubuntu kernel how-to to the letter ([http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)) and apart from the new options, most of which were either selected as module compiles or disabled (the preempt desktop or real-time being an exception), everything else is the same as Ubuntu's generic kernel, yet the thing simply hangs.

So, at this point I am wondering if anyone has any ideas why is this so?

Do I need to use gcc-3.4 to compile?

My laptop is M6807 with a KT800 motherboard (VIA). The kernel output is virtually the same between the two kernels, except that one hangs, as I mentioned, literally seconds into the boot process (right after assigning some IRQs and probing for IDE stuff, before the detection of the HD). I tried 2.6.17.7 + rt7 patch and 2.6.18.2 + rt7 patch, both of which patched with relative ease, but neither worked.

Any help would be greatly appreciated! If you need any files/config stuff in order to help me solve this riddle, please do not hesitate to contact me.

Best wishes,

Ico

---

### Post by deviant on 2006-12-03
I have the same problem. After installing a custom 2.6.19 kernel, the system hangs at boot time. It says "Uncompressing Linux .. " , and the hangs. 
Any sugestions anyone ?

---

### Post by Kikoolol on 2006-12-03
Hi guys !

It seems you are not the only one having this issue ! It's already being discussed in here : [http://www.ubuntuforums.org/showthread.php?t=310546]("http://www.ubuntuforums.org/showthread.php?t=310546") and here : [http://www.ubuntuforums.org/showthread.php?t=311393]("http://www.ubuntuforums.org/showthread.php?t=311393")

No solution found for now, but it seems that at least one person succeeded in booting the last kernel. Let's hope somebody will come with a solution :)

Kikoolol

---

