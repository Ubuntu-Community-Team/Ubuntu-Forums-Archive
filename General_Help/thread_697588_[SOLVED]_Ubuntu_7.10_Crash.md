---
title: "[SOLVED] Ubuntu 7.10 Crash"
date: 2008-02-15
forum: General Help
---

### Post by DanielHorror on 2008-02-15
Hi all! I am a young, unexperienced Ubuntu user...
I have this problem:
My Ubuntu freezes at some point and don't reacts at nothing and I must reboot my PC from the button on the box...
When I check the error log I see this:

```
daniel@Dante:/var/log$ cd /var/log/
daniel@Dante:/var/log$ cat messages | grep error
Feb 15 17:44:05 Dante kernel: [   16.809145] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

```

I don't have ANY idea what to do!
Can some one tel me what is the problem and how can I fix it?

---

### Post by uberlube on 2008-02-15
Im not an expert when it comes to the kernal but it looks as though you may have deleted an important file. Try googling the error message to see if it is a common problem or something else, you may get a fix out of that. Also if you havent had Ubuntu installed for long and dont have too much stuff you want to keep just make backups and do a clean install.

---

