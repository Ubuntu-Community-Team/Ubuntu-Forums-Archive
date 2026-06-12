---
title: "X Server Dies Upon KDM"
date: 2007-01-16
forum: General Help
---

### Post by jlacroix on 2007-01-16
Hello everyone (again, I've been having alot of problems lately).

I installed a new Nvidia video card today and KDM dies on its first time loading. In my kdm.log I get this error:
```

Error loading keymap /var/lib/xkb/server-0.xkm

```
What the heck is that and how do I fix it? I have never had this error before so any assistance would be wonderful. :)

---

### Post by jlacroix on 2007-01-16
Anyone?



:(

---

### Post by der_joachim on 2007-01-17
The error does not seem Nvidia-related to me. What is the output of your /var/log/Xorg.0.log? Is your /etc/X11/xorg.conf configured for your nvidia card?

Additionally: which kernel are you running and have you installed the restricted modules? Note that the restricted modules for the 386 kernel will not work with the generic kernel.

---

### Post by jlacroix on 2007-01-17
I attached both files in the attachment.

I have kernel 2.6.19.2 installed, I compiled it so I could use nvidia-settings (I tried to install nvidia-settings from Adept but it wanted to remove nvidia-glx) and also for a speed boost. The platform is AMD64. Before I installed anything I purged nvidia-glx and I compiled the kernel for AMD64, and I also made sure to use the 64-bit version of the official nvidia driver. I also let nvidia make the xorg file during setup.

The problem started right after rebooting after installing the nvidia driver. If I press ALT+CTRL+Backspace, KDM reloads and everything runs perfect, but it always crashes to a black screen the first time KDM starts and the error I posted is the only one I could find.

I searched Google for almost an hour and alot of people had the same problem as me but they were using XGL or Beryl, which I'm not using. The fix for them was to recompile Beryl I think but I am not using Beryl at all.

From what I can tell, the nvidia driver is working perfectly, I traced the problem to the error I posted about the keyboard map, for some reason KDM doesn't like it and bails out the first time.

---

### Post by jlacroix on 2007-01-17
Bump.

---

