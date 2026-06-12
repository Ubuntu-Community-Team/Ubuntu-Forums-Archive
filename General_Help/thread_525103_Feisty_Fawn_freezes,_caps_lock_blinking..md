---
title: "Feisty Fawn freezes, caps lock blinking."
date: 2007-08-13
forum: General Help
---

### Post by Asian_Wannabe on 2007-08-13
I just did a fresh reinstall of Feisty because my system would occasionally freeze and the caps lock and num lock would be blinking. Problem is, even after the fresh install, I still get this problem. Can anyone help me :confused:?

---

### Post by Paulmd on 2007-08-14
> **Asian_Wannabe said:**
> I just did a fresh reinstall of Feisty because my system would occasionally freeze and the caps lock and num lock would be blinking. Problem is, even after the fresh install, I still get this problem. Can anyone help me :confused:?


I'm afraid you have a hardware issue. Open it up, blow out the dust. Maks sure ALL the fans are working. Look for bulging or leaking capacitors.  Check RAM (press ESC during boot, one of the options will be to run MEMTEST. 

Let us know what you find.

---

### Post by w2vy on 2007-08-14
> **Paulmd said:**
> I'm afraid you have a hardware issue. Open it up, blow out the dust. Maks sure ALL the fans are working. Look for bulging or leaking capacitors.  Check RAM (press ESC during boot, one of the options will be to run MEMTEST. 

Let us know what you find.

I am having similar problem. Mouse, Keyboard and Ethernet traffic all stops.

Cap Lock still active (does that action require CPU intervention or internal to keyboard?)

Then after 2 to 3 to 5 mins (not 100% sure and it may vary) it will come back as if nothing was wrong.

At times if I have not typed anything to my ssh session the session will even survive.

No dust here... brand new machine...

So... if you WAIT long enough does your system come back alive?

tom

---

### Post by Asian_Wannabe on 2007-08-14
I just cleaned all the dust out of my machine. Also the memtest seemed to repeat itself, and I needed the computer, so I stopped it. Also if I wait, the computer will not unfreeze itself.

---

### Post by w2vy on 2007-08-14
> **Asian_Wannabe said:**
> I just cleaned all the dust out of my machine. Also the memtest seemed to repeat itself, and I needed the computer, so I stopped it. Also if I wait, the computer will not unfreeze itself.

You should try letting the memory test run all night to be sure..
(or all day... depends when you sleep :biggrin: )

tom

---

### Post by Paulmd on 2007-08-14
> **Asian_Wannabe said:**
> I just cleaned all the dust out of my machine. Also the memtest seemed to repeat itself, and I needed the computer, so I stopped it. Also if I wait, the computer will not unfreeze itself.

Memtest runs infinitely until stopped. No errors (they get highlighted in red)?

If you got no errors on memtest, the RAM and processor are PROBABLY OK, and also, no critical heat issue. 

Another common hardware cause of freezing is a bad video card.  Do you get smears or odd artifacts on the screen? Check the capacitors on IT, too.  Also even an itty-bitty bulge on a capacitor is a very, very bad thing.

Older Nvidia cards (vanta, and geforce 2[if it came without a heatsink]), sometimes just crap out after so many years, and cause random nastiness.

Also, you just might have a bad keyboard, and it's an easy thing to test.


If you let us know the make and model of your machine (or motherboard) we could tell you if it's been prone to failures.

---

### Post by Paulmd on 2007-08-14
> **Asian_Wannabe said:**
> I just cleaned all the dust out of my machine. Also the memtest seemed to repeat itself, and I needed the computer, so I stopped it. Also if I wait, the computer will not unfreeze itself.

Memtest runs infinitely until stopped. No errors (they get highlighted in red)?

If you got no errors on memtest, the RAM and processor are PROBABLY OK, and also, no critical heat issue. 

Another common hardware cause of freezing is a bad video card.  Do you get smears or odd artifacts on the screen? Check the capacitors on IT, too.  Also even an itty-bitty bulge on a capacitor is a very, very bad thing.

Older Nvidia cards (vanta, and geforce 2[if it came without a heatsink]), sometimes just crap out after so many years, and cause random nastiness.

Also, you just might have a bad keyboard, and it's an easy thing to test.


If you let us know the make and model of your machine (or motherboard) we could tell you if it's been prone to failures.

---

### Post by tigerstripedcat on 2007-08-14
This is not a hardware issue.  I've had this problem before.  As far as I remember you need to pass an argument to the kernel.  I'm having this problem right now, and I've fixed it before.  Which kernel are you using?  I'll let you know if i fix it.

---

### Post by tigerstripedcat on 2007-08-14
Ok <<< I >>>> fix it by passing the following to the kernel at boottime (edit /boot/grub/menu.lst)

ro quiet splash noapic nolapic pci=noacpi acpi=off 

or you can try  noirq or irqpoll

or  no_timer_check  notsc

ubuntu (linux?) kernels have a horrible problem dealing with irqpolling, acpi, and system timing

I actually have to pass similar arguments on 3 seperate computers to have a stable problem-free system

---

### Post by wirelessmonkey on 2007-08-14
passing pci=nommconf also helped me with this issue... it was with an asus k7N mobo

---

### Post by w2vy on 2007-08-15
Well it just figures my IT guy would buy a Motherboard that is known to have problems.

I have an Intel D101GGC w/ Pent 4 #3.0Ghz AA D35788-310

Had BIOS 310 and I just upgraded to 312

I may stand a chance that something has been fixed since all the other reports I saw seem to
indicate it just did not work; when in fact the only 'issue' I have is it will hang for 2-3 mins and
then recover.

If I still have issues, I may need to try some of those kernel args.

Is there a description of them around?

thanks

---

