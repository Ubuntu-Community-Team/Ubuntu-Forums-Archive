---
title: "Unexpected reboot with no error seen"
date: 2008-06-24
forum: General Help
---

### Post by jb59892 on 2008-06-24
Hi All,

This is my first post to please excuse me if I ask what may seem a simple question to some:)

I installed Ubunto on an old PC I had laying around and it has run very well until recently when it started rebooting it self every few days; some times once a week some times three or four times a week. I've had alook in the messages file but there is no indication of any error before the system reboots. Can any one point me to a location to look for any error messages before the system rebooted it self?

Thanks,
Jon

---

### Post by iaculallad on 2008-06-24
Try to look at your /var/log/syslog file.

```
cat /var/log/syslog
```

---

### Post by jb59892 on 2008-06-24
> **iaculallad said:**
> Try to look at your /var/log/syslog file.

```
cat /var/log/syslog
```

Nothing obvious in there either (see below). Is there any way to force a system dump that I could look at after it does this the next time?

Jun 23 14:45:01 jbweb /USR/SBIN/CRON[10346]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Jun 23 15:02:15 jbweb syslogd 1.4.1#20ubuntu4: restart.
Jun 23 15:02:16 jbweb kernel: Inspecting /boot/System.map-2.6.20-15-server
Jun 23 15:02:16 jbweb kernel: Loaded 25134 symbols from /boot/System.map-2.6.20-15-server.
Jun 23 15:02:16 jbweb kernel: Symbols match kernel version 2.6.20.

---

### Post by iaculallad on 2008-06-24
Try issuing the command dmesg in your terminal:

```
dmesg
```

---

### Post by jb59892 on 2008-06-24
Same thing, there is no error shown, just the actual reboot :confused:

[    0.000000] Linux version 2.6.20-15-server (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:41:34 U
TC 2007 (Ubuntu 2.6.20-15.27-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000ec000 size: 0000000000014000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fef0000 end: 000000001fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fff0000 size: 0000000000008000 end: 000000001fff8000 type: 3
[    0.000000] copy_e820_map() start: 000000001fff8000 size: 0000000000008000 end: 0000000020000000 type: 4
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ec000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap

etc, etc....

---

### Post by madhusker on 2008-09-04
I have the same problem with 8.04.01.

---

### Post by lucho64 on 2008-09-04
I had the same problem a couple of weeks ago. Run memtest86 (the last of the default Ubuntu boot options in Grub) and found errors on one of my memory cards. Went and bought another pair and it's been solved ever since.
Linux does not reboot by itself. It might freeze, crash, whatever but I think the only time it could reboot by itself is with bad hardware (and that is pretty much either memory or CPU, even a hard drive failure won't give you this) or maybe ACPI shutting down because you were about to fry your CPU. But in that case it should leave a message in the logs.
So check memory, fans, etc. If there is nothing on the logs, I would say it's memory.
Actually there is a kernel option for automatically rebooting after a panic, but that is disabled by default, and you would get an error message in the logs anyway.

I think I've noticed that there seems to be more problems like this on the summer months (it's still likely that most Ubuntu users are in the northern hemisphere). So another thing to try is to just throttle down the CPU and maybe use less aggressive memory settings, at least while the summer remains hot ...

---

### Post by madhusker on 2008-09-04
Thanks for the reply. I did do memtest last night and everything is ok.  This machine has run gentoo rock solid for the last 3 years. I am trying out ubuntu and so far not much luck.

---

