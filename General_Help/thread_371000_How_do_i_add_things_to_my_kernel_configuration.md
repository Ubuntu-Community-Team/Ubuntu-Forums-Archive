---
title: "How do i add things to my kernel configuration"
date: 2007-02-26
forum: General Help
---

### Post by Dcode^ on 2007-02-26
According to this [guide]("http://www.thinkwiki.org/wiki/How_to_make_use_of_Graphics_Chips_Power_Management_features#Power_saving_with_a_framebuffer_console"). I need to enable CONFIG_FB_RADEON to my kernel configuration. I need to add this so i can enable dynamic clocks on my Thinkpad T41's mobility 9000 radeon card for power saving features. I haven't got a clue how to do this or where to begin to start. Can someone please help me?

---

### Post by Dcode^ on 2007-02-26
Forgot to mention i am running Ubuntu 6.10 with the 2.6.17-11-generic kernel.

---

### Post by llamakc on 2007-02-26
Yes. You need to recompile the kernel. You can start by grabbing the kernel source from the repos.

---

### Post by ~LoKe on 2007-02-26
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by Dcode^ on 2007-02-27
Thanks for the replies.

This guide explains how to recompile the kernel. I dont really want to do this, all i want to do is enable CONFIG_FB_RADEON to the current kernel config. Can this be achived without having to recompile the kernel itself?

---

### Post by ~LoKe on 2007-02-27
> **Dcode^ said:**
> Thanks for the replies.

This guide explains how to recompile the kernel. I dont really want to do this, all i want to do is enable CONFIG_FB_RADEON to the current kernel config. Can this be achived without having to recompile the kernel itself?

In order for something to be added to the kernel, it must be recompiled.

---

### Post by hikaricore on 2007-02-27
> **Dcode^ said:**
> Thanks for the replies.

This guide explains how to recompile the kernel. I dont really want to do this, all i want to do is enable CONFIG_FB_RADEON to the current kernel config. Can this be achived without having to recompile the kernel itself?

I'm not an expert at the setting you're looking into, but I do believe you still need to recompile the kernel to achieve this even if you don't really want to.

It's kinda like saying "I want toast" then refusing to go to the store and buy bread.

---

### Post by Dcode^ on 2007-02-27
Ok, i was hoping i would be able to get away with it without having to recompile but i guess not. I'll see what i can get out of this guide.

Thanks for the heads up.

---

