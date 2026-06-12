---
title: "Recursive copy to dvd-ram w/ udf freezes system"
date: 2006-07-19
forum: General Help
---

### Post by ecki on 2006-07-19
Hi,

I formatted a dvd-ram with udf.  Than after mounting the dvd-ram I can copy files to it and a diff shows that the copied files are okay.  To ensure that the files has really been written I switched the writer off and on and mounted and ejected another dvd between cp and diff.  But if I try to recursively copy directories to the udf-formatted dvd-ram:

```
cp -r /some/dir /media/cdrecord
```

than after a few seconds the system freezes totally - only a power off/on to reboot is possible.

The same occurs if I use Nautilus for the copying.

However if I formatted the dvd-ram with ext2 all went fine, no problems.

I run Ubuntu 5.10 with kernel 2.6.12-10-amd64-generic on a Dell OPTIPLEX GX620 (Intel P4 620, 1G RAM), the dvd-writer is a NEC ND-4550A (Firmware 1.07), connected via USB with a Cypress Semiconductor Corp. USB-2.0 IDE Adapter.

Any suggestions?

       Thanks

           Ecki

---

