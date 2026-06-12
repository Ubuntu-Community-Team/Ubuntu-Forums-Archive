---
title: "Ubuntu randomly suspends when not idle"
date: 2008-03-21
forum: General Help
---

### Post by accepttheownage on 2008-03-21
While logged in and using my laptop Ubuntu sometimes randomly starts suspending, as if I clicked suspend or pressed my sleep button. It last happened while chatting to someone with my webcam through MSN running in a Windows XP virtual machine (VMWare Workstation). I use a virtual machine because my webcam isn't supported yet in Linux. Anyway, in the middle of a chat it suddenly decided it was time to suspend, even though Ubuntu did not think it was idle (the screen would have turned off before suspending) it decided to suspend anyway. Any reason as to why this behavior would occur? Is there any way to fix this besides turning off suspend completely?
Another problem I have is that as soon as Ubuntu wakes up from sleep it immediately hibernates. It ONLY does this when Ubuntu suspends after being idle, NOT when I suspend it myself. Turning off hibernate helps, but it instead gives me an error upon waking up telling me that hibernate has failed. Either way this is also unacceptable behavior.
My laptop is an Asus C90S

---

### Post by cmnorton on 2008-03-21
Try to get hold of your laptop's hardware specifications. Asus is pretty good about keeping documentation like that on their web site. All I can advice you to do is check your bios settings. You would have to rely on whatever help/explanation is available in the bios setting program, which is not much.

Also, I would set your laptop never to idle after so many minutes.

How much memory is in this laptop, and do you have Ubuntu or XUbuntu installed?

My Acer Travelmate 630 did tend to turn to cement under a daily production load, email, editor and terminal emulation running, and so on. I eventually boosted the RAM to the max allowed, 1GB.

---

### Post by accepttheownage on 2008-03-21
Bios settings are okay, and I've never had this problem before in WIndows XP or Vista. Actually, I don't think I've ever had this problem in Ubuntu before either, it has just recently started happening. I have a feeling it has something to do with VMWare. I have 2gb RAM in the laptop, a nVidia 8600m GT video card, Intel 4965AGN card, and an Intel Core 2 Duo 6600 desktop processor.

---

### Post by cmnorton on 2008-03-22
Definitely look in your logs and see if something shows up.

---

