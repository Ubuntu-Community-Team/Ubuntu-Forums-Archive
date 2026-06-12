---
title: "Locallly installed ubuntu desktop consuming too much memory - II"
date: 2013-11-28
forum: General Help
---

### Post by chetanmadaan on 2013-11-28
This is a REPOST for this one : [http://ubuntuforums.org/showthread.php?t=2180800&highlight=Locallly+installed+ubuntu+desktop+consuming+memory](http://ubuntuforums.org/showthread.php?t=2180800&highlight=Locallly+installed+ubuntu+desktop+consuming+memory).


I am still having memory problems and all and i am starting to doubt if ubuntu is really best for what i want to have (considering the fact that ubuntu is considered best for daily use desktop) where i am running it as a server.

Once of the things i saw when i ran **top **command this time was a lot of times find/chown/chmod commands are at the top of the list as it refreshes... and may be it's because i am running **crontab** cronjobs every minute to change permissions for all the files for around 5 - 6 users.
is that something that could be consuming a lot of memory??

other than this... i installed the desktop GUI a while ago... but don't really need it. shall i just remove it.. will it save some/any memory?

Thanks

---

### Post by MG&amp;TL on 2013-11-28
Desktop Ubuntu will/should be absolutely fine with your reported 4GB. You may be struggling conceptually with how Linux handles RAM, but there's a really good read on that at [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/).

Running every minute seems a little excessive, but *chown*, *chmod* and co. should take very little time to execute, so should not be a problem. *top* should tell you how much memory is being used for each process: the ***%MEM*** column.

Not running the desktop GUI will save a considerable amount, but not that much; remove it if you want.

---

### Post by chetanmadaan on 2013-11-28
Thanks for the quick reply... i will definitely get up to linuxatemyram.com and figure something  out.

here are some screenshots from the top commands.

[IMG]http://content.screencast.com/users/jmexperts/folders/Jing/media/f7f9ba29-6651-4482-8f2a-1e5c8cbeb072/2013-11-28_1207.png[/IMG]

[IMG]http://content.screencast.com/users/jmexperts/folders/Jing/media/16f032de-e813-47c5-b6f1-1f68bf8c6d87/2013-11-28_1208.png[/IMG]

[IMG]http://content.screencast.com/users/jmexperts/folders/Jing/media/d7b70c07-2c0d-4166-bd79-69b55f899dc0/2013-11-28_1209.png[/IMG]

Anyone? has some other advice?

---

### Post by MG&amp;TL on 2013-11-28
You're actually using (at the moment *free -m* ran), 1085 MB out of a possible 5766 MB. What's your problem?

---

### Post by chetanmadaan on 2013-11-28
No problem right now... because i just restarted it... but about 10 minutes... it wasn't in taking commands... i mean i type in **shutdown -r now** and i didn't even restart and then i had to manually plug out the cable and restart it.

---

### Post by MG&amp;TL on 2013-11-28
> **chetanmadaan said:**
> No problem right now... because i just restarted it... but about 10 minutes... it wasn't in taking commands... i mean i type in **shutdown -r now** and i didn't even restart and then i had to manually plug out the cable and restart it.

Memory is probably not your problem then, unless a recalcitrant process locks everything up somehow (which is pretty hard to do). Do the logs have anything interesting in them?

---

### Post by chetanmadaan on 2013-11-28
Well, shall i be looking at a specefic log file?

i mean... i went through all the files under /var/log and didn't find anything interesting (***may be because i don't know what i am looking for***[I]?)

[/I]Thanks

---

### Post by MG&amp;TL on 2013-11-28
You might try */var/log/kern.log.1* . Unfortunately, this is where my knowledge runs a little thin; I have no idea why the machine is freezing and no idea if and where that would be logged. It might be a good idea to check the hardware on the machine as well as pursuing investigations on the software side.

Another to try is to boot another distribution on a live CD and see if it still freezes after ten minutes as Ubuntu is doing.

Sorry I can't help more. :-(

---

