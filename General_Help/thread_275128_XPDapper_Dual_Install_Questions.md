---
title: "XP/Dapper Dual Install Questions"
date: 2006-10-10
forum: General Help
---

### Post by matt in japan on 2006-10-10
Hi, folks. New to Ubuntu and really enjoying it, with one small (and perhaps unimportant) issue: system hangs on reboot/shutdown after displaying "will now reboot/halt" dialogue.

Quick background:

 - installed latest Dapper from Live CD on XP machine (trying for dual boot - seems to work from Grub, except for the reboot/shutdown issue)

 - Set up four partitions - 3 x 50 GB (one Windows NTFS, one share, one for Linux, all marked primary) + Linux swap

First try with Dapper was a complete format and install from Live CD and GPartEd - no issues with reboot/shutdown, but unfortunately, I need that other OS from Redmond for the time being.

Any ideas?

---

### Post by mighty_falcon on 2006-10-12
I have the same exact problem..it hangs on that now halting message when I shut down...i have to manually turn it off from there

any help is greately appreciated!

edit: i am using the 386 kernel not the 686

---

### Post by matt in japan on 2006-10-12
Kind of a shot in the dark, but a Linux fanatic that I work with tells me that I should check for available BIOS and see what happens. I'm going to try it tonight and I'll post the results.

---

### Post by mighty_falcon on 2006-10-14
any lucK?

---

### Post by matt in japan on 2006-10-15
Flashed the BIOS and now I am able to reboot/shutdown without stalling. I hope this helps anyone who is experiencing similar problems.

---

### Post by krypto_wizard on 2006-10-15
I had similar problem. I was using TOshiba Laptop A70-S249 and I read on internet somewhere that it was the BIOS problem.

> **matt in japan said:**
> Flashed the BIOS and now I am able to reboot/shutdown without stalling. I hope this helps anyone who is experiencing similar problems.

---

