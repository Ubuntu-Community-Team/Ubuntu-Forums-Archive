---
title: "Change resolution in all terminals"
date: 2004-10-27
forum: General Help
---

### Post by neon on 2004-10-27
Hi all, I would like to change the horrible resolution of the terminals to a normal 1280x768. 
Any ideas? I'm newbie so I dont know much about compiling kernel, enabling framebuffer etc.

Thanks for your help

---

### Post by HungSquirrel on 2004-10-27
First off: I do NOT know if framebuffer support and fonts are enabled in the Ubuntu kernels.  We will have to wait for someone who knows more about that before trying this!

To enable a framebuffer, open up /boot/grub/menu.lst under sudo and look for the line that begins with 'kernel' that applies to the kernel you normally boot.  At the end of that line, append "vga=791" without the quotes, replacing 791 with the correct framebuffer (Grub supports either decimal or hex values here).  I don't know if there is a framebuffer that will support such a wide resolution, though...

I suggest you only add it to the kernel you boot and not to the recovery mode kernel.  ;)

Edit: You can get a widescreen res, it's just a pain in the rear.  If you really want to try, check out the first two posts of [this Gentoo thread](http://forums.gentoo.org/viewtopic.php?t=49036&postdays=0&postorder=asc&start=307).

Edit 2: 1024x768 16bpp (vga=0x317) works.  I also tried 1152x864 but it didn't work.

---

