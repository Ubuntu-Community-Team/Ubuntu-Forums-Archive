---
title: "connecting two external monitors with Ubuntu 22.04"
date: 2024-10-03
forum: General Help
---

### Post by pierreillien on 2024-10-03
[]("https://askubuntu.com/posts/1528842/timeline")I know this question has been addressed several times but I can't  find the right answer to my problem -- sorry for posting again about  this.

 
I have a HP Elitebook with a a Mesa Intel GPU. The OS is Ubuntu 22.04.

 
I can plug one external monitor with the built-in HDMI port of the  laptop. This works. I want to plug a second HDMI monitor through one of  the USB-C port, with a USB-C/HDMI adaptor.

 
This used to work, and it suddenly stopped working, I have no idea why.

 
This is NOT a cable or adapter issue. They all work when tested separately.

 
What are the software solutions I should try?

 
Everything I read is about Nvidia, not Intel GPU.

 
Thanks!

---

### Post by guiverc on 2024-10-03
I'd explore when this issue first started occurring, and what change(s) were made in the **session BEFORE** the problem appeared.

I don't know how often you use your machine, how often you apply upgrades & security fixes; but if you can't recall making a change yourself, I'd explore system logs for update fixes.

eg.  some *many* weeks ago the HWE kernel stack for 22.04 switched from 6.5 to 6.8 kernel and thus your change maybe related to that for example; your logs will show when that change occurred and if that occurred at that time, the easy *workaround* maybe switching from the HWE kernel stack to GA, but before even doing that I'd reboot the machine & select an older kernel (*you may still have a 6.5 kernel installed*) and see if the problem occurs there.. If it doesn't, and only when you boot 6.8 kernels; you have at least something to work with...  This is said only as example; as I don't know what you're actually using (*you mention only 22.04, and you may be using the GA kernel stack thus this paragraph doesn't even apply*).

My 2c thought anyway.

---

