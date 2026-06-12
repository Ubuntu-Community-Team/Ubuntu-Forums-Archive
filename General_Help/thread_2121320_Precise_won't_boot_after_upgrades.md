---
title: "Precise won't boot after upgrades"
date: 2013-03-01
forum: General Help
---

### Post by sgage on 2013-03-01
I just installed 12.04.2, and had it running nicely. I applied the pending upgrades, and can't get it to boot, not even "previous versions". What is going on? This is supposed to be a rock-solid LTS - I did not really expect this kind of nonsense.

Any suggestions?

---

### Post by tgalati4 on 2013-03-01
Many times installing a new distro, or upgrading a old distro will cause a hardware fault--typically a hard disk failure.  Writing ~5 GB of data in one session heats the heads and when they cool, they have problems reading--thus no boot.  Of course it could be a *regression*, something working and now, no longer working.  What previous versions are you talking about?  If you just installed 12.04.2, and you applied all updates, then it's possible that a kernel update also occured and that could cause a no boot situation.  When booting into a rescue kernel, hit esc or Alt-F1 to bring up the messages during boot.  What actually happens when you boot?

---

### Post by sgage on 2013-03-01
I did a clean install of Precise. It was working beautifully. I did the updates, and no joy. I'm sure it has to do with a kernel update, and the strange quantal backports. 

What actually happens when I boot is that after a bit of purple, the monitor goes black and tells me "no signal", and that's the end of that. I have work to do at the moment, but I will try the "rescue" mode at some point.

I really did not expect this from Precise.

---

### Post by tgalati4 on 2013-03-01
If you are running a proprietary graphics driver and upgraded the kernel, then video will often crash--this sounds like a possible cause.  Boot into rescue mode and there are some repair options available.  Proprietary drivers often need to recompile a module to hook into kernel, and if this isn't done properly, then you loose graphics.  Having spent many winters in the Granite State, I feel your pain.

---

### Post by sgage on 2013-03-01
Yes, I understand about proprietary drivers. I never even think about installing them until I'm all updated, have the latest kernel humming along, and am sure that all the proper headers are there. I've been at this a long time ;-)

It is rather wintry right now in the Granite State, but nothing can stop the March sun! :-)

I will do some more poking around as soon as I have some time...

---

