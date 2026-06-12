---
title: "compling and installing kernel: how do I tell w/ patches and config I have currently"
date: 2006-11-28
forum: General Help
---

### Post by akijikan on 2006-11-28
I'm updating to 2.6.18.3

I want to keep all my config and patches.

---

### Post by RAOF on 2006-11-28
make oldconfig should copy the config from /boot/config-2.6.whatever

As for patches, you'll need to get and apply them yourself.

---

### Post by akijikan on 2006-11-28
Yes, but how do I know what patches I have currently?

---

### Post by RAOF on 2006-11-28
You don't.  And (pretty much) can't.

Ok, you can remember what patches you applied to the last kernel you built.

Why do you want a new kernel anyway.  Why do you want to patch the kernel?

---

### Post by akijikan on 2006-11-28
I just want a new kernel because I need to remove all the bloat from the install kernel and if I'm doing that might as well be the latest.  I don't know if I need any patches.  I just installed Ubuntu so I haven't applied any patches, so unless there's anything already there I assumed I was okay.  The reason I ask is because I did once and lost my wifi.

---

### Post by RAOF on 2006-11-28
My advice: don't bother.  The standard kernel doesn't include any "bloat" - everything can be is built as a module, so if you don't use it, it doesn't use anything but a couple of Kb of harddrive space.

The time and effort required to actually build and maintain a custom kernel (even though it's an initial investment of a couple of hours, and some extra time here and there) just isn't worth it.  Use those extra hours to learn [Python](www.python.org) instead. :)

---

### Post by akijikan on 2006-11-28
sigh...why does everyone want to tell me what I want...you have piqued my interest though...what IDE would you recommend>

---

### Post by RAOF on 2006-11-28
Because you're asking for advice :).

If I can't persuade you against compiling your own kernel, then:
1) You don't have any patches you need to apply.
2) [https://help.ubuntu.com/community/forum/software/CustomKernel?highlight=%28kernel%29](https://help.ubuntu.com/community/forum/software/CustomKernel?highlight=%28kernel%29) if you don't want the latest kernel.
3) If you **do** want the latest kernel, do the same things as above, just from the "You can make menuconfig and remove the options you do not need." part.

---

### Post by akijikan on 2006-11-28
> **RAOF said:**
> Because you're asking for advice :).

If I can't persuade you against compiling your own kernel, then:
1) You don't have any patches you need to apply.
2) [https://help.ubuntu.com/community/forum/software/CustomKernel?highlight=%28kernel%29](https://help.ubuntu.com/community/forum/software/CustomKernel?highlight=%28kernel%29) if you don't want the latest kernel.
3) If you **do** want the latest kernel, do the same things as above, just from the "You can make menuconfig and remove the options you do not need." part.

Yes, but I was asking how to do something.  Thank you.  Do you have recommendation for a Python IDE?

---

### Post by RAOF on 2006-11-28
I actually use Emacs with python-mode.  That's pretty good.

Failing that, IDLE is the default python IDE, and is packaged as **idle** in Ubuntu.

---

### Post by akijikan on 2006-11-28
thank you very much!

---

