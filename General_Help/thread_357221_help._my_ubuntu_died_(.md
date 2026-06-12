---
title: "help. my ubuntu died :("
date: 2007-02-09
forum: General Help
---

### Post by noobuntoo on 2007-02-09
i was running feisty fawn herd 2. After a recent update, when i rebooted it refused to load ubuntu. The progress meter on the splash screen moves a hair and then black screen.

I also have grub, unfortunately i have it set to only display the latest kernel. I'd like to change this so that i can at least run an older kernel and see if that lets me load ubuntu. How do i do this if ubuntu won't load? I have a live cd of ubuntu 6.06 that i can boot from, but how do i edit the files on my hard drive?

Tried running ubuntu in recovery mode. After scrolling through a bunch of stuff it loaded, i get this over and over

hde: dma_timer_expiry dma status == 0x24
hde: DMA interrupt recovery
hde: lost interrupt

Can anyone help me figure out whats going on? or at least how to run an older kernel so ubuntu will load and i have access to my hard drive again?

---

### Post by igknighted on 2007-02-09
Boot into grub, then arrow to the latest kernel in the menu, then hit 'e'.  Now arrow to the kernel line and hit 'e' again, edit the path to show the new kernel (if you erase, then <tab> will autocomplete and give you options if you don't know the name of it).  Do likewise with the initrd file. then hit 'b' to boot and that should do it.

---

### Post by noobuntoo on 2007-02-09
ok i did that. Attempted to load other kernels without any success. Basically every old kernel i tried loaded the splash screen but the progress bar won't move at all no matter how long i wait. Did recovery mode with older kernels and i get the same dma_timer_expiry junk as before.

Has anyone had anything similar to this happen? Something that was updated broke my ubuntu. How do i fix this problem? I just want to be able to have ubuntu load and access my files.

I thought about reinstalling 6.06 from the live cd. Would that break anything or delete my files if i did that?

---

### Post by noobuntoo on 2007-02-09
*bump*

anyone know what the error means?

Is it possible for me to downgrade without losing my personal files?

---

### Post by arya6000 on 2007-02-09
I don't know if this case if for you or not, but just check it any ways.

Same thing happed to me I found out that if was my HDD data wire, I always changed HDDs thats why the wire started to tear, I also got to the loading screen then nothing happened, so if you change your HDD often check the wire.

---

