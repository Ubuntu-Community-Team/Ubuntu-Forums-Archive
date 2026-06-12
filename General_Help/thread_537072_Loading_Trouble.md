---
title: "Loading Trouble"
date: 2007-08-28
forum: General Help
---

### Post by Mr. Mumbles on 2007-08-28
Hi all, I'm new to linux so bare with me :)

I recently installed Ubuntu (32bit edition) onto my computer onto its own 80gig hd. Everything is fine until I have to log in. I get to the log in screen, type my username and passwrod, hit enter and it starts to load, but then all the sudden it freezes and I sometimes get weird purple colored lines across the center on the screen or I get like a jagged square with those lines and I can barely make out it saying ubuntu. It gets completely frozen and I have to restart the pc. Any help would be greatly appreciated! 

My PC:
AMD64 3500+ winchester core
Motherboard: Asus A8N-E 
7800gt
x2 1gig OCZ Platinum pc3200
x2 80gig SATA hard drives, one with ubuntu, the other vista

---

### Post by nitro_n2o on 2007-08-28
I think you need ubuntu 64bit edition

---

### Post by Mr. Mumbles on 2007-08-28
Well, I should have no problems running the 32bit, as the processor can do both. Also, when I tried the live cd, and booted in like the safe graphics mode or whatever its called, it loaded, but not the regular loading option froze.

---

### Post by merlinus on 2007-08-28
It may be related to your video card.

You might try this.

At the login prompt, press Ctrl-Alt-F1.

Then enter at the CLI:

```

sudo dpkg-reconfigure xserver-xorg

```You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```or reboot.

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

You might also be able to do this by choosing Recovery Mode at the opening menu.

-merlin

---

### Post by Mr. Mumbles on 2007-08-28
Well, at the login screen Ctrl-Alt-F1 does nothing. In recovery mode, if I type sudo dpkg-reconfigure xserver-xorg it says xserver not found. If I type startx it goes to load but then freezes. Any other ideas?

---

### Post by merlinus on 2007-08-28
What about Ctrl-Alt-F1 after logging in?

-merlin

---

### Post by Mr. Mumbles on 2007-08-28
Hey I figured it out :)

I just plugged in my old PS/2 port keyboard and it worked, I typed what you said, selected vesa, and went through all the other stuff it had me do, restarted, and now I'm typing to you from Ubuntu. Thanks a lot! :)

---

### Post by Mr. Mumbles on 2007-08-28
Just one more quick question.

Now in grub, I have 4 Ubuntu options instead of just 2. I have 2 regular Ubuntu's and 2 Ubuntu recovery's. Is there any way to fix this?

---

### Post by merlinus on 2007-08-28
That is because you have two kernels, the original -15 and the upgrade to -16.

You can simply leave them, because you never know when the new one may cause unforeseen problems, and you can then boot from the old one.

But if it is terribly annoying, post back and I will give you instructions.

-merlin

---

### Post by Mr. Mumbles on 2007-08-28
> **merlinus said:**
> That is because you have two kernels, the original -15 and the upgrade to -16.

You can simply leave them, because you never know when the new one may cause unforeseen problems, and you can then boot from the old one.

But if it is terribly annoying, post back and I will give you instructions.

-merlin

So was the kernel -16 given to me through the updates I downloaded, or through the steps you gave to me?

Sorry, I know that might be a dumb question :lolflag:

---

### Post by merlinus on 2007-08-28
Through the updates.

-merlin

---

