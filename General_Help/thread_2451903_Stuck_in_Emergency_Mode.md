---
title: "Stuck in Emergency Mode"
date: 2020-10-12
forum: General Help
---

### Post by risqi-r on 2020-10-12
I was running on my laptop a dual-boot system of Win8.1 and Ubuntu 18.04 LTS.
Suddenly, my laptop went into emergency mode when it booted but I don't know the cause

I typed "journalctl -xb" to view system logs then here are some red lines that I found:

```
[COLOR=#ff0000]Couldn't get size: 0x800000000000000e
MODSIGN: Couldn't get UEFI db list[/COLOR]
```

```
[COLOR=#ff0000]PKCS#7 signature not signed with a trusted key[/COLOR]
```

```
[COLOR=#ff0000]fsck failed with exit status 4.[/COLOR]
Running request emergency, target/start/replace
systemd-fsck@dev-disk-by\x2duuid-28d17037\x2d3529\x2d4641\x2d8fa5\x2d01acc067aed7.service: Main process
systemd-fsck@dev-disk-by\x2duuid-28d17037\x2d3529\x2d4641\x2d8fa5\x2d01acc067aed7.service: Failed with
[COLOR=#ff0000]Failed to start File System Check on /dev/diks/by-uuid/28d17037-3529-4641-8fa5-01acc067aed7.[/COLOR]
```

```
[COLOR=#ff0000]ata1.00: exception Emask 0x0 SAct 0xc00 SErr 0x0 action 0x0
ata1.00: irq_stat 0x40000008
ata1.00: failed command: READ FPDMA QUEUED
ata1.00: cmd 60/00:50:30:1e:e3/01:00:31:00:00/40 tag 10 ncq dma 131072 in
             res 41/40:00:10:1f:e3/00:01:31:00:00/40 Emask 0x409 (media error) <F>
ata1.00: status: { DRDY ERR }
ata1.00: error: { UNC }[/COLOR]
```

```
[COLOR=#ff0000]print_req_error: I/O error, dev sda, sector 836968208[/COLOR]
```

Please help me. What should I do?
Thank you in advance.

---

### Post by CelticWarrior on 2020-10-12
Can you still boot Windows directly?
If not your disk is toast. You have been warned: [https://ubuntuforums.org/showthread.php?t=2443160&p=13957064#post13957064](https://ubuntuforums.org/showthread.php?t=2443160&p=13957064#post13957064)

---

### Post by risqi-r on 2020-10-13
> **CelticWarrior said:**
> Can you still boot Windows directly?
If not your disk is toast. You have been warned: [https://ubuntuforums.org/showthread.php?t=2443160&p=13957064#post13957064](https://ubuntuforums.org/showthread.php?t=2443160&p=13957064#post13957064)

Yes, I can still boot windows.
I'm sorry I didn't pay attention to your warning. I initially didn't understand about the warning you gave and my problem has been resolved so I don't think it's a problem anymore.
Actually, several times (not often) I got an error message saying Kernel_Data_Inpage_Error on Windows.  My laptop also gets hot easily.

So what should I do at this point apart from changing to a new drive?

---

### Post by CelticWarrior on 2020-10-13
Send it to a competent tech service.

---

