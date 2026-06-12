---
title: "desktop stuttering/periodicly freezing, help please!"
date: 2007-07-11
forum: General Help
---

### Post by sockmonkee on 2007-07-11
The problem started yesterday after I upgraded my old CRT to a new samsung 226bw lcd screen. 
I've been running Kubuntu 7.04 on an AMD 2400+ with 768MB ram and nvidia card since its was released and everything has been working perfectly until now. 

The problem is that even before I login the mouse seems to move fine for about 1 second and then freeze for about I guess 1/4 second and then repeat perfectly periodically and its driving me nuts!
after logging in if I repeat a key in console I see the same pause, and the same thing when playing video but strangely the sound is unaffected. I tried switching back to the crt but the problem remains.

I have tried running top without finding anything ( but then I'm not 100% sure what I'm looking for) and looking at KDE system guard I can see that the CPU Load is rapidly oscillating and there is also a pattern on the average load, while memory is constant ( but physical memory is 98% full, about 30% application, 30% buf and 30% cached) and swap is completely empty.

 I tried switching back to the crt but the problem remains. the only thing that fixes the problem is booting in recovery mode, so if someone could just tell me what recovery mode does (or does not) do, that would already help a lot.

---

### Post by sockmonkee on 2007-07-11
ok, problem goes away when i add acpi=off in grub? what does this mean?

---

