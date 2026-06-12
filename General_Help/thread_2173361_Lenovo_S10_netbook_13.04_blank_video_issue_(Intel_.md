---
title: "Lenovo S10 netbook 13.04 blank video issue (Intel 945GMS Express). 12.04 LTS works."
date: 2013-09-09
forum: General Help
---

### Post by RGshXxh on 2013-09-09
Hello there,

I am having difficulties getting Ubuntu 13.04 to work with my 6-years old Lenovo S10 netbook. LiveCD worked well, if I do a lspci -k, I can see the i195 module was loaded automatically. But after I installed to HDD, I was greeted with a blank screen after the grub loader and after the HDD led stopped blinking (should be at the login screen now). Backlight was on, so it was not pitch black on the screen.

I did some research and tried different kernel options. The one that works is "nomodeset" - this guarantees a working login and desktop, but using a funny resolution (native resolution is 1024x600) and 0.0 Hz refresh rate.

Also tried to set kernel option "i915 modeset=1", this gave me about 40% success rate.... I have to pray for a good boot each time, which is really annoying (have to hard-shutdown if I see blank screen). But if this worked, everything (resolution and refresh rate, etc) works well as it should be.

Then I tried to use 12.04 LTS and it just worked every time without me hacking anything...

I suspect the it might be a kernel issue, but if you have any insight into this please let me know!

Thanks for your help.

---

### Post by mörgæs on 2013-09-09
Hi, welcome to the fora.

How does it work in a fresh install of the development version (13.10)?

---

### Post by jrda on 2013-11-28
Do you already fixed your Problem?

---

