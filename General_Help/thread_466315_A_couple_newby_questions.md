---
title: "A couple newby questions"
date: 2007-06-06
forum: General Help
---

### Post by jibber_sc on 2007-06-06
Hi, I just installed Feisty and I have a couple petty questions.

1. How do I move a bunch of files to a folder that requires root permission to access?
I know I can use the terminal, but it would take too long to type the names of the files.
I don't want to long in as root 'cuz that takes too long too.
Can I open a window as root? (i.e. what is the command to open a window)

2. How do I get rid of the icons of the partitions of my Windows XP partition?
I still want it in my "Places" menu, but not on the desktop.
When I try to delete it, it tells me I can't delete it but I can unmount the partitions, which i don't want to do, of course.

Lastly, what is the font that Windows XP uses? I want to see a familiar font every time I use Ubuntu.

Thanx in advance :D

---

### Post by jfinkels on 2007-06-06
> **jibber_sc said:**
> Hi, I just installed Feisty and I have a couple petty questions.

1. How do I move a bunch of files to a folder that requires root permission to access?
I know I can use the terminal, but it would take too long to type the names of the files.
I don't want to long in as root 'cuz that takes too long too.
Can I open a window as root? (i.e. what is the command to open a window)
Type the following in the terminal:```
gksudo nautilus
```

> 
2. How do I get rid of the icons of the partitions of my Windows XP partition?
I still want it in my "Places" menu, but not on the desktop.
When I try to delete it, it tells me I can't delete it but I can unmount the partitions, which i don't want to do, of course.

Press alt+F2, type ```
gconf-editor
``` and press enter. On the left-hand side, go to "apps > nautilus > desktop" and then turn off the check box next to "volumes_visible".
> 
Lastly, what is the font that Windows XP uses? I want to see a familiar font every time I use Ubuntu.

Thanx in advance :D
I don't know, but you may have trouble with that...Microsoft uses proprietary fonts, I think, so we may not be allowed to use them...

---

### Post by jibber_sc on 2007-06-06
Forgot one question:

I have two sets of options for booting Ubuntu in grub. They both boot Ubuntu the same way. Here is a section of /boot/grub/menu.lst:

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2e70bd71-c064-4ffc-b7f4-61c67608e704 ro quiet splash acpi=force
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2e70bd71-c064-4ffc-b7f4-61c67608e704 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2e70bd71-c064-4ffc-b7f4-61c67608e704 ro quiet splash acpi=force
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2e70bd71-c064-4ffc-b7f4-61c67608e704 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Is this a bug? How do I get rid of one option? Can I just delete from menu.lst?

---

### Post by jfinkels on 2007-06-06
> **jibber_sc said:**
> Forgot one question:

I have two sets of options for booting Ubuntu in grub. They both boot Ubuntu the same way. Here is a section of /boot/grub/menu.lst:


Is this a bug? How do I get rid of one option? Can I just delete from menu.lst?

This is not a bug, and they only *appear* to boot the same way. Each of those entries boots a different kernel (the kernel is the base of the operating system, which communicates with your hardware below it and software above it). One is 2.6.20-15, one is 2.6.20-16. You can hide them if you want like this:

Type the following in the terminal:
```
gksudo gedit /boot/grub/menu.lst
```
Change your /boot/grub/menu.lst to look like this, with "#" symbols at the beginning of each line of the section you want to remove from your boot list:
```

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-16-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=2e70bd71-c064-4ffc-b7f4-61c67608e704 ro quiet splash acpi=force
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=2e70bd71-c064-4ffc-b7f4-61c67608e704 ro single
initrd /boot/initrd.img-2.6.20-16-generic

#title Ubuntu, kernel 2.6.20-15-generic
#root (hd0,2)
#kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=2e70bd71-c064-4ffc-b7f4-61c67608e704 ro quiet splash acpi=force
#initrd /boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root (hd0,2)
#kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=2e70bd71-c064-4ffc-b7f4-61c67608e704 ro single
#initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST  

```

Here I have left the most recent kernel, the most recent kernel's recovery mode, and the memtest86+ entry.

---

### Post by merlinus on 2007-06-06
System/Administration/Synaptic Package Manager.

Search for 

msttcorefonts

This will install the basic M$ fonts (e.g. arial, georgia, verdana).

-merlin

---

### Post by jfinkels on 2007-06-06
> **merlinus said:**
> System/Administration/Synaptic Package Manager.

Search for 

msttcorefonts

This will install the basic M$ fonts (e.g. arial, georgia, verdana).

-merlin

Oh. 

*shrugs* I prefer Linux fonts!

---

### Post by jibber_sc on 2007-06-06
> **jfinkels said:**
> 
Press alt+F2, type ```
gconf-editor
``` and press enter. On the left-hand side, go to "apps > nautilus > desktop" and then turn off the check box next to "volumes_visible".


Thanx jfinkels that was a fast reply. And now I know about the Configuration Editor, too.

What do I need the older kernel for? Is it like a backup in case I mess up the kernel?

> System/Administration/Synaptic Package Manager.

Search for

msttcorefonts

This will install the basic M$ fonts (e.g. arial, georgia, verdana).

-merlin

I have that already, but what I mean is what specific font is used for icons and text and such?

---

### Post by merlinus on 2007-06-06
System/Preferences/Font

You can change anything you like.

-merlin

---

### Post by jfinkels on 2007-06-06
> **jibber_sc said:**
> Thanx jfinkels that was a fast reply. And now I know about the Configuration Editor, too.

What do I need the older kernel for? Is it like a backup in case I mess up the kernel?


Sometimes, when the update manager proposes updates for you to install, it will propose a kernel update (the package will be something like "linux-image-generic"). The default Feisty kernel is 2.6.20-15, but an update a few weeks ago provided this new, updated kernel, 2.6.20-15. I don't know the reason why we keep the older kernel. Perhaps it is in case there's some huge flaw in the new kernel (but then, they would just release a newer version, right?). Perhaps it is because the newer kernel might cause some issues with drivers or other software, so we have an older kernel to roll back to. Perhaps it is because in the Linux world (as opposed to the Windows world), the user decides what happens to his or her computer, so it's up to you to remove it if you feel that's necessary. I don't know. :D

---

### Post by tk03759 on 2007-06-07
> **jibber_sc said:**
> 
I have that already, but what I mean is what specific font is used for icons and text and such?

XP uses a combination of "Trebucket MS", "Microsoft Sans Serif", and "Tahoma". Icons in particular use "Tahoma," the title bar uses "Trebucket MS," menu text is "Tahoma," and message boxes are "MS Sans Serif."

---

