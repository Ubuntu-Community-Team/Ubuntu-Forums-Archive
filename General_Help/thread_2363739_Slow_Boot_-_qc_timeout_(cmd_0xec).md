---
title: "Slow Boot - qc timeout (cmd 0xec)"
date: 2017-06-13
forum: General Help
---

### Post by marmaladejackson on 2017-06-13
Hi All,

I tried to upgrade to 17.04 a couple of weeks ago, but something went wrong and I wound up having to just do a clean install.  No big deal.  However, no the boot time takes significantly longer. Running dmesg, I find almost 30 seconds is being spent here:

```
[   18.415913] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   50.448918] ata3.00: qc timeout (cmd 0xec)
[   50.448928] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   50.924898] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
```
 
I did some googling and the suggestions seemed to revolve around setting the hard drives to AHCI in the BIOS.  They seemed to be already set like that.Does anybody have any ideas how to troubleshoot that error?  Or failing that, reduce the timeout to 1 second so it doesn't seem to hang?

Full dmesg:

[https://pastebin.com/L7BzHcs2](https://pastebin.com/L7BzHcs2)

lshw:

[https://pastebin.com/zTwEWMLP](https://pastebin.com/zTwEWMLP)


Thanks for any insight!
Brian

---

