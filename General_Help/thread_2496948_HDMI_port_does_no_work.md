---
title: "HDMI port does no work"
date: 2024-04-18
forum: General Help
---

### Post by dalpets on 2024-04-18
I have a HDMI cable attached to my Ubuntu machine but it does not work. The same cable works on my Windows machine, but it does not work on 2 other linux machines.

Is there a way to get a hdmi/display port  to work with Ubuntu/Linux?

Thanks

---

### Post by TheFu on 2024-04-18
They have always "just worked" for me, but it is possible that the HDMI port used requires a specific CPU with an iGPU to get any signal.  
Is the HDMI port going into a standalone GPU or into the motherboard?
Which GPU driver is being used?
Did it ever work with any version of Ubuntu?  Does booting from an install flash drive and using *Try Ubuntu* mode work?

So many questions, but few answers.

**inxi -Gxxz** output would be useful and answer many questions, but please re-re-read the post and answer ALL questions clearly.

---

### Post by VMC on 2024-04-18
What does "Settings > Sound > Output" show. I had similar issue. Fixed by triggering Output.

---

