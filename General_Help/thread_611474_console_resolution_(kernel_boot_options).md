---
title: "console resolution (kernel boot options)"
date: 2007-11-13
forum: General Help
---

### Post by Yakov Hrebtov on 2007-11-13
I've just installed 7.10-server on my test box. 
I want to have console with higher resolution when by default. What kernel boot option I have to use to change the resolution? What values I can assing to that option? How could I get a full list of available video modes and corresponding values?

thanks in advance

---

### Post by prodezigner on 2007-11-13
Well... this isn't an expert opinion, but most servers are headless, meaning no KVM (Keyboard/Video/Mouse) hooked up. If you SSH into your box with a program like Putty and go to fullscreen in it, it looks MUCH better. My server is headless with only two cords (AC and CAT5), eventually I'll get around to dumping another NIC card in and setting it up for something else other than file sharing on a home network.

Like I said, not an expert opinion, but a suggestion.

---

### Post by pxwpxw on 2007-11-13
> **Yakov Hrebtov said:**
> I've just installed 7.10-server on my test box. 
I want to have console with higher resolution when by default. What kernel boot option I have to use to change the resolution? What values I can assing to that option? How could I get a full list of available video modes and corresponding values?

thanks in advance

add the VESA mode to your kernel options

I use:

 vga=773

That gets 1024x768, google VESA modes for other resolutions.

---

### Post by Yakov Hrebtov on 2007-11-13
> **pxwpxw said:**
> 
 vga=773
That gets 1024x768, google VESA modes for other resolutions.

Seems I was hurried, when marked thread as solved...
I tryed a couple of vesa modes (vga=773, vga=771), but did not succeed. All of them causing just black screen. System goes to normal boot, but screen remains black.

Am I missing something?
May be framebuffer support is disabled in ubuntu's server kernel?

Thanks in advance.

---

### Post by pxwpxw on 2007-11-14
> **Yakov Hrebtov said:**
> Seems I was hurried, when marked thread as solved...
I tryed a couple of vesa modes (vga=773, vga=771), but did not succeed. All of them causing just black screen. System goes to normal boot, but screen remains black.

Am I missing something?
May be framebuffer support is disabled in ubuntu's server kernel?

Thanks in advance.

I did have that blank screen problem in an i386 ubuntu 710. It was missing 
modules

vesafb
fbcon

I think, I will check.

Thats right, 
modprobe vesafb
modprobe fbcon

admax@ubuntu:~$ lsmod | grep fb
fbcon                  41760  71 
tileblit                3584  1 fbcon
font                    9344  1 fbcon
bitblit                 6912  1 fbcon
vesafb                  9092  1 
admax@ubuntu:~$ 

Add them to /etc/modules, or if you want to see earlier startup screen text, add to /etc/initramfs-tools/modules and update-initramfs

This is on xubuntu710 on an Apple MacBook (intel).

---

### Post by Yakov Hrebtov on 2007-11-15
> **pxwpxw said:**
> 
modprobe vesafb
modprobe fbcon

<skip>

Add them to /etc/modules, or if you want to see earlier startup screen text, add to /etc/initramfs-tools/modules and update-initramfs

This is on xubuntu710 on an Apple MacBook (intel).
Now it becomes more clear to me.
This works when loading modules via /etc/modules or manualy, but does not work on initrd level.

I've updated initrd as you suggested. Screen remains black.
Using ssh session I found that vesafb module is not in loaded modules list. Just fbcon...

manual `modprobe vesafb` helps.

So, on some reason vesafb does not start with initrd...

Thank you for your help.

---

### Post by pxwpxw on 2007-11-15
> **Yakov Hrebtov said:**
> Now it becomes more clear to me.
This works when loading modules via /etc/modules or manualy, but does not work on initrd level.

I've updated initrd as you suggested. Screen remains black.
Using ssh session I found that vesafb module is not in loaded modules list. Just fbcon...

manual `modprobe vesafb` helps.

So, on some reason vesafb does not start with initrd...

Thank you for your help.

I just rechecked, and it was ubuntu704 that i ran update-initramfs - that worked, but now I have upgraded to 710, and now I get the same result as you - the update-initramfs runs but does not fix the console. The modules in /etc/modules works ok.
Don't know why, I will have another look.

Rechecking, found that I had kept the /etc/modules entry for vesafb, and in fact the update-initramfs does not get vesafb, so it was irrelevant. So /etc/modules is the best can do for now, starts showing text in the console when init gets started.

---

