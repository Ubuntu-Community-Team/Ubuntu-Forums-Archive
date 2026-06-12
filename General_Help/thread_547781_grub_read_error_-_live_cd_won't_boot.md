---
title: "grub read error - live cd won't boot"
date: 2007-09-10
forum: General Help
---

### Post by crawdaddy on 2007-09-10
I've used Ubuntu for a bit.
Loved it and it seemed to work play well with my hardware for a while - till it broke grub.
Now I'm unable to reboot.
I get Grub read error.
When I try to use the Ubuntu live cd it gets as far as Ubuntu loader graphic, then a series of error messages - I/O error buffer... something something.
No other live cd variants will boot either.
I burnt a copy of Super Grub Disk, but that just returns a grub read error.
Any ideas.
I'm running Feisty fawn on a Pentium 4 system, 1GB mem, Nvidia video card.
That's about as detailed a system summary as I can manage at this minute.

---

### Post by jnorthr on 2007-09-10
do you get an error code for the grub read error ?
Have you changed any hardware recently ? Can you boot from a ms dos floppy ?

---

### Post by crawdaddy on 2007-09-10
I haven't installed any hardware.
Did a fairly routine software install in gnome (I thought).
The system locked up and wouldn't respond at all.
Had to force a shut down, and when I restarted I got -
Grub read error
No other error codes

I have been able to get a copy of knoppix live cd up and running.
When I go to mount my hdb it gives me an error.

Could not mount device.
The reported error was:
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
or too many mounted file systems

This isn't the first time something similar has happened to this system, but not to this extent.
I'm beginning to suspect flaky hardware.
What do you think?

---

### Post by jnorthr on 2007-09-13
Have to say that this all sounds really queer. It was working then after a reboot, it decided not to. Sounds like you really need some kinda hardware tester utility, say norton or maybe a grub memory test. If it's a flaky video or video ram that might give you look ups like this but grub read error sounds more like disk access gone wrong. Do you have a floppy drive you might try a dos boot disk in ?

When you boot do you ever see the msg 'grub 1.5' ? This is where grub is trying to reach the hardware after a lot of setup stuff in the first part of grub called grub 1.0 ?

---

