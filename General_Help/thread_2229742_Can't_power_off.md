---
title: "Can't power off"
date: 2014-06-15
forum: General Help
---

### Post by dcintes on 2014-06-15
Hi,

I can't power off the computer. Is a recent installation of 14.04, in the old 13.04 don't have this problem. When shutdown the last lines are:

Will now halt
reboot: System halted

and then don't do nothing. Just can press power button and force stop.

I try some configurations of /etc/default/grub and nothing

Thx for help

---

### Post by Blutkoete on 2014-06-15
Hello,

could you please try the following [command]("http://linux.die.net/man/8/halt") in a terminal

```
sudo halt -p
```

and tell us if the system powers off or if it stops with the same message as you posted before?

Blutkoete

**WARNING:** Any command issued with *sudo* in front may harm your system, so be sure to read beforehand what *halt* does. You have no reason to trust me!

---

### Post by dcintes on 2014-06-15
Hi,

Same problem with halt. The system stops with same message.

---

### Post by dcintes on 2014-06-16
I reinstall the system and the bug persist.

Someone know somo solution?

---

### Post by Deanimator on 2014-06-16
This is a well known problem without any well known definitive solution.

I'm having the related problem of not being able to reboot.

You could try "sudo shutdown -P now", which works for me.

---

### Post by dcintes on 2014-06-16
> **Deanimator said:**
> This is a well known problem without any well known definitive solution.

I'm having the related problem of not being able to reboot.

You could try "sudo shutdown -P now", which works for me.

Don't work, same problem. Can't power off the computer

---

### Post by Deanimator on 2014-07-03
I couldn't make this work in a machine with a Biostar nForce 6100-A939 MB.

The board stopped responding to the keyboard (probable bad cap), so I ditched it.

I had a working 12.04 system (ECS MB), so I disconnected the two RAIDed drives and moved the drives from the Biostar.

I decided to start over in an organized fashion, so I found a well organized thread on how to fix the problem and tried the GRUB switches one by one.  The post I used gave four switches: efi, bios, acpi and pci.  The last one worked.  Got it working the night before last.

I have no idea if the Biostar board would never have worked, or whether it was the board dying.  Six of one, half dozen of the other.  I had wanted to keep the 12.04 install going, but the ECS is a LOT better motherboard, and I can always switch back to the 12.04 install by reconnecting the drives.

---

### Post by morganpatrick on 2014-08-12
Same issue here. I have tried all kinds of modifications to grub and nothing works. Suspending doesn't work for me, either -- it just starts to suspend and then pops right back up.

It would be helpful if the last poster would give some more details on what worked for them. What does it mean that you 'tried the GRUB switches'?

---