### Post by chetanmadaan on 2013-11-28
Here we are... **none of this is making sense to me... (*may be because i am too stupid :-p)***
```
Nov 26 13:11:03 joomdevprojects kernel: [660007.969739] usb 1-1.3: USB disconnect, device number 7
Nov 26 13:11:03 joomdevprojects kernel: [660008.210538] usb 1-1.3: new low-speed USB device number 8 using ehci_hcd
Nov 26 13:11:03 joomdevprojects kernel: [660008.313016] usb 1-1.3: New USB device found, idVendor=1a2c, idProduct=0021
Nov 26 13:11:03 joomdevprojects kernel: [660008.313023] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 26 13:11:03 joomdevprojects kernel: [660008.313027] usb 1-1.3: Product: USB Keykoard
Nov 26 13:11:03 joomdevprojects kernel: [660008.313031] usb 1-1.3: Manufacturer: USB
Nov 26 13:11:03 joomdevprojects kernel: [660008.316030] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input15
Nov 26 13:11:03 joomdevprojects kernel: [660008.316135] hid-generic 0003:1A2C:0021.0009: input,hidraw0: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:1a.0-1.3/input0
Nov 26 13:11:13 joomdevprojects kernel: [660018.293287] hid-generic 0003:1A2C:0021.000A: usb_submit_urb(ctrl) failed: -1
Nov 26 13:11:13 joomdevprojects kernel: [660018.293332] hid-generic 0003:1A2C:0021.000A: timeout initializing reports
Nov 26 13:11:13 joomdevprojects kernel: [660018.293473] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/input/input16
Nov 26 13:11:13 joomdevprojects kernel: [660018.293816] hid-generic 0003:1A2C:0021.000A: input,hidraw1: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:1a.0-1.3/input1
Nov 27 21:05:30 joomdevprojects kernel: imklog 5.8.6, log source = /proc/kmsg started.
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Linux version 3.5.0-43-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #66~precise1-Ubuntu SMP Thu Oct 24 14:52:23 UTC 2013 (Ubuntu 3.5.0-43.66~precise1-generic 3.5.7.23)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-43-generic root=UUID=5ff68faa-a3ad-4099-8e34-269996af1070 ro
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] KERNEL supported cpus:
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   Intel GenuineIntel
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   AMD AuthenticAMD
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   Centaur CentaurHauls
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009bfff] usable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x000000000009c000-0x000000000009ffff] reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cb441fff] usable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb442000-0x00000000cb484fff] ACPI NVS
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb485000-0x00000000cb4f6fff] reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb4f7000-0x00000000cb50afff] ACPI NVS
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb50b000-0x00000000cb50cfff] usable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb50d000-0x00000000cb612fff] reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb613000-0x00000000cb613fff] usable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb614000-0x00000000cb614fff] ACPI NVS
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb615000-0x00000000cb61cfff] ACPI data
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb61d000-0x00000000cb61dfff] ACPI NVS
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb61e000-0x00000000cb61ffff] ACPI data
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb620000-0x00000000cb627fff] ACPI NVS
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb628000-0x00000000cb648fff] reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb649000-0x00000000cb68bfff] ACPI NVS
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cb68c000-0x00000000cb7fffff] usable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000cde00000-0x00000000cfffffff] reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000e3ffffff] reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000017bffffff] usable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x000000017c000000-0x000000017fffffff] reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] BIOS-e820: [mem 0x0000000180000000-0x00000001abffffff] usable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] NX (Execute Disable) protection: active
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] SMBIOS 2.6 present.
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] DMI:                  /DH55TC, BIOS TCIBX10H.86A.0035.2010.0429.1516 04/29/2010
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] No AGP bridge found
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] e820: last_pfn = 0x1ac000 max_arch_pfn = 0x400000000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] MTRR default type: uncachable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] MTRR fixed ranges enabled:
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   00000-9FFFF write-back
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   A0000-BFFFF uncachable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   C0000-CFFFF write-protect
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   D0000-E7FFF uncachable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   E8000-FFFFF write-protect
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] MTRR variable ranges enabled:
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   1 base 0CC000000 mask FFC000000 uncachable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   2 base 0D0000000 mask FF0000000 uncachable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   3 base 0E0000000 mask FE0000000 uncachable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   4 base 17C000000 mask FFC000000 uncachable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   5 base 1AC000000 mask FFC000000 uncachable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   6 base 1B0000000 mask FF0000000 uncachable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   7 base 1C0000000 mask FC0000000 uncachable
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] original variable MTRRs
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] reg 0, base: 0GB, range: 8GB, type WB
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] reg 1, base: 3264MB, range: 64MB, type UC
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] reg 2, base: 3328MB, range: 256MB, type UC
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] reg 3, base: 3584MB, range: 512MB, type UC
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] reg 4, base: 6080MB, range: 64MB, type UC
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] reg 5, base: 6848MB, range: 64MB, type UC
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] reg 6, base: 6912MB, range: 256MB, type UC
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] reg 7, base: 7GB, range: 1GB, type UC
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] total RAM covered: 5952M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 128M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 256M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 512M     num_reg: 8      lose cover RAM: -320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 1G     num_reg: 8      lose cover RAM: -256M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64K     chunk_size: 2G     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128K     chunk_size: 16M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128K     chunk_size: 32M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128K     chunk_size: 64M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 128M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 256M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 512M     num_reg: 8      lose cover RAM: -320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 1G     num_reg: 8      lose cover RAM: -256M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128K     chunk_size: 2G     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256K     chunk_size: 16M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256K     chunk_size: 32M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256K     chunk_size: 64M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 128M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 256M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 512M     num_reg: 8      lose cover RAM: -320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 1G     num_reg: 8      lose cover RAM: -256M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256K     chunk_size: 2G     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512K     chunk_size: 16M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512K     chunk_size: 32M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512K     chunk_size: 64M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 128M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 256M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 512M     num_reg: 8      lose cover RAM: -320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 1G     num_reg: 8      lose cover RAM: -256M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512K     chunk_size: 2G     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 1M     chunk_size: 16M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 1M     chunk_size: 32M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 1M     chunk_size: 64M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 128M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 256M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 512M     num_reg: 8      lose cover RAM: -320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 1G     num_reg: 8      lose cover RAM: -256M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 1M     chunk_size: 2G     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 2M     chunk_size: 16M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 2M     chunk_size: 32M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 2M     chunk_size: 64M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 128M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 256M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 512M     num_reg: 8      lose cover RAM: -320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 1G     num_reg: 8      lose cover RAM: -256M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 2M     chunk_size: 2G     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 4M     chunk_size: 32M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 4M     chunk_size: 64M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 4M     chunk_size: 128M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 4M     chunk_size: 256M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 4M     chunk_size: 512M     num_reg: 8      lose cover RAM: -320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 4M     chunk_size: 1G     num_reg: 8      lose cover RAM: -256M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 4M     chunk_size: 2G     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 8M     chunk_size: 128M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 8M     chunk_size: 256M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 8M     chunk_size: 512M     num_reg: 8      lose cover RAM: -320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 8M     chunk_size: 1G     num_reg: 8      lose cover RAM: -256M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 8M     chunk_size: 2G     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 16M     chunk_size: 128M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 16M     chunk_size: 256M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 16M     chunk_size: 512M     num_reg: 8      lose cover RAM: -320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 16M     chunk_size: 1G     num_reg: 8      lose cover RAM: -256M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 16M     chunk_size: 2G     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 32M     chunk_size: 128M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 32M     chunk_size: 256M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 32M     chunk_size: 512M     num_reg: 8      lose cover RAM: -320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 32M     chunk_size: 1G     num_reg: 8      lose cover RAM: -256M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 32M     chunk_size: 2G     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 8      lose cover RAM: 768M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 64M     chunk_size: 128M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 64M     chunk_size: 256M     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 64M     chunk_size: 512M     num_reg: 8      lose cover RAM: -320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 64M     chunk_size: 1G     num_reg: 8      lose cover RAM: -256M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 8      lose cover RAM: 320M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 8      lose cover RAM: 64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 128M     chunk_size: 512M     num_reg: 8      lose cover RAM: -192M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] *BAD*gran_size: 128M     chunk_size: 1G     num_reg: 8      lose cover RAM: -64M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 8      lose cover RAM: 192M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 6      lose cover RAM: 576M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 5      lose cover RAM: 576M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 5      lose cover RAM: 576M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 5      lose cover RAM: 576M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 5      lose cover RAM: 832M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 5      lose cover RAM: 832M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 5      lose cover RAM: 832M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 3      lose cover RAM: 1856M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 3      lose cover RAM: 1856M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 1      lose cover RAM: 3904M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] mtrr_cleanup: can not find optimal value
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] e820: update [mem 0xcc000000-0xffffffff] usable ==> reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] e820: update [mem 0x17c000000-0x17fffffff] usable ==> reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] e820: last_pfn = 0xcb800 max_arch_pfn = 0x400000000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] found SMP MP-table at [mem 0x000fcd40-0x000fcd4f] mapped at [ffff8800000fcd40]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0xcb7fffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  [mem 0x00000000-0xcb7fffff] page 2M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] kernel direct mapping tables up to 0xcb7fffff @ [mem 0x1fffb000-0x1fffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x17bffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  [mem 0x100000000-0x17bffffff] page 2M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] kernel direct mapping tables up to 0x17bffffff @ [mem 0xcb7fd000-0xcb7fffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] init_memory_mapping: [mem 0x180000000-0x1abffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  [mem 0x180000000-0x1abffffff] page 2M
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] kernel direct mapping tables up to 0x1abffffff @ [mem 0x17bffe000-0x17bffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] RAMDISK: [mem 0x36200000-0x370f7fff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: RSDP 00000000000f0410 00024 (v02  INTEL)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: XSDT 00000000cb61ee18 00054 (v01 INTEL  DH55TC   01072009 MSFT 00010013)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: FACP 00000000cb61cd98 000F4 (v04 INTEL  DH55TC   01072009 MSFT 00010013)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20120320/tbfadt-378)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xCB61DF40/0x00000000CB61DE40, using 32 (20120320/tbfadt-502)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: DSDT 00000000cb615018 06B88 (v01 INTEL  DH55TC   00000000 INTL 20051117)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: FACS 00000000cb61df40 00040
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: APIC 00000000cb61cf18 000CC (v02 INTEL  DH55TC   01072009 MSFT 00010013)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: SSDT 00000000cb61cc18 00102 (v01 INTEL  DH55TC   00000001 MSFT 03000001)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: MCFG 00000000cb61ff18 0003C (v01 INTEL  DH55TC   01072009 MSFT 00000097)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: HPET 00000000cb61fe98 00038 (v01 INTEL  DH55TC   01072009 AMI. 00000003)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: ASF! 00000000cb61ec18 000A0 (v32 INTEL  DH55TC   00000001 TFSM 000F4240)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] No NUMA configuration found
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x00000001abffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x1abffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   NODE_DATA [mem 0x1abffc000-0x1abffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]  [ffffea0000000000-ffffea0006bfffff] PMD -> [ffff8801a5600000-ffff8801ab5fffff] on node 0
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Zone ranges:
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   Normal   [mem 0x100000000-0x1abffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Movable zone start for each node
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Early memory node ranges
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009bfff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   node   0: [mem 0x00100000-0xcb441fff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   node   0: [mem 0xcb50b000-0xcb50cfff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   node   0: [mem 0xcb613000-0xcb613fff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   node   0: [mem 0xcb68c000-0xcb7fffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   node   0: [mem 0x100000000-0x17bffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   node   0: [mem 0x180000000-0x1abffffff]
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] On node 0 totalpages: 1520965
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   DMA zone: 6 pages reserved
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   DMA zone: 3910 pages, LIFO batch:0
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   DMA32 zone: 812537 pages, LIFO batch:31
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   Normal zone: 11008 pages used for memmap
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]   Normal zone: 677120 pages, LIFO batch:31
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] SMP: Allowing 16 CPUs, 12 hotplug CPUs
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] nr_irqs_gsi: 40
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb442000 - 00000000cb485000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb485000 - 00000000cb4f7000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb4f7000 - 00000000cb50b000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb50d000 - 00000000cb613000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb614000 - 00000000cb615000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb615000 - 00000000cb61d000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb61d000 - 00000000cb61e000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb61e000 - 00000000cb620000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb620000 - 00000000cb628000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb628000 - 00000000cb649000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb649000 - 00000000cb68c000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cb800000 - 00000000cde00000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000cde00000 - 00000000d0000000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000e0000000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000e4000000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000e4000000 - 00000000fed1c000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PM: Registered nosave memory: 000000017c000000 - 0000000180000000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] e820: [mem 0xe4000000-0xfed1bfff] available for PCI devices
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:1
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8801abc00000 s83584 r8192 d22912 u131072
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] pcpu-alloc: s83584 r8192 d22912 u131072 alloc=1*2097152
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1493567
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Policy zone: Normal
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-43-generic root=UUID=5ff68faa-a3ad-4099-8e34-269996af1070 ro
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] __ex_table already sorted, skipping sort
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Checking aperture...
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] No AGP bridge found
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Memory: 5886500k/7012352k available (6828k kernel code, 928492k absent, 197360k reserved, 6340k data, 948k init)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Hierarchical RCU implementation.
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] NR_IRQS:16640 nr_irqs:808 16
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Extended CMOS year: 2000
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Console: colour dummy device 80x25
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] console [tty0] enabled
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] allocated 25165824 bytes of page_cgroup
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] hpet clockevent registered
Nov 27 21:05:30 joomdevprojects kernel: [    0.000000] Fast TSC calibration using PIT
Nov 27 21:05:30 joomdevprojects kernel: [    0.008000] Detected 3192.017 MHz processor.
Nov 27 21:05:30 joomdevprojects kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6384.03 BogoMIPS (lpj=12768068)
Nov 27 21:05:30 joomdevprojects kernel: [    0.000009] pid_max: default: 32768 minimum: 301
Nov 28 22:14:30 joomdevprojects kernel: [    7.486297] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9703950
Nov 28 22:14:30 joomdevprojects kernel: [    7.486301] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9703960
Nov 28 22:14:30 joomdevprojects kernel: [    7.486305] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9703931
Nov 28 22:14:30 joomdevprojects kernel: [    7.486309] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9703865
Nov 28 22:14:30 joomdevprojects kernel: [    7.486313] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9703901
Nov 28 22:14:30 joomdevprojects kernel: [    7.486317] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9703943
Nov 28 22:14:30 joomdevprojects kernel: [    7.486327] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9703906
Nov 28 22:14:30 joomdevprojects kernel: [    7.486331] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9703945
Nov 28 22:14:30 joomdevprojects kernel: [    7.486335] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9703934
Nov 28 22:14:30 joomdevprojects kernel: [    7.486339] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9703922
Nov 28 22:14:30 joomdevprojects kernel: [    7.486342] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 9703917
Nov 28 22:14:30 joomdevprojects kernel: [    7.486346] EXT4-fs (sda1): 56 orphan inodes deleted
Nov 28 22:14:30 joomdevprojects kernel: [    7.486348] EXT4-fs (sda1): recovery complete
Nov 28 22:14:30 joomdevprojects kernel: [    7.598878] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Nov 28 22:14:30 joomdevprojects kernel: [   12.554079] hid-generic 0003:1A2C:0021.0002: usb_submit_urb(ctrl) failed: -1
Nov 28 22:14:30 joomdevprojects kernel: [   12.554125] hid-generic 0003:1A2C:0021.0002: timeout initializing reports
Nov 28 22:14:30 joomdevprojects kernel: [   12.554230] input: USB USB Keykoard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/input/input3
Nov 28 22:14:30 joomdevprojects kernel: [   12.554366] hid-generic 0003:1A2C:0021.0002: input,hidraw1: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:1a.0-1.3/input1
Nov 28 22:14:30 joomdevprojects kernel: [   25.739936] Adding 2001916k swap on /dev/sda5.  Priority:-1 extents:1 across:2001916k 
Nov 28 22:14:30 joomdevprojects kernel: [   26.194089] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Nov 28 22:14:30 joomdevprojects kernel: [   26.667043] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 28 22:14:30 joomdevprojects kernel: [   26.742943] lp: driver loaded but no devices found
Nov 28 22:14:30 joomdevprojects kernel: [   26.754646] mei 0000:00:16.0: setting latency timer to 64
Nov 28 22:14:30 joomdevprojects kernel: [   26.754717] mei 0000:00:16.0: irq 43 for MSI/MSI-X
Nov 28 22:14:30 joomdevprojects kernel: [   26.759346] Bluetooth: Core ver 2.16
Nov 28 22:14:30 joomdevprojects kernel: [   26.759364] NET: Registered protocol family 31
Nov 28 22:14:30 joomdevprojects kernel: [   26.759365] Bluetooth: HCI device and connection manager initialized
Nov 28 22:14:30 joomdevprojects kernel: [   26.759367] Bluetooth: HCI socket layer initialized
Nov 28 22:14:30 joomdevprojects kernel: [   26.759368] Bluetooth: L2CAP socket layer initialized
Nov 28 22:14:30 joomdevprojects kernel: [   26.759372] Bluetooth: SCO socket layer initialized
Nov 28 22:14:30 joomdevprojects kernel: [   26.760800] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov 28 22:14:30 joomdevprojects kernel: [   26.760805] Bluetooth: BNEP filters: protocol multicast
Nov 28 22:14:30 joomdevprojects kernel: [   26.764600] [drm] Initialized drm 1.1.0 20060810
Nov 28 22:14:30 joomdevprojects kernel: [   26.770242] Bluetooth: RFCOMM TTY layer initialized
Nov 28 22:14:30 joomdevprojects kernel: [   26.770249] Bluetooth: RFCOMM socket layer initialized
Nov 28 22:14:30 joomdevprojects kernel: [   26.770250] Bluetooth: RFCOMM ver 1.11
Nov 28 22:14:30 joomdevprojects kernel: [   26.796329] i915 0000:00:02.0: setting latency timer to 64
Nov 28 22:14:30 joomdevprojects kernel: [   26.797396] parport_pc 00:04: reported by Plug and Play ACPI
Nov 28 22:14:30 joomdevprojects kernel: [   26.797555] parport0: PC-style at 0x378 (0x778), irq 5, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Nov 28 22:14:30 joomdevprojects kernel: [   26.806067] ppdev: user-space parallel port driver
Nov 28 22:14:30 joomdevprojects kernel: [   26.830714] i915 0000:00:02.0: irq 44 for MSI/MSI-X
Nov 28 22:14:30 joomdevprojects kernel: [   26.830724] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Nov 28 22:14:30 joomdevprojects kernel: [   26.830726] [drm] Driver supports precise vblank timestamp query.
Nov 28 22:14:30 joomdevprojects kernel: [   26.830773] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Nov 28 22:14:30 joomdevprojects kernel: [   26.851387] microcode: CPU0 sig=0x20652, pf=0x2, revision=0x9
Nov 28 22:14:30 joomdevprojects kernel: [   26.891801] type=1400 audit(1385657070.713:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=709 comm="apparmor_parser"
Nov 28 22:14:30 joomdevprojects kernel: [   26.891810] type=1400 audit(1385657070.713:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=660 comm="apparmor_parser"
Nov 28 22:14:30 joomdevprojects kernel: [   26.892086] type=1400 audit(1385657070.713:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=709 comm="apparmor_parser"
Nov 28 22:14:30 joomdevprojects kernel: [   26.892108] type=1400 audit(1385657070.713:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
Nov 28 22:14:30 joomdevprojects kernel: [   26.892242] type=1400 audit(1385657070.713:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=709 comm="apparmor_parser"
Nov 28 22:14:30 joomdevprojects kernel: [   26.892302] type=1400 audit(1385657070.713:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=660 comm="apparmor_parser"
Nov 28 22:14:30 joomdevprojects kernel: [   26.902011] lp0: using parport0 (interrupt-driven).
Nov 28 22:14:30 joomdevprojects kernel: [   26.951270] type=1400 audit(1385657070.773:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=776 comm="apparmor_parser"
Nov 28 22:14:30 joomdevprojects kernel: [   26.951760] type=1400 audit(1385657070.773:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=776 comm="apparmor_parser"
Nov 28 22:14:30 joomdevprojects kernel: [   27.021630] No connectors reported connected with modes
Nov 28 22:14:30 joomdevprojects kernel: [   27.021639] [drm] Cannot find any crtc or sizes - going 1024x768
Nov 28 22:14:30 joomdevprojects kernel: [   27.029154] fbcon: inteldrmfb (fb0) is primary device
Nov 28 22:14:30 joomdevprojects kernel: [   27.029343] Console: switching to colour frame buffer device 128x48
Nov 28 22:14:30 joomdevprojects kernel: [   27.031474] fb0: inteldrmfb frame buffer device
Nov 28 22:14:30 joomdevprojects kernel: [   27.031476] drm: registered panic notifier
Nov 28 22:14:30 joomdevprojects kernel: [   27.031567] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20120320/video-1203)
Nov 28 22:14:30 joomdevprojects kernel: [   27.031573] ACPI: Video Device [GFX0] (multi-head: no  rom: yes  post: no)
Nov 28 22:14:30 joomdevprojects kernel: [   27.031709] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
Nov 28 22:14:30 joomdevprojects kernel: [   27.031817] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Nov 28 22:14:30 joomdevprojects kernel: [   27.031847] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \_SB_.PCI0.GFX0.TCOI 1 (20120320/utaddress-251)
Nov 28 22:14:30 joomdevprojects kernel: [   27.031852] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov 28 22:14:30 joomdevprojects kernel: [   27.031854] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
Nov 28 22:14:30 joomdevprojects kernel: [   27.031863] ACPI Warning: 0x0000000000000500-0x000000000000057f SystemIO conflicts with Region \_SB_.PCI0.SBRG.AY34 1 (20120320/utaddress-251)
Nov 28 22:14:30 joomdevprojects kernel: [   27.031866] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov 28 22:14:30 joomdevprojects kernel: [   27.031867] lpc_ich: Resource conflict(s) found affecting gpio_ich
Nov 28 22:14:30 joomdevprojects kernel: [   27.032071] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
Nov 28 22:14:30 joomdevprojects kernel: [   27.035767] microcode: CPU1 sig=0x20652, pf=0x2, revision=0x9
Nov 28 22:14:30 joomdevprojects kernel: [   27.036976] microcode: CPU2 sig=0x20652, pf=0x2, revision=0x9
Nov 28 22:14:30 joomdevprojects kernel: [   27.037866] microcode: CPU3 sig=0x20652, pf=0x2, revision=0x9
Nov 28 22:14:30 joomdevprojects kernel: [   27.041521] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Nov 28 22:14:30 joomdevprojects kernel: [   27.049079] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
Nov 28 22:14:30 joomdevprojects kernel: [   27.094209] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
Nov 28 22:14:30 joomdevprojects kernel: [   27.094341] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
Nov 28 22:14:30 joomdevprojects kernel: [   27.094442] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
Nov 28 22:14:30 joomdevprojects kernel: [   27.094537] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Nov 28 22:14:31 joomdevprojects kernel: [   27.250073] type=1400 audit(1385657071.073:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=920 comm="apparmor_parser"
Nov 28 22:14:31 joomdevprojects kernel: [   27.250423] type=1400 audit(1385657071.073:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=919 comm="apparmor_parser"
Nov 28 22:14:31 joomdevprojects kernel: [   27.296123] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
Nov 28 22:14:31 joomdevprojects kernel: [   27.396734] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
Nov 28 22:14:31 joomdevprojects kernel: [   27.397739] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov 28 22:14:31 joomdevprojects kernel: [   27.398107] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov 28 22:14:33 joomdevprojects kernel: [   29.423679] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx
Nov 28 22:14:33 joomdevprojects kernel: [   29.423687] e1000e 0000:00:19.0: eth1: 10/100 speed: disabling TSO
Nov 28 22:14:33 joomdevprojects kernel: [   29.424447] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Nov 28 22:19:39 joomdevprojects kernel: [  332.106520] audit_printk_skb: 54 callbacks suppressed
Nov 28 22:19:39 joomdevprojects kernel: [  332.106523] type=1400 audit(1385657379.745:30): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=783 comm="cupsd" pid=783 comm="cupsd" capability=36  capname="block_suspend"


```

