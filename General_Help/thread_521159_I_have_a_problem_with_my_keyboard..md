---
title: "I have a problem with my keyboard."
date: 2007-08-09
forum: General Help
---

### Post by ekb on 2007-08-09
I don't think this is an Ubuntu-related question however, I don't know where else I can ask. Please suggest any possible causes and solutions.

My keyboard doesn't work before I have already booted into Ubuntu. When I'm in a GRUB menu, I can't use my keyboard to choose different choice of OS. I have 2 keyboards; one is with my laptop and another one is usb keyboard connected to my laptop. Even in bios, i can't use my keyboard to select any part of the menu.

All that problem gone when my laptop already has an OS (ubuntu) running so I have no idea why this is happening.

thank you!

---

### Post by WakkiTabakki on 2007-08-09
It sounds like your BIOS is set to have USB controlled by OS. 
On my desktop computer, I can choose to let the BIOS or the OS control USB. If set to OS, it behaves exactly as you describe...

But, yes, it sure seems to be a BIOS configuration problem...
/N

---

### Post by ekb on 2007-08-09
thanks for you suggestion.

there wasn't any problem before last night so im not quite sure what changes it (I didn't go into bios for ages). But how do I fix it? I can't use my keyboard although I got into bios but i can't use my keyboard to change the configuration and my laptop doesn't have ps/2 port.

thank you.

---

### Post by ekb on 2007-08-09
any suggestion?

---

### Post by ekb on 2007-08-09
anyone?

---

### Post by WakkiTabakki on 2007-08-12
Ehhh, I may have misunderstood something, but won't your laptops built-in keyboard work?
As I understood, it was an external keyboard connected to the USB port that didn't react until you'd booted an OS...


/N

---

### Post by Herman on 2007-08-12
Hmmm, well I have an Acer laptop and I was trying out Clonezilla on a GParted-Clonezilla CD and it asked me a question about selecting a keymap as it loaded. 
I don't know what happened, but next time I went to use my laptop I couldn't type my password. Neither the usb keyboard I have or the laptop's own keyboard would work properly. Then I remembered playing with Clonezilla. 
It was easy to fix for me, all I did was go into the BIOS (CMOS settings) and select 'reset to defaults'. That fixed it! :) Simple!

Well, that worked for me anyway. I really don't know if I can solve every keyboard problem in the world with the same simple method, but it probably wouldn't hurt to try that if you can manage it at all. I had a little trouble navigating in the BIOS too, but I did manage it somehow. 
I hope it helps, 
Regards, Herman :)

---

