---
title: "nouveau screen resolution on text login?"
date: 2017-03-29
forum: General Help
---

### Post by mathog on 2017-03-29
Ubuntu 14.04 LTS 32 bit.

This machine has a text login (does not go directly to X11).  When it had the nvidia driver the text mode was fairly large.  After removing nvidia and installing nouveau it has changed to a very high resolution.  During the login the text is large while it goes through the BIOS, then also large during the early part of the OS loading, then it becomes small.

The transition from large to small is before the "loading essential drivers" line appears.  At that point the screen clears and the "loading essential drivers" appears in the small font at the top.

The display is an old high quality CRT which supports up to 2048 x 1536 - and that seems to be what nouveau is using. 

How does one tell nouveau to only go up to 1280x1024 (or whatever) when in text mode?

Thanks.

---

### Post by oldrocker99 on 2017-03-29
Here's how:[https://askubuntu.com/questions/173220/how-do-i-change-the-font-or-the-font-size-in-the-tty-console](https://askubuntu.com/questions/173220/how-do-i-change-the-font-or-the-font-size-in-the-tty-console).

---

### Post by Bashing-om on 2017-03-29
mathog; Hello;

My solution is to edit /etc/default/grub :
> 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

To tell grub not to use the resolution that bios passes . - removing the leading '#' character and substituting a suitable resolution
Pay attention to that warning !

What you want to do here is boot to the grub boot menu -> 'c' key for a command line in this environment and execute:
```

vbeinfo

```
IF the desired mode is known by grub, you may use it to make the edit to the grub config file.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by mathog on 2017-03-29
> **oldrocker99 said:**
> Here's how:[https://askubuntu.com/questions/173220/how-do-i-change-the-font-or-the-font-size-in-the-tty-console](https://askubuntu.com/questions/173220/how-do-i-change-the-font-or-the-font-size-in-the-tty-console).

That does not change the screen resolution, it changes the font size.  I want to change the screen resolution to 1280 x 1024, both to make the text larger, and so that if I ever plug an LCD display in there's a chance that it can actually handle the refresh rate.  The LCD probably would work if I made no change, it would come up with the maximum resolution of the LCD.  However the maximum resolution of the CRT is pushing things too far so a "happy medium" must be found.

---

### Post by mathog on 2017-03-29
> **Bashing-om said:**
> 
To tell grub not to use the resolution that bios passes 

grub isn't the problem, it's what happens once nouveau loads.

According to 

 [http://unix.stackexchange.com/questions/101643/centos-boot-time-screen-resolution](http://unix.stackexchange.com/questions/101643/centos-boot-time-screen-resolution)

the solution is to add this to the kernel parameters

```
nouveau.modeset=0

```

If the machine ever finishes upgrading to 16.04 I will give that a shot and report back here.

---

### Post by mathog on 2017-03-31
Tested this today.  Adding

```
nouveau.modeset=0

```

to the kernel boot line prevents nouveau from changing the resolution to an insanely high value.  With this set the entire kernel boot sequence has text of the same size.

---

