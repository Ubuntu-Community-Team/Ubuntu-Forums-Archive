---
title: "Read Only Permission to Mounted Drive"
date: 2024-09-18
forum: General Help
---

### Post by ldavid on 2024-09-18
Recently upgraded to the newest version of Ubuntu (24.04.1 LTS), and now have some issues with an external HDD permanently plugged in.

It appears (I think) that I only now have **read-only** access to the mounted **exFAT** partition. Upon upgrade it auto dismounted the drive, so I went into "Disks" and went into mounting options to ensure it is mounted automatically upon boot - this worked successfully.

Per Mount Options I have set:

```
Mount Point: /mnt/Temp
Identify As: LABEL=Temp
```

I'm lost as to how to make this drive read-writable moving forward?

Appreciate any assistance someone is able to give.

Thanks

---

### Post by ldavid on 2024-09-18
Was able to solve my issue! I was able to find someone with a similar issue and I followed instructions on this page which resolved the problem: [URL="https://forums.linuxmint.com/viewtopic.php?t=413207"]https://forums.linuxmint.com/viewtopic.php?t=413207
[/URL]
Providing here in case anybody else in the future runs into this problem.

---

### Post by yancek on 2024-09-18
Your link in post # 2 is broken (504 error) so I don't know what it says but, part of the problem is that you were using the proprietary, Microsoft windows exfat filesystem on the drive partition.  Support for exfat should be available in recent Linux systems.  You do know that windows filesystems do not use the standard Linux permissions, do not understand them?  You need to use umask or dmask and fmask entries in your /etc/fstab file to set permissions.,

---

