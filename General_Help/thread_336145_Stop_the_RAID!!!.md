---
title: "Stop the RAID!!!"
date: 2007-01-11
forum: General Help
---

### Post by dhoeschen on 2007-01-11
I created a RAID5 over 4) ATA drives, after rebooting I had an error "DMA timeout" for hdh so I rebooted with no IDE DMA support.  MDADM said my RAID is being re-built in the background and my system is extremely slow.

I would like to know how I can KILL the background rebuilding process or simply get a status or progress report.

What commands should I try?  Remember, my system is very,very slow right now (it takes a while for the letters I type to show up in the shell) so a direct approach would be helpful.

;)

---

### Post by kidders on 2007-01-11
Hi there,

Surely you don't want to kill the rebuild!

You can see what's going on either by taking a look at the contents of /proc/mdstat or using mdadm for more detailed info & control.

---

### Post by dhoeschen on 2007-01-11
The confusing part is... I don't know what it is rebuilding!

The Prequel:
The 4) drives should be empty.  2) were from a previous mirrored RAID and were re-partitioned.  After creating my /dev/md0 I tried to format the partition but it stopped responding 3/4 of the way thru.  That is when the system was re-booted and I seen the DMA error.

I don't know what will be rebuilt, perhaps the information on one of the drives?

---

### Post by kidders on 2007-01-11
Ahhh. I see. In that case, mdadm is indeed the tool you're looking for. It will let you stop an array, disassemble it, or whatever you'd like. You can also make it give you very detailed information about your arrays ... far more than what's in /proc/mdstat.

Your DMA-related error probably has to do with a faulty SATA controller implementation. (They're worryingly common!) I've seen people encounter them while arrays are doing very I/O-intensive stuff like rebuilding themselves. Since you seem to be connecting four hard disks to the same I/O bus, I can't say I'm too surprised. :-( Post back if it keeps giving you trouble.

---

