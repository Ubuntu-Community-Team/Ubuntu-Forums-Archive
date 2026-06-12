---
title: "[SOLVED] How to start in init 0 after reboot withUbuntu Gutsy"
date: 2008-03-14
forum: General Help
---

### Post by moonkuh on 2008-03-14
Hi all

My motherboard needs a restart to accept the start time in the bios.
Under Debian the only thing i had to do to shutdown the pc after a
restart was enter a 0 

```
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3b9e3c24-a44d-40b6-b258-4ea79c3ae82d ro quiet splash acpi=force 0
```

but under Ubuntu Gutsy, this doesn't work.

I also tried init 0 and init=/sbin/poweroff.
With init 0, Gutsy starts normal and with init=/sbin/poweroff i get a
kernel panic :(

I also tried the poweroff kernel v. 2.6...., but there seems to be a
problem with acpi or apm, so that the pc doesn't wakeup automatically :(

Does someone know the option how i can start the kernel in init 0, so
that he turns off after a restart?

---

### Post by pointone on 2008-03-15
Is /etc/event.d/rc-default what you're looking for?

---

### Post by dcstar on 2008-03-15
> **moonkuh said:**
> 
..........
Does someone know the option how i can start the kernel in init 0, so
that he turns off after a restart?

Run level "init" 0 will shutdown a PC, "init 6" is the reboot sequence.

---

### Post by moonkuh on 2008-03-15
Solved

I got the PowerOff-Kernel 2.6.9 to work and everything is working fine :)

---