---

### Post by efflandt on 2013-11-28
You seem to have a high load ave. probably from all those **find** processes competing for disk access from your cron script. So even though your CPU is not working that hard and not using that much memory, your system has to wait for the backlog of things trying to access the disk. What happens if you run that cron job less often?

---

### Post by chetanmadaan on 2013-11-29
The cron jobs where really running every 1 minute which i now changed to 5 mins...

also, there were around 10 - 12 or them and i now i changed back to like 5 or 6. so may be this is help... I would like to like explain what i was doing with cron job... just so if anyone wants to offer some help on that part too.

so, the Server is mostly used for CMS softwares i.e. Joomla, Wordpress... Now, the two reasons i run the cron jobs is to.

1. Make all the files chmod 664 and folder 775 (assuming that those are the permission a php script need to make things writable.
2. Once a file is uploaded via a php script the owner of the file is root:root... so i run the script to change the owner to user:www-data (this will make it writable for the particular FTP user and the PHP scripts will also be able to edit these).

Any idea how this could be automated without a cron job. I know cpanel has this kind of setting by default.

---

### Post by efflandt on 2013-11-29
If whatever is saving the files is running as root:root (do you really consider that safe?), can't that set ownership/permissions when each directory is created or file is saved, instead of constantly searching for them from cron?

I used to use Perl CGI scripts running as me with SUID C wrapper when I needed to be able to write to files from a webserver and only give the webserver or anyone else read permission (others). But I never got into php much, so cannot help with that.

---

### Post by chetanmadaan on 2013-11-29
Alright... i will find something.

Thanks Anyways!

---

