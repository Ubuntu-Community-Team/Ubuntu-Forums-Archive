---
title: "raid 5 array and disk standby"
date: 2008-02-28
forum: General Help
---

### Post by mrf0x on 2008-02-28
hi all,

I have a home server with 5 disks as a RAID5 array. most of the time these disks are idle, so I let them spin down to save power. 
the problem is that when accessing the array when all disks are in standby, all the disks spin up *sequentially *- each taking around 20 secs. so I have to wait almost 2 minutes until I finally can access any data. 
is there an easy way how I can spin up all the disks in parallel, as soon as any of the disks is accessed?

thanks!

---

### Post by fjgaude on 2008-02-29
Is the array being driven by a raid card, hardware raid?

---

### Post by mrf0x on 2008-02-29
> **fjgaude said:**
> Is the array being driven by a raid card, hardware raid?

it's a software md RAID (kernel 2.6.23.9)

---

### Post by fjgaude on 2008-02-29
Strange, I run a four-disk raid5 mdadm array and at boot-up they all seem to come up fast enough to not hold assembly back. This is true for Hardy, Gudtsy, and Feisty, 2.6.24, 2.6.22, and 2.6.20. How do you get them, the drives, to spin-down?

Your controller is on the motherboard or is it a card running JBOD style?

---

### Post by mrf0x on 2008-03-03
> **fjgaude said:**
> Your controller is on the motherboard or is it a card running JBOD style?

some of the disks are directly plugged into the MB, some are on a PCI-express SATA controller. the spindown time is set in /etc/hdparm.conf (spindown_time directive). 

so --  what I'm looking for is a way to monitor when any of the disks in the array spins up, and then issue hdparm commands to the other disks so they are ready immediately... are there any hooks in the md driver for this?

thanks,
- Dave.

---

### Post by fjgaude on 2008-03-03
I think that md is a part of the 2.6.20 and beyond kernels. I guess you are using the -s and/or -S options in the hdparm program?

Each drive has been set to spindown after a time of no-activity?

You do this to save electrical power or wear and tear on the drive bearings?

Out of curiosity, what does hdparm -tT /dev/md0 or whatever show for the array?

---

### Post by mrf0x on 2008-03-03
> **fjgaude said:**
> I guess you are using the -s and/or -S options in the hdparm program?

Each drive has been set to spindown after a time of no-activity?
yes, by setting the spindown_time in /etc/hdparm.conf so this is done automatically @ boot. it looks like this:
```
root@marvin:# tail /etc/hdparm.conf
/dev/disk/by-id/scsi-SATA_WDC_WD10EACS-00_WD-WCASJ0351065 {
        spindown_time = 246
}
... (etc for other disks)
```

> You do this to save electrical power or wear and tear on the drive bearings?
to save power. I know I'm rather increasing than decreasing mechanical wear and tear by doing that.

> Out of curiosity, what does hdparm -tT /dev/md0 or whatever show for the array?
```

root@marvin:# hdparm -tT /dev/md0 (... wait for disks to spin up...)

/dev/md0:
 Timing cached reads:   1302 MB in  2.00 seconds = 651.18 MB/sec
 Timing buffered disk reads:  322 MB in  3.00 seconds = 107.22 MB/sec
```

for the record (although I don't think it has anything to do with the issue), the filesystem is ext3  on top of LVM, which is on top of a LUKS crypto device which is on top of the RAID.

---

### Post by fjgaude on 2008-03-03
Five drives running without seeking likely use about 2 watts each, if they are late-generation ones.

Your drive controller, at least the MB one, must be on the PCI bus, as your top throughput is limited to about 114 MB/sec.

Here's mine:

With Xigmatek DHT-S1283 cooler, CPU at 4.0MHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz) (2/26/08), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.33/1.31v:

```
/dev/md32:
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

I have only four drives in raid5. I would forget the spin-down but you might think otherwise.

---

