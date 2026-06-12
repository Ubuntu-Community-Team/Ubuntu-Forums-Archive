---
title: "Yet another no GUI post"
date: 2008-05-14
forum: General Help
---

### Post by Fizzwizz on 2008-05-14
Hi everyone
I'm new to Ubuntu, but have some linux experience.

I've just installed ubuntu-8.04-desktop-i386 within the windows environment (because the installer wouldn't recognise one of my partitions)

When I ran the demo from disk I had a GUI

Now if I boot from HDD I get only command line.

I've tried startx .. but this command isn't recognised.

Next I tried sudo apt-get install ubuntu desktop, but frustratingly I get "sudo not recognised"

I removed the distro then re-installed but still the same

What on earth have I done?

Thanks ... Fizz

---

### Post by RATM_Owns on 2008-05-14
Could you tell us what some of the lines in the command line is?
Or is it just blank?

---

### Post by ibuclaw on 2008-05-14
If you have a problem with Installing Ubuntu, Wubi isn't exactly going to be the Saviour of the Day.

Firstly, what sort of hard-drive do you have?
You may have to set a special boot-parameter to get it working when you first load up the Live-CD.

Regards
Iain

---

### Post by Fizzwizz on 2008-05-14
The command prompt says INITRAMFS
Are we installed properly here?

... Fizz

---

### Post by Fizzwizz on 2008-05-14
The drive is a Samsung HDD HM060HI 60GB SATA 1.5Gbps 5400rpm 8MB

---

### Post by ibuclaw on 2008-05-14
Ok, first, try rebooting your computer.
Go into BIOS and set your ICH8 controller to be in AHCI mode.

Then try booting from the Ubuntu LiveCD to see if it can detect your hard-drives properly.

Regards
Iain

---

### Post by Fizzwizz on 2008-05-14
Awesome, thanks tinivole. Sorted and installed properly now.

I'll be posting again to morrow with wifi help so don't go too far ;-)

Best wishes .. Fizz

---

