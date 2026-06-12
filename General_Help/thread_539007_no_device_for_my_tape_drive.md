---
title: "no device for my tape drive"
date: 2007-08-30
forum: General Help
---

### Post by snorhyvel on 2007-08-30
I seem to not get any "dev" for my tape drive. I've tried different "modprobe" like eata, st, scsi_mod but no one seems to work. my dmesg looks like this:
[42949395.350000] DAC960#0:   Physical Devices:
[42949395.350000] DAC960#0:     0:5  Vendor: HP        Model: C7438A            Revision
: V303
[42949395.350000] DAC960#0:          Serial Number: 0005018354
[42949395.350000] DAC960#0:   Logical Drives:

some of my loaded modules:
st                     44320  0
scsi_mod              146184  1 st (could this be my tape?)
DAC960                 79304  0

I've added "st" in /etc/modules

can anyone help me?

---

