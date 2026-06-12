---
title: "Does XGL/Compiz work on the AMD k7 kernel image?"
date: 2006-09-04
forum: General Help
---

### Post by user1397 on 2006-09-04
I installed xgl/compiz flawlessly with my i386 kernel.  It works perfectly on the i386 kernel.  Then i installed the k7 kernel, and booted to the k7 kernel.  Then I tried to start an xgl session but it didn't work.  

The first time I tried to do it, my desktop loaded fine, I had both panels on top and bottom, and my background was there, but none of the xgl /compiz effects were working, it seemed as if a normal session.


So I logged out, and tried to log back in a second time, but this time, my panels didn't load, I could only see the background.  So I pressed CTRL+ALT+Backspace to get myself out of something potentially harmful.  Then I logged into windows and that's where I am typing this now...:-k

---

### Post by David Corrales on 2006-09-04
I'm running it without problems on my K7 image. You probably forgot to add the restricted modules packages for the K7 kernel (which contain the propietary nvidia/ati drivers) :)

---

### Post by user1397 on 2006-09-04
> **David Corrales said:**
> I'm running it without problems on my K7 image. You probably forgot to add the restricted modules packages for the K7 kernel (which contain the propietary nvidia/ati drivers) :)oh i see...let me see if that works...

EDIT: yep, it worked, thanks!

---

### Post by mihaic on 2006-10-18
Hi guys,

  Can you please enumerate restricted modules packages for the K7 Kernel?

Thanks and have fun,
Mihai

---

### Post by user1397 on 2006-10-18
> **mihaic said:**
> Hi guys,

  Can you please enumerate restricted modules packages for the K7 Kernel?

Thanks and have fun,
Mihai
wwhat do you mean?  do you want to know the full name of the restricted modules package?  first we must know your kernel version.  (as in 2.6.15-23 or something like that)  just check in synaptic for your installed version.

---

### Post by mcduck on 2006-10-18
> **mihaic said:**
> Hi guys,

  Can you please enumerate restricted modules packages for the K7 Kernel?

Thanks and have fun,
Mihai

you shouldn't install a specific package version. If you do, when the kernel updates kernel modules don't..

Instead you should install a package called linux-k7. It's a metapackage thet always depends on the latest versions of all kernel-related files. So installing thet makes sure that you get updates for all needed files.

---

