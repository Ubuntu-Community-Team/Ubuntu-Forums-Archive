---
title: "Kernel Panic-Not Syncing.” Fatal exception in interrupt"
date: 2008-01-20
forum: General Help
---

### Post by irv on 2008-01-20
On my laptop I have been running a duel boot with Ubuntu 7.10 and XP. My system has been running with out a flaw for a long time. But yesterday it just shut off. Now I can boot into either OS's. All I get is a “Kernel Panic-Not Syncing.” Fatal exception in interrupt” error. The only way I can get it going again is to do a repair on the XP install. It then boot into Windows and Ubuntu, but then it shut off by itself and does the same thing. I have repaired XP twice now but this does not fix the problem. I am wondering if my hard drive or CPU or motherboard is going out. Does any one have any thoughts on this?
Oh yes, It won't boot off the live CD either, I get the same error.
Thanks

---

### Post by aphirst on 2008-01-20
This would strike me as a hardware error. It's as if the computer has just gone "hang on, where's the hard drive gone!?"

This may well not be the case, but the only way you could easily find out would be to do a mass backup jobbie from a live cd, then a complete reinstall (i.e. blank the hard drive).

On closer inspection, you mention that the same error occurs from a livecd. Hmm. It may be something common to an off-disk boot and an off-disc boot: the motherboard (or connected peripherals). Check the wiring, give the whole thing a dust with an anti-static brush or even better, compressed air. Vacuum the case just to be sure. Connect the drives/ram to other slots. Hell, even replace the cpu heatsink paste. Try booting from someone else's hard drive on your machine.

If that fails, get a new motherboard (or new ram, if that's what's broken).

---

### Post by irv on 2008-01-20
Well I started to pull and push. I pull all the memory out and pushed back in to make sure it was seating. I then removed my cpu fan and blew it out. Re-greased it and put it back in the laptop. I am not 100% sure but it might not have been turning on. But after reinstalling it, it is working now. After all this it booted up. I have turn it off and on again several times and it seems to be working. I would like to give it a few days to see if it continues to work. But I feel the problem might be solved.

---

### Post by irv on 2008-01-21
I was wrong, I locked up while scrolling with the mouse. I had no choice but to power down. When I tried to start back up it gave me the message “Switched to high resolution mode on CPU0”. At that point it would not boot. I pulled the memory again and re-seated it again. Then the laptop booted again. In fact I am writing this on it right now. I am not sure what is going on. Is it possible my memory is going bad. I always thought memory was either good or bad and not flaky.

---

### Post by irv on 2008-01-22
It died again, This time I think it a goner. It won't even boot from HD or CD. It starts to boot from the CD but just stops when, I believe it is trying to read the HD. My gut feeling is my HD crashed. My next step is to try a new HD. I hope this is all it is.

---

### Post by irv on 2008-02-01
OK, it wasn't the hard drive, It was the memory.
I thought I would just update this post so others might see what problem I was having and what I found out. I had another tech look at the laptop, and he thought it might be something on the motherboard. This was just somewhat true. The problem was one of the memory modules went bad. I have two chips in the laptop; one 256 and the other 512MB. Well, the 512 went bad, I removed it and just left the 256 in and the laptop would boot, but very slow. The RAM was “Buffalo” brand, and they were very good about replacing it. I called them and they gave me an RMA number to send the bad memory to them and they said they would exchange it at no cost. They have a life time guaranty on this memory. I only have one problem. Thinking it was the motherboard and the cost to replace it, I went out and bought a new laptop. Now I have two of them and I can only use one at a time. Right now I am on a Vista OS on the new laptop, because I am having some issues getting Ubuntu going. First I had problem with my Wireless, but I have it going now. But I have no sound and the video card is not recognized. Well that is another issue.
My plan is to use my old laptop for Ubuntu and my new one for windows. I can see one problem with using Ubuntu on new hardware, and that is drivers are going to be slow in getting support. Maybe as new versions of Ubuntu come out, the drivers will be supported right from the get-go.
Hope this post will help someone.
Irv

---

