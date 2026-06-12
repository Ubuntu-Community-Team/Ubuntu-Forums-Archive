---
title: "Shell screen resolution"
date: 2007-06-09
forum: General Help
---

### Post by chrismyers on 2007-06-09
Hi there,

Im running an Ubuntu server as a NAS (& various other things).

The server has no gui, no X. It only has a shell prompt.

How do I force a higher screen resolution for the shell so that I can get more text on screen?

Is it something I can set at boot time?

This would be incredibly useful, as the wordwrap on some screens can be annoying.

I'm sure this is possible, because Knoppix boots in a tiny text mode. Try as I might, I cant find a command to make the change.

Thanks in advance.

---

### Post by reclusivemonkey on 2007-06-09
In /boot/grub/menu.list add vga=791 to the kernel you are using like so;

```

kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d76bca45-bcd9-415a-9e4
4-b7f8faae9709 ro vga=791 quiet splash

```

I think you might be able to do this by default, but I am not too familiar with grub and am not too sure where you should place it, but the above works well for me.

---

### Post by hikaricore on 2007-06-09
> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash=verbose _**vga=791**_

Adding the line here as well will make it stay across upgrades that rewrite grub's menu.lst.
Please ignore my other defoptions unless you want them. :P

---

### Post by chrismyers on 2007-09-01
Hi guys,

Sorry for the delay, but I couldn't get it working straight away, got bogged down with another project & I had to put this one on-hold.

I have tried various options of VGA=xxx including:

794
775
771
0x31A

All of these produce the same results
[COLOR="RoyalBlue"]
**You passed an undefined mode number. Press RETURN to see video modes available**[/COLOR]

What am I doing wrong?

---

### Post by chrismyers on 2007-09-01
Update:

OK. I did some more research.

I tried vesa=791 option on a desktop version of Ubuntu & it worked fine.

This leads me to think that my Feisty server has a component missing that would allow me to change the resolution.

Does anyone have any ideas?

---

