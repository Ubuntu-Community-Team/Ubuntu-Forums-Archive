---
title: "Green Lined Screen"
date: 2014-03-27
forum: General Help
---

### Post by Aaron_Florey on 2014-03-27
Our power went out for a day and after coming back, my server won't boot. It gets to the GRUB menu where i have to manually select the kernel to boot. Once i do that, it has a lined green screen, which i've never seen before. One time it stopped for enough time to read something like this on the last line – [ 1.132277] pci_root PNP0A08 :00 : host bridge window [mem 0xfed45000-0xffffffff]. I've tried recovery mode and an older kernel, both do the same thing.


This is on a HP Microserver N36L


Here is an image of what happens after the GRUB menu – [http://imgur.com/p7W0PVi](http://imgur.com/p7W0PVi)


Anyone have any ideas? Is it a hardware issue or is my ubuntu install borked?


Thanks

---

### Post by m-dw on 2014-03-27
It looks like a graphics driver issue - I had some problems with the Nvidia drivers a while back.  Can you use <Ctrl><alt><F1> to drop to a text console.  What I eventually did was remove all the graphics drivers completely and reinstall them.

---

### Post by Aaron_Florey on 2014-03-27
> **m-dw said:**
> It looks like a graphics driver issue - I had some problems with the Nvidia drivers a while back.  Can you use <Ctrl><alt><F1> to drop to a text console.  What I eventually did was remove all the graphics drivers completely and reinstall them.

It has integrated graphics, not sure what drivers that would need. But i tried to open the console and nothing happened. 

Not sure why Ubuntu would stop working randomly

---

### Post by m-dw on 2014-03-27
Well integrated graphics could be anything depending on what HP chose but nVidia would be unusual on a server platform.  If you can't drop to a console it sounds like something is stopping the system from starting properly.  Have you tried booting from a DVD/USB drive to rule out issues with hardware?  Maybe use a system rescue CD like UBCD?

The reason I thought it was graphics is that the display looks like lots of blurry text repeated over and over which is exactly what I saw on my monitor when the NVidia install failed following an upgrade to 13.04.

Also, if you don't have alternative media, have you tried booting into single user mode?

---

