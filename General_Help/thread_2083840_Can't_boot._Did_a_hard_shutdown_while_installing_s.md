---
title: "Can't boot. Did a hard shutdown while installing software. RAM related?"
date: 2012-11-13
forum: General Help
---

### Post by Aaron Christianson on 2012-11-13
So, I tried to install KDE on 12.10. I was almost to the end of it, and I had already chosen my display manager (stuck with lightDM), and then I had to go somewhere for a few hours.

upon my return, the screen was black (pretty normal), but the machine wouldn't come back up. It was just blackness. The fan was still running, but no output of any kind. Couldn't get to the tty either. Did a hard shutdown and rebooted. It hung after the bootloader.

Did memtest, and it was fine for tests 1-6, but failed epicly on test 7. Tried to boot some live media, but they all hung when booting the kernel (after the boot loader). I did manage to get into an ubuntu live environment (kinda) by using parameters 'nomodesed' and 'acpi=off'

However, X wasn't really working. I could drop into a tty and do stuff, however. I deleted my Ubuntu partition with cfdisk, but that didn't really seem to do anything (it's on a non-mission-critical machine, so it wasn't a big deal).

Again, this machine isn't really a big deal, but I'd rather have it working than not.

It's a dell inspiron duo, by the way. Fun for seeing how the Unity touch UI is coming along. I was going to try KDE Plasma Active, but apparently that's a no-go.

---

### Post by rai4shu2 on 2012-11-13
If you see a memtest failure, you need to either fix that in the BIOS settings or get some serious hardware analysis (although hardware troubleshooters will generally just tell you to replace the hardware component that's going bad).

---

### Post by Aaron Christianson on 2012-11-13
Alright, went into the bios. Couldn't see anything to do there, but I did hit "load optimal settings" or something. Didn't change anything.

What kind of "serious hardware analysis" did you have in mind? If it's just RAM, I'll buy more, no problem, but I don't really even know what's broken.

Might be nice if I could install packages from universe without worrying that trying to do so will destroy my hardware.

---

### Post by rai4shu2 on 2012-11-13
Well, you take your machine to professionals and they try out replacement components until they get it working. And then they offer to sell you components. That's basically how hardware troubleshooting works.

---

### Post by Aaron Christianson on 2012-11-13
And I presume this costs a lot of money, correct?

Anyway, thanks for you're help. I'll see what I can do. Should this thread be marked as 'solved'?  I still have the problem, but it looks like nothing Ubuntu-related is going to fix it.

---

### Post by audiomick on 2012-11-13
I also believe that if memtest shows any errors at all, then your RAM has a problem. According to everything I have seen, it should always turn up zero errors if the RAM is ok.

The first thing to try is to simply unplug the RAM and then plug it back in. There is a chance that it is just not seated properly, or that the contacts are perhaps a little corroded. Then run memtest again. 

If you have more than one stick of RAM, then remove one, or all but one, and run memtest again. Keep doing this until you have isolated which RAM stick has the problem, and just remove it until you can get a replacement. Your system will most likely run on less RAM, and will find and use additional RAM when you install it.

---

