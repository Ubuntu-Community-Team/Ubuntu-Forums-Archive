---
title: "Feisty shutdown problem"
date: 2007-04-21
forum: General Help
---

### Post by lolwhites on 2007-04-21
Upgraded to Feisty on the 19th. Everything going smoothly do far except one thing; when I restart or shut down, it goes through all the right steps except the very last one - shutting off the power. I have to turn it off or restart manually once Ubuntu has shut everything down.

---

### Post by DeadEyes on 2007-04-21
An upgrade from the alternate CD caused the same problems for me. My wireless stopped working as well, but I expected that. After some messing around I realised I'd trashed some settings so I'm going to go for a clean Install. Hopefully that will fix my problem if it does I'll report back.

I assume the problem is a daemon failing to unload, I turned off power management but that had no effect. Trawling through logs might show something up.

Good Luck

---

### Post by jerrylamos on 2007-04-21
On our LAN one of the systems Feisty does not "shutdown".  After a while nothing is happening, the keyboard and mouse are dead, and there is no message on the screen at all.

After a while I take a chance that everything's halted and closed, then push hardware reset and power off.  Previous Ubuntu's 6.10 Edgy and 6.06 Dapper shut down just fine as do several competing Linux's.

So with Feisty I have to remember to "Restart" instead of "Shutdown" and watch to push power off before reboot occurs.  A bit of a messy workaround.

Cheers, Jerry :confused:

---

### Post by davemicc on 2007-04-21
Do you get a notice when the computer is booting like "APCI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI "?  In this case you can add acpi=force to the end of the kernel line in /boot/grub/menu.lst to force ACPI on.

---

### Post by lolwhites on 2007-04-21
I don't see any messages when booting up, no.

---

### Post by DeadEyes on 2007-04-21
Well after the clean install I can shutdown and restart OK. I don't really know enough to offer any insight into what the issue is.

---

### Post by Jallu59 on 2007-04-21
> **davemicc said:**
> Do you get a notice when the computer is booting like "APCI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI "?  In this case you can add acpi=force to the end of the kernel line in /boot/grub/menu.lst to force ACPI on.

Well, I am getting the error message mentioned above, with an antigue QDI Legend V- motherboard. Thank you for your advice, I will try that as soon I get to the computer.

If someone is not getting the error message, the diagnostig display on boot might be disabled in BIOS.

Yours Jallu59

---

### Post by nadarockyraccoon on 2007-04-23
i have this problem as well, and i have no solution better than when the last message is displayed "System Halted" it is ok to turn off the comp with the power button. This will not harm your drive. As far as the bios cuttoff error, use apm instead, though you can remove acpi, it is possable to turn it off, but i don't know how. It's possable that apm over acpi will fix the shutdown issue as well, but not likely (that issue is caused by acpi mismanagement). Also if it means that much to you, the debian Etch distro does not have this problem.

---

### Post by qvoffka on 2007-04-28
Hello, evetybody.
I had same problem with shutting down. Also I had message about adding acpi=force. 
After I added acpi=force to kernel line in menu.lst it's begin shut down.
But one question - is it OK for my HDD? Does go to parking with acpi=force?

---

### Post by lolwhites on 2007-04-30
Now it shuts down fine, but I still have the same problem when trying to restart.

---

### Post by Wherdgo on 2007-06-07
> **davemicc said:**
> Do you get a notice when the computer is booting like "APCI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI "?  In this case you can add acpi=force to the end of the kernel line in /boot/grub/menu.lst to force ACPI on.

Yep.  I got that one, and was looking for the answer.  Thanks for the tip, I'll implement it.

---

### Post by Wherdgo on 2007-06-07
Perhaps a n00b question; but after looking at the menu.lst, can anyone elaborate on where to place the acpi=force command at the "end of the kernel line"?  

There seem to be several commented kernel sections, and some global variables prior to the kernel(s) section.  Where should 'acpi=force' go?

It didn't work for me to put 'acpi=force' in the global section, so I'm wondering if it's placement is an issue.

Do I have to put acpi=force in every subsequent kernel's comment section, or just try plastering it on at the bottom?     Any insight would be appreciated, thanks.

---

### Post by regomodo on 2007-06-13
@wherdo you have to put acpi=force inline with your other options. Take mine for example

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7e91b1d3-25b0-4ff3-9242-2602b2605f3e acpi=force ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

---

### Post by Wherdgo on 2007-06-13
Perfect.  I'll try that.  Thank you.

---

### Post by regomodo on 2007-06-14
you'll still get the message, at least i do, but you will be able to shutdown properly

---

### Post by Wherdgo on 2007-06-15
Yup.  That worked like a charm.  I had 5 kernel sections, so I added it to all of them, and boom.  Works.
Thanks to everyone for their help on this thread.

---

### Post by Bugbear1973 on 2007-11-29
I'm running Ubuntu 7.10 on a Toshiba Satellite 4090XCDT (yes, an old laptop, but performance is generally what you would expect for a 400MHz processor - acceptable for basic web browsing)

I have been experiencing the same shutdown issues that have been reported earlier in this topic.  I've tried the acpi=force switch - while this does resolve the shutdown issues, I find that the processor usage goes through the roof.

Have other people seen this behaviour?

Cheers

---

### Post by -grubby on 2007-11-29
> **Bugbear1973 said:**
> I'm running Ubuntu 7.10 on a Toshiba Satellite 4090XCDT (yes, an old laptop, but performance is generally what you would expect for a 400MHz processor - acceptable for basic web browsing)

I have been experiencing the same shutdown issues that have been reported earlier in this topic.  I've tried the acpi=force switch - while this does resolve the shutdown issues, I find that the processor usage goes through the roof.

Have other people seen this behaviour?

Cheers

you do realize this is a nearly 8 month old thread? If you want help, you should start a new thread

---

