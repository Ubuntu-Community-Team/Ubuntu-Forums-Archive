---
title: "Gutsy Gibbon Restart Problem"
date: 2007-12-04
forum: General Help
---

### Post by richardeng2005 on 2007-12-04
I have a Dimension 9200 Quad-Core Core 2 Duo with 3GB RAM that I purchased two months ago. I setup the PC to multiboot between Vista and Gutsy Gibbon. (I installed Vista first, and then Gutsy Gibbon.)

However, whenever I try to Restart Ubuntu, it hangs. The system would begin to shutdown, the progress bar would show completion of shutdown and then remain on the screen forever. It never gets to BIOS POST. I have to force a power off by pressing the power button for 6 seconds.

The interesting thing is, if I select Ubuntu Shutdown, no problem. It actually shuts down (powers off). So the problem is unique to Restart.

Has anyone else experienced this?

Richard

---

### Post by marpstar on 2007-12-04
Try updating the BIOS to your machine.  What does Vista do when you shutdown/reboot?

---

### Post by richardeng2005 on 2007-12-04
No, you don't understand. It *never* gets to the BIOS, so it's not a BIOS issue. The computer remains on the Ubuntu shutdown screen (with the expired progress bar), which means Ubuntu has hung.

Richard

---

### Post by marpstar on 2007-12-04
Is it happening in Windows also?

Just because it's not getting past a Ubuntu shutdown screen doesn't automatically rule out a motherboard issue. 

Try a BIOS upgrade, it's not going to hurt any... If that doesn't work, then there must be some program or service that's hanging upon shutdown.  Instead of telling Ubuntu to shutdown, try going to a terminal (Ctrl+Alt+F1) and typing 
```
sudo reboot
```

see if the hanging service throws any terminal errors when rebooting...

---

### Post by richardeng2005 on 2007-12-04
I installed the latest firmware from Dell (version 2.5.1). It didn't help.

I tried to look at the terminal output during reboot. The screen didn't last long but I managed to see something in the final line of output:

...nm_hal_deinit: libhal shutdown failed

I don't know if this is related to the hanging, but it's likely.

Richard

---

### Post by richardeng2005 on 2007-12-04
BTW, it's not happening in Windows. Vista restarts just fine.

If anybody cares to investigate, the Dell model I have is Dimension 9200 (DXP061). It originally came with BIOS version  2.5.0 (dated 5/24/2007). I upgraded to BIOS version 2.5.1 (dated 8/29/2007), the latest available BIOS.

I have a 2.4GHz Core 2 Quad Core Q6600 with 3GB of memory (667MHz) and NVIDIA GeForce 8600GT video card with 256MB of DDR3. I also have a 500GB SATA hard drive.

The hard drive has two primary partitions, one for Vista Home Premium and one for Ubuntu Gutsy Gibbon. I installed Vista first, so I'm using Ubuntu's multiboot loader.

My guess is, I won't be the only one to experience this problem.

Richard

---

### Post by simonfiction on 2007-12-28
Did you get anywhere with this? I'm experiencing exactly the same problem with my Dimension 9200.

-Si

---

### Post by Antkin on 2008-01-27
I've installed Dell A11 Bios on my Optiplex GX620 and Gutsy will not restart. Shut down works fine.

---

### Post by not_a_haxor on 2008-06-02
I'm also having the exact same problem. :( Shutdown works fine, but not reboot. It hangs after the Ubuntu shutdown status bar slides all the way to the end. My machine is a Dell Dimension 9200 Intel 6600 2.4 Ghz with 3 Gig Ram.
If anyone has a solution to this, it would be much appreciated.

Thanks!

---

