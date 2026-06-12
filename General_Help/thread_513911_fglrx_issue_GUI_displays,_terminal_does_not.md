---
title: "fglrx issue: GUI displays, terminal does not"
date: 2007-07-31
forum: General Help
---

### Post by Theory? on 2007-07-31
I manually installed fglrx and now I can get into GNOME just fine.

However, I press ctrl+alt+f1 to go to my terminal, and to my surprise, I have no terminal.  My monitor goes idle because no signal is being sent to it...similar to the problem I had with my GUI before I installed fglrx...but backwards.  Madness, I tell you.  MADNESS!

---

### Post by mcduck on 2007-07-31
You could try adding 'vga=792' to your kernel options in /bot/grub/menu.lst. This will make Ubuntu boot using 1024x768 resolution, and also affects the resolution in VTTs. At least this helped me with my Radeon 9600XT and Mobility Radeon X1600 cards..

---

### Post by Theory? on 2007-07-31
I'm just scrolling through this thing, would it be

defoptions=vga=792 under the section titled "default options" or should I just be appending that line to the end of the doc?

---

### Post by mcduck on 2007-07-31
you need to add it into both the defoptions line, and also to the end of the actual kernel entry line like this:
```

# defoptions=quiet splash vga=792
.
.
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=365d417b-a50b-4df9-8249-f17f37a542aa ro quiet splash vga=792
```

kernel line is the one that will actually do the job when you boot, and defoptions are used to generate kernel entries to the menu.lst file when you get kernel updates. So nthe importan one is the kernel line, and adding it to defoptions means that you don't have to add it to new kernel versions by hand.

If that one doesn't work for some reason try 791 instead of 792. It gives the same resolution but less colors which works better with some display adapters.

---

### Post by strabes on 2007-07-31
By the way, I believe you'll have to restart in order for the changes to take effect.

---

### Post by mcduck on 2007-07-31
> **strabes said:**
> By the way, I believe you'll have to restart in order for the changes to take effect.
Yes, that's of course true. Boot options are only recognized on boot. One of the rare situations when Linux needs a full reboot ;)

---

### Post by Theory? on 2007-07-31
Should that line still be commented?

EDIT: It doesn't seem to be working.

I have an ATI X1900 X.

I installed the fglrx driver and now I have no terminal.

---

### Post by mcduck on 2007-07-31
> **Theory? said:**
> Should that line still be commented?

EDIT: It doesn't seem to be working.

I have an ATI X1900 X.

I installed the fglrx driver and now I have no terminal.
yes, the default line should be commented.

It's strange if it doesn't work. It also worked on my friends X1800.. Did you try with 791 instead of 792?

---

