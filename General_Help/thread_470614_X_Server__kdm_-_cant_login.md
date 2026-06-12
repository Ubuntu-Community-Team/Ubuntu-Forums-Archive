---
title: "X Server / kdm - cant login"
date: 2007-06-11
forum: General Help
---

### Post by rupy on 2007-06-11
Hi guys,

My system was working hundreds (running Feisty with 2.6.20-15-generic). I changed a few things, namely upgraded the kernel to 2.6.20-16-generic and set the font size to 120dpi (doubt this is the cause), and now when I login it takes me in, shows the mouse with a black screen for 2 seconds then seems to crash and take me back to the login screen.

I've checked the x-server logs and don't see anything really helpful, the kdm logs also show nothing particularly useful, except;
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

I've tried logging in with basic xorg.conf file, setting the res down and using vesa/nv driver however to no avail.

I was seeing weird errors about wfb module too but those seem to have disappeared? Also I was seeing ACPI warnings so I disabled it and booted in but it made no difference.

---

### Post by renzokuken on 2007-06-11
as far as i remember, when you upgrade/change the kernel you have to install the nvidia driver again.

i.e. each kernel requires its own install of the nvidia driver, even though they share the xorg.conf.

---

### Post by Naegling23 on 2007-06-11
I second the last comment.  I noticed the kernal upgrade yesterday, and figured I would be doing this today.

The best advice I can give you is to log in using the safe mode/command line.  once logged in, download and run envy (instructions can be found on the website, just google something like envy linux, and it should be up near the top of the list(sorry I cant provide a link, im at work right now).  I recommend keeping envy on your system, that way, when this happens in the future, all you have to do is log into the command line, type envy, restart x, and your done.

Its an annoying problem, and not a fun one, but once you've done it, you realize that its not really a big deal anymore.

---

### Post by renzokuken on 2007-06-11
envy is available at [www.albertomilone.com](www.albertomilone.com)
boot into your old kernel and download it with the gui and install it there

reboot and enter the new kernel which has no graphics......when it fails or whatever, press Ctrl+Alt+F1 to get to a terminal, login and as Naegling says, just run

```
envy
```

---

### Post by rupy on 2007-06-11
Cool, thanks guys. Gonna give this a shot.

BTW. Isnt this weird though, because I cant even boot in with the vesa/nv driver?

---

### Post by rupy on 2007-06-11
Finally managaed to fix it by poking around and reverting back to the old kernel. 

Bleh, Kernel upgrades suck.

Thanks for the tip about Envy, gonna grab it now now.

---

