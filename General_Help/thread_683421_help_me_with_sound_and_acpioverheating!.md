---
title: "help me with sound and acpi/overheating!"
date: 2008-01-31
forum: General Help
---

### Post by gettingthere6 on 2008-01-31
Hi everyone, I had originally asked for help about 3 weeks ago in the Hardware/Laptop forums but I got no replies... 

I have recently installed gutsy on my Toshiba M45 S265 laptop. The sound did not work and the solution I found after some research was to turn off acpi. The sound now works but the battery monitor no longer works and my computer will not sleep or hibernate or properly shut down. All those functions (except for sound) work if I boot up with acpi on. 

Does anyone know of a solution to get the sound working that doesn't involve turning off acpi? My computer gets really hot- which concerns me (it does not do that running windows).

There are a bunch of threads on these power issues, but I haven't found an answer yet. I searched for a different answer for the sound issue (I don't get any sound all if acpi is turned on) but either the solutions don't work or I don't understand the instructions... 

Anyone got some advice for this beginner?

Thanks in advance

---

### Post by happyhamster on 2008-01-31
How did you turn of acpi? (In case you used a boot parameter; which one?)

---

### Post by rax_m on 2008-01-31
A solution for my Toshiba P100 was to install a custom DSDT file which enabled sound, and GPU fans. I don't know if this solution works for you. 
The linux ACPI website's changed now so I'm not sure where to look anymore.

---

### Post by gettingthere6 on 2008-01-31
I turned acpi off by following some instructions I found somewhere that involved editing the file /boot/grub/menu.lst by adding acpi=off

Frankly before this I had no idea how to do any of this stuff. Thanks for trying to help me out.

I'm going to do some research on this custom DSDT file, since I don't know what it is or where it is...but sounds like it might help. Anyone have any ideas?

Thank you so much.

---

### Post by happyhamster on 2008-02-01
What you could try is a few different boot parameters. Instead of disabling acpi completely, try disabling only parts of it.

acpi=noirq

pci=noacpi

Easiest way to test this is to reboot the computer, and add the parameters in the grub menu. You usually enter that menu automatically, if not, press the escape key a few times when you see the "grub loading..." message.

- Now, a line called "Ubuntu gutsy, kernel 2.6...." should be highlighted. Press 'e' to edit.
- Now select the second line, "kernel /boot/vmlinuz...." and press 'e' again.
- You should see all boot parameters currently used (in my case: ro quiet splash, in your case probably ro quiet splash acpi=off)
- Remove acpi=off and replace it with acpi=noirq
- Leave the other parameters alone, and always keep "ro" (!).
- Accept with the enter key.
- You're back to the previous page. Boot with the new parameter, by pressing 'b'.

- Check if anything has changed for the better.


Advantage of this procedure is that it's only temporary: it's pretty safe, because everything will be reset after a reboot. Only if you're sure that you've found the right parameter you should edit menu.lst.

Good luck, and keep us informed.

---

### Post by gettingthere6 on 2008-02-01
Success!

acpi=noirq  gives me both sound and all of those other features that weren't working with acpi=off (battery status, hibernation etc). The fans also seem to be working better. Hopefully it will no longer be so hot that it is uncomfortable to have the computer on my lap. Just out of curiosity, is there a way to check the temperature, and what temperature should it be at? 
 
 With pci=noacpi the audio did not work. 

Thank you again for your help.

Alice

---

### Post by gettingthere6 on 2008-02-01
EDIT#2: It finally dawned on me that the sound stops working whenever I come back from suspend/hibernation now and will work after rebooting, it's still an improvement from before.


EDIT: I don't know what's going on, but after rebooting a couple of times with acpi=noirq and the sound not working, now everything seems to be in working order. I probably missed/misspelled something along the way, so just ignore the message below.

**
Bad news. I may have jumped the gun in saying that everything was fixed. In actuality with acpi=noirq only the sound at boot up works. Everything else I've tried doesn't, and if I'm trying to play music, there is no sound and the program just crashes.

---

### Post by happyhamster on 2008-02-03
Hmm, weird. Is there a difference in the output of:

cat /proc/interrupts

Before and after suspend/hibernation? Does dmesg list errors about interrupts perhaps (when sound's not working)? Try:

dmesg | grep irq -i

(It will look in your log for the "irq" string). If you find something like "IRQ ..: Nobody cared" then try adding yet another bootparameter:

irqpoll

(in addition to acpi=noirq). 

[edit:] Try adding the parameter manually while booting (the grub menu again), don't directly edit menu.lst yet.

---

### Post by gettingthere6 on 2008-02-08
First of all, I apologize for not getting back to you sooner, I've had a crazy week. I followed your suggestions and it works! There was a difference of cat /proc/interrupts before and after hibernation/suspend (an error was listed). I also found something along the lines of irq nobody cared.

After adding irqpoll, sound works, even after hibernation.

I don't really know what all that did, but thanks for helping me out, I truly appreciate it.

---

