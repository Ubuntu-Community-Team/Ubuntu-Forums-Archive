---
title: "Why do I have to unmount a USB storage device before I remove it?"
date: 2008-02-14
forum: General Help
---

### Post by charlescarroll1 on 2008-02-14
So I noticed that whenever I unplug a USB storage device, for example, my cell phone or MP3 player, I get a message saying that I must unmount the device before I remove it. 

So I began to unmount my storage devices before I removed them, and when I wanted to plug them back in, they wouldn't show up on my desktop.  

Why is it necessary?

---

### Post by charlescarroll1 on 2008-02-14
I noticed that when I plug it back in, it shows up on my desktop now (weird).

---

### Post by lisati on 2008-02-14
> **charlescarroll1 said:**
> So I noticed that whenever I unplug a USB storage device, for example, my cell phone or MP3 player, I get a message saying that I must unmount the device before I remove it. 

So I began to unmount my storage devices before I removed them, and when I wanted to plug them back in, they wouldn't show up on my desktop.  

Why is it necessary?

It is usually necessary to unmount a device for one of two reasons: If you have copied data to the device, unmounting the device will make sure that all the data has been written to the device, and isn't just sitting in a cache or buffer somewhere in RAM. Unmounting will also help make sure that your computer doesn't try to access it when it's not actually there. Both these reasons apply not just to Linux but to other OSes as well - Windows has its "Safely remove hardware" option.

---

### Post by nutz on 2008-02-15
Same issue. I unmounted it properly but now when I plug it in it doesn't come up like it did before...

Rythmbox opens up but the icons for the mp3 player itself do not show up on the desktop.

---

