---
title: "Extremely slow boot"
date: 2016-01-23
forum: General Help
---

### Post by leo.2292 on 2016-01-23
Hi there. I recently installed Ubuntu 14.04 LTS on my laptop and it's great tough i think the boot is taking a long time to finish.
I've tried to remove a few programs that had services running on OS startup like VirtualBox to no avail, i don't have much knowledge on Linux, could someone help me out?

Thanks in advance.

[Bootchart image attached]

---

### Post by Petro Dawg on 2016-01-23
Try posting your boot log using code tags.  
```
 LIKE THIS 
```

Nobody will be able to make out anything in that picture at all.

---

### Post by leo.2292 on 2016-01-23
Sorry, just realized the image got too small.

Where can i find this boot log file ? Anyway here's the full image:

[http://pasteboard.co/11r4e9LS.png](http://pasteboard.co/11r4e9LS.png)

---

### Post by sandyd on 2016-01-23
According to bootchart, it takes 75s, which is reasonable.

Is it slow getting to the actual desktop? (i.e. after the login screen if you don't have auto-logins enabled)

---

### Post by Petro Dawg on 2016-01-23
There are several somewhat useful logs found in the /var/log folder.  "syslog" is time stamped and is sometimes useful to identify at what point you are getting hung up, if at all.

---

### Post by leo.2292 on 2016-01-24
>  Is it slow getting to the actual desktop? (i.e. after the login screen if you don't have auto-logins enabled)
- Yes, and the login screen seems to be a a bit slow as well.

> According to bootchart, it takes 75s, which is reasonable.
- Thats weird because i've used an older version of ubuntu on a less capable computer before and it was fine, boot times were faster than Windows.

I'll check the log files when i get the chance, thanks.

---

### Post by leo.2292 on 2016-01-24
Here's the log extracted from the syslog file, i hope it can help shed some light on this problem.

thanks

```
Jan 24 15:40:31 hugo-K46CA rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="985" x-info="http://www.rsyslog.com"] start
Jan 24 15:40:31 hugo-K46CA rsyslogd: rsyslogd's groupid changed to 104
Jan 24 15:40:31 hugo-K46CA rsyslogd: rsyslogd's userid changed to 101
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Linux version 3.19.0-47-generic (buildd@lgw01-19) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #53~14.04.1-Ubuntu SMP Mon Jan 18 16:09:14 UTC 2016 (Ubuntu 3.19.0-47.53~14.04.1-generic 3.19.8-ckt10)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-47-generic root=UUID=c7652e51-fedf-46e2-823a-3f665feaa14c ro quiet splash vt.handoff=7
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] KERNEL supported cpus:
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   Intel GenuineIntel
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   AMD AuthenticAMD
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   Centaur CentaurHauls
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000d973dfff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d973e000-0x00000000d9d3efff] ACPI NVS
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9d3f000-0x00000000d9d41fff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9d42000-0x00000000d9d58fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9d59000-0x00000000d9d5efff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9d5f000-0x00000000d9d60fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9d61000-0x00000000d9d6efff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9d6f000-0x00000000d9efcfff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9efd000-0x00000000d9f00fff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f01000-0x00000000d9f49fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f4a000-0x00000000d9f50fff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f51000-0x00000000d9f52fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f53000-0x00000000d9f5ffff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f60000-0x00000000d9f70fff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f71000-0x00000000d9f73fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f74000-0x00000000d9f75fff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f76000-0x00000000d9f8cfff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f8d000-0x00000000d9f92fff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f93000-0x00000000d9f9afff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f9b000-0x00000000d9f9bfff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9f9c000-0x00000000d9faafff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9fab000-0x00000000d9fabfff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9fac000-0x00000000d9fb6fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9fb7000-0x00000000d9fbbfff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9fbc000-0x00000000d9fdafff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9fdb000-0x00000000d9fdcfff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9fdd000-0x00000000d9fe9fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9fea000-0x00000000d9feafff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9feb000-0x00000000d9ffcfff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000d9ffd000-0x00000000da022fff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da023000-0x00000000da036fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da037000-0x00000000da037fff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da038000-0x00000000da038fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da039000-0x00000000da03afff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da03b000-0x00000000da03bfff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da03c000-0x00000000da040fff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da041000-0x00000000da054fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da055000-0x00000000da0d5fff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da0d6000-0x00000000da0f0fff] type 20
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da0f1000-0x00000000da61afff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da61b000-0x00000000da89afff] ACPI NVS
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da89b000-0x00000000da89ffff] ACPI data
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da8a0000-0x00000000da8a0fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da8a1000-0x00000000da8e3fff] ACPI NVS
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000da8e4000-0x00000000dacf0fff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000dacf1000-0x00000000daff3fff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000daff4000-0x00000000daffffff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000dbc00000-0x00000000dfdfffff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021f1fffff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] NX (Execute Disable) protection: active
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] efi: EFI v2.31 by American Megatrends
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] efi:  ACPI=0xda86f000  ACPI 2.0=0xda86f000  SMBIOS=0xf04c0  MPS=0xfd4c0 
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] SMBIOS 2.7 present.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] DMI: ASUSTeK COMPUTER INC. K46CA/K46CA, BIOS K46CA.315 05/17/2013
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] AGP: No AGP bridge found
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] e820: last_pfn = 0x21f200 max_arch_pfn = 0x400000000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] MTRR default type: uncachable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] MTRR fixed ranges enabled:
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   00000-9FFFF write-back
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   A0000-BFFFF uncachable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   C0000-D3FFF write-protect
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   D4000-DFFFF uncachable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   E0000-FFFFF write-protect
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] MTRR variable ranges enabled:
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   1 base 200000000 mask FE0000000 write-back
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   4 base 0DBC00000 mask FFFC00000 uncachable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   5 base 21F800000 mask FFF800000 uncachable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   6 base 21F400000 mask FFFC00000 uncachable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   7 base 21F200000 mask FFFE00000 uncachable
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   8 disabled
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   9 disabled
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] original variable MTRRs
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] reg 0, base: 0GB, range: 8GB, type WB
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] reg 1, base: 8GB, range: 512MB, type WB
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] reg 4, base: 3516MB, range: 4MB, type UC
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] reg 5, base: 8696MB, range: 8MB, type UC
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] reg 6, base: 8692MB, range: 4MB, type UC
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] reg 7, base: 8690MB, range: 2MB, type UC
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] total RAM covered: 8110M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 50M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 50M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 50M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 50M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 50M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 50M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 242M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 50M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: 50M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 4M     chunk_size: 32M     num_reg: 9      lose cover RAM: 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 4M     chunk_size: 64M     num_reg: 9      lose cover RAM: 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 4M     chunk_size: 128M     num_reg: 8      lose cover RAM: 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 4M     chunk_size: 256M     num_reg: 8      lose cover RAM: 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 4M     chunk_size: 512M     num_reg: 8      lose cover RAM: 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 4M     chunk_size: 1G     num_reg: 8      lose cover RAM: 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 4M     chunk_size: 2G     num_reg: 9      lose cover RAM: 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 118M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 54M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 9      lose cover RAM: 6M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 9      lose cover RAM: 6M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 8      lose cover RAM: 6M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 8      lose cover RAM: 6M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 8M     chunk_size: 512M     num_reg: 8      lose cover RAM: 6M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 8      lose cover RAM: 6M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 8M     chunk_size: 2G     num_reg: 9      lose cover RAM: 6M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 62M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 9      lose cover RAM: 14M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 9      lose cover RAM: 14M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 8      lose cover RAM: 14M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 8      lose cover RAM: 14M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 16M     chunk_size: 512M     num_reg: 8      lose cover RAM: 14M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 8      lose cover RAM: 14M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 16M     chunk_size: 2G     num_reg: 9      lose cover RAM: 14M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 10      lose cover RAM: 46M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 9      lose cover RAM: 46M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 8      lose cover RAM: 46M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 8      lose cover RAM: 46M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 32M     chunk_size: 512M     num_reg: 8      lose cover RAM: 46M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 8      lose cover RAM: 46M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 32M     chunk_size: 2G     num_reg: 9      lose cover RAM: 46M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 8      lose cover RAM: 110M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 7      lose cover RAM: 110M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 7      lose cover RAM: 110M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 7      lose cover RAM: 110M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 7      lose cover RAM: 110M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 8      lose cover RAM: 110M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 7      lose cover RAM: 174M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 7      lose cover RAM: 174M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 7      lose cover RAM: 174M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 7      lose cover RAM: 174M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 8      lose cover RAM: 174M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 5      lose cover RAM: 430M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 7      lose cover RAM: 430M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 7      lose cover RAM: 430M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 8      lose cover RAM: 430M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 3      lose cover RAM: 942M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 3      lose cover RAM: 942M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 3      lose cover RAM: 942M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 3      lose cover RAM: 942M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 3      lose cover RAM: 942M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 2      lose cover RAM: 1966M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] mtrr_cleanup: can not find optimal value
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] e820: update [mem 0xdbc00000-0xffffffff] usable ==> reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] e820: last_pfn = 0xdb000 max_arch_pfn = 0x400000000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] found SMP MP-table at [mem 0x000fd7b0-0x000fd7bf] mapped at [ffff8800000fd7b0]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0x21f000000-0x21f1fffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0x21f000000-0x21f1fffff] page 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0x200000000-0x21effffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0x200000000-0x21effffff] page 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0x1e0000000-0x1ffffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0x1e0000000-0x1ffffffff] page 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BRK [0x01fd8000, 0x01fd8fff] PGTABLE
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0x40000000-0x40003fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0x40005000-0xd973dfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0x40005000-0x401fffff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0x40200000-0xd95fffff] page 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9600000-0xd973dfff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9d42000-0xd9d58fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9d42000-0xd9d58fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9d5f000-0xd9d60fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9d5f000-0xd9d60fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9d6f000-0xd9efcfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9d6f000-0xd9efcfff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9f01000-0xd9f49fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9f01000-0xd9f49fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9f51000-0xd9f52fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9f51000-0xd9f52fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9f71000-0xd9f73fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9f71000-0xd9f73fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9f76000-0xd9f8cfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9f76000-0xd9f8cfff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9f93000-0xd9f9afff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9f93000-0xd9f9afff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9f9c000-0xd9faafff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9f9c000-0xd9faafff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9fac000-0xd9fb6fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9fac000-0xd9fb6fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9fbc000-0xd9fdafff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9fbc000-0xd9fdafff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9fdd000-0xd9fe9fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9fdd000-0xd9fe9fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xd9feb000-0xd9ffcfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xd9feb000-0xd9ffcfff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xda023000-0xda036fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xda023000-0xda036fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xda038000-0xda038fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xda038000-0xda038fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xda03b000-0xda03bfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xda03b000-0xda03bfff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xda041000-0xda054fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xda041000-0xda054fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xda8a0000-0xda8a0fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xda8a0000-0xda8a0fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xda8e4000-0xdacf0fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xda8e4000-0xda9fffff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xdaa00000-0xdabfffff] page 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xdac00000-0xdacf0fff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0xdaff4000-0xdaffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0xdaff4000-0xdaffffff] page 4k
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x1dfffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [mem 0x100000000-0x1dfffffff] page 2M
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] RAMDISK: [mem 0x3470e000-0x3637efff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: Early table checksum verification disabled
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: RSDP 0x00000000DA86F000 000024 (v02 _ASUS_)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: XSDT 0x00000000DA86F090 0000AC (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: FACP 0x00000000DA87FE00 00010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: DSDT 0x00000000DA86F1D0 010C2F (v02 _ASUS_ Notebook 00000013 INTL 20091112)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: FACS 0x00000000DA898080 000040
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: APIC 0x00000000DA87FF10 000072 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: FPDT 0x00000000DA87FF88 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: ECDT 0x00000000DA87FFD0 0000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: MCFG 0x00000000DA880098 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: SSDT 0x00000000DA8800D8 000A3C (v01 DptfTa DptfTab  00001000 INTL 20091112)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: SSDT 0x00000000DA880B18 000CA5 (v01 SADptf SADptf_  00001000 INTL 20091112)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: SSDT 0x00000000DA8817C0 000098 (v01 PchDpt PchDptf  00001000 INTL 20091112)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: SSDT 0x00000000DA881858 00091C (v01 CfgTDP CfgTDP_  00001000 INTL 20091112)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: HPET 0x00000000DA882178 000038 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: SSDT 0x00000000DA8821B0 00066E (v01 AhciR1 AhciTab1 00001000 INTL 20091112)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: SSDT 0x00000000DA882820 00049E (v01 AhciR2 AhciTab2 00001000 INTL 20091112)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: SSDT 0x00000000DA882CC0 000886 (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: SSDT 0x00000000DA883548 000A92 (v01 PmRef  CpuPm    00003000 INTL 20051117)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: DMAR 0x00000000DA883FE0 0000B8 (v01 INTEL  SNB      00000001 INTL 00000001)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: SSDT 0x00000000DA884098 0000D0 (v01 Iffs   IffsAsl  00003000 INTL 20051117)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: MSDM 0x00000000DA61AE18 000055 (v03 _ASUS_ Notebook 00000000 ASUS 00000001)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] No NUMA configuration found
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021f1fffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x21f1ee000-0x21f1f2fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880216800000-ffff88021e7fffff] on node 0
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Zone ranges:
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   Normal   [mem 0x100000000-0x21f1fffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Movable zone start for each node
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Early memory node ranges
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009efff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0x20200000-0x40003fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0x40005000-0xd973dfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9d42000-0xd9d58fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9d5f000-0xd9d60fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9d6f000-0xd9efcfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9f01000-0xd9f49fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9f51000-0xd9f52fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9f71000-0xd9f73fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9f76000-0xd9f8cfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9f93000-0xd9f9afff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9f9c000-0xd9faafff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9fac000-0xd9fb6fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9fbc000-0xd9fdafff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9fdd000-0xd9fe9fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xd9feb000-0xd9ffcfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xda023000-0xda036fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xda038000-0xda038fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xda03b000-0xda03bfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xda041000-0xda054fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xda8a0000-0xda8a0fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xda8e4000-0xdacf0fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0xdaff4000-0xdaffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   node   0: [mem 0x100000000-0x21f1fffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Initmem setup node 0 [mem 0x00001000-0x21f1fffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] On node 0 totalpages: 2067851
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   DMA zone: 27 pages reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   DMA32 zone: 13872 pages used for memmap
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   DMA32 zone: 887789 pages, LIFO batch:31
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   Normal zone: 18376 pages used for memmap
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]   Normal zone: 1176064 pages, LIFO batch:31
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Reserving Intel graphics stolen memory at 0xdbe00000-0xdfdfffff
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd973e000-0xd9d3efff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9d3f000-0xd9d41fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9d59000-0xd9d5efff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9d61000-0xd9d6efff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9efd000-0xd9f00fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9f4a000-0xd9f50fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9f53000-0xd9f5ffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9f60000-0xd9f70fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9f74000-0xd9f75fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9f8d000-0xd9f92fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9f9b000-0xd9f9bfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9fab000-0xd9fabfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9fb7000-0xd9fbbfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9fdb000-0xd9fdcfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9fea000-0xd9feafff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xd9ffd000-0xda022fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xda037000-0xda037fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xda039000-0xda03afff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xda03c000-0xda040fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xda055000-0xda0d5fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xda0d6000-0xda0f0fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xda0f1000-0xda61afff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xda61b000-0xda89afff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xda89b000-0xda89ffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xda8a1000-0xda8e3fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdacf1000-0xdaff3fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdb000000-0xdbbfffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdbc00000-0xdfdfffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xdfe00000-0xf7ffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] e820: [mem 0xdfe00000-0xf7ffffff] available for PCI devices
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PERCPU: Embedded 31 pages/cpu @ffff88021ee00000 s86144 r8192 d32640 u524288
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] pcpu-alloc: s86144 r8192 d32640 u524288 alloc=1*2097152
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 2035512
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Policy zone: Normal
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-47-generic root=UUID=c7652e51-fedf-46e2-823a-3f665feaa14c ro quiet splash vt.handoff=7
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340 using standard form
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] AGP: Checking aperture...
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] AGP: No AGP bridge found
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Memory: 7847716K/8271404K available (7922K kernel code, 1174K rwdata, 3756K rodata, 1408K init, 1292K bss, 423688K reserved, 0K cma-reserved)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Hierarchical RCU implementation.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] NR_IRQS:16640 nr_irqs:456 16
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] Console: colour dummy device 80x25
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] console [tty0] enabled
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] hpet clockevent registered
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000000] tsc: Detected 1696.085 MHz processor
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000050] Calibrating delay loop (skipped), value calculated using timer frequency.. 3392.17 BogoMIPS (lpj=6784340)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000054] pid_max: default: 32768 minimum: 301
Jan 24 15:40:31 hugo-K46CA kernel: [    0.000061] ACPI: Core revision 20141107
Jan 24 15:40:31 hugo-K46CA kernel: [    0.023753] ACPI: All ACPI Tables successfully acquired
Jan 24 15:40:31 hugo-K46CA kernel: [    0.024957] Security Framework initialized
Jan 24 15:40:31 hugo-K46CA kernel: [    0.024978] AppArmor: AppArmor initialized
Jan 24 15:40:31 hugo-K46CA kernel: [    0.024979] Yama: becoming mindful.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.025736] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.028800] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030156] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030171] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030445] Initializing cgroup subsys memory
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030452] Initializing cgroup subsys devices
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030455] Initializing cgroup subsys freezer
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030458] Initializing cgroup subsys net_cls
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030460] Initializing cgroup subsys blkio
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030463] Initializing cgroup subsys perf_event
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030466] Initializing cgroup subsys net_prio
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030468] Initializing cgroup subsys hugetlb
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030501] CPU: Physical Processor ID: 0
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030503] CPU: Processor Core ID: 0
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030509] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Jan 24 15:40:31 hugo-K46CA kernel: [    0.030509] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.031082] mce: CPU supports 7 MCE banks
Jan 24 15:40:31 hugo-K46CA kernel: [    0.031097] CPU0: Thermal monitoring enabled (TM1)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.031106] process: using mwait in idle threads
Jan 24 15:40:31 hugo-K46CA kernel: [    0.031111] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
Jan 24 15:40:31 hugo-K46CA kernel: [    0.031111] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
Jan 24 15:40:31 hugo-K46CA kernel: [    0.031286] Freeing SMP alternatives memory: 32K (ffffffff81e87000 - ffffffff81e8f000)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.041291] ftrace: allocating 30027 entries in 118 pages
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061513] dmar: Host address width 36
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061517] dmar: DRHD base: 0x000000fed90000 flags: 0x0
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061528] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061529] dmar: DRHD base: 0x000000fed91000 flags: 0x1
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061537] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061539] dmar: RMRR base: 0x000000da34d000 end: 0x000000da369fff
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061541] dmar: RMRR base: 0x000000dbc00000 end: 0x000000dfdfffff
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061615] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061617] HPET id 0 under DRHD base 0xfed91000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061618] Queued invalidation will be enabled to support x2apic and Intr-remapping.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061829] Enabled IRQ remapping in x2apic mode
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061831] Enabling x2apic
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061832] Enabled x2apic
Jan 24 15:40:31 hugo-K46CA kernel: [    0.061839] Switched APIC routing to cluster x2apic.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.062323] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 24 15:40:31 hugo-K46CA kernel: [    0.102026] smpboot: CPU0: Intel(R) Core(TM) i5-3317U CPU @ 1.70GHz (fam: 06, model: 3a, stepping: 09)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.102036] TSC deadline timer enabled
Jan 24 15:40:31 hugo-K46CA kernel: [    0.102069] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.102097] ... version:                3
Jan 24 15:40:31 hugo-K46CA kernel: [    0.102099] ... bit width:              48
Jan 24 15:40:31 hugo-K46CA kernel: [    0.102100] ... generic registers:      4
Jan 24 15:40:31 hugo-K46CA kernel: [    0.102101] ... value mask:             0000ffffffffffff
Jan 24 15:40:31 hugo-K46CA kernel: [    0.102102] ... max period:             0000ffffffffffff
Jan 24 15:40:31 hugo-K46CA kernel: [    0.102104] ... fixed-purpose events:   3
Jan 24 15:40:31 hugo-K46CA kernel: [    0.102105] ... event mask:             000000070000000f
Jan 24 15:40:31 hugo-K46CA kernel: [    0.103331] x86: Booting SMP configuration:
Jan 24 15:40:31 hugo-K46CA kernel: [    0.103334] .... node  #0, CPUs:      #1
Jan 24 15:40:31 hugo-K46CA kernel: [    0.117047] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.117179]  #2 #3
Jan 24 15:40:31 hugo-K46CA kernel: [    0.144695] x86: Booted up 1 node, 4 CPUs
Jan 24 15:40:31 hugo-K46CA kernel: [    0.144699] smpboot: Total of 4 processors activated (13568.68 BogoMIPS)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.149171] devtmpfs: initialized
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153388] evm: security.selinux
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153390] evm: security.SMACK64
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153391] evm: security.SMACK64EXEC
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153392] evm: security.SMACK64TRANSMUTE
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153393] evm: security.SMACK64MMAP
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153395] evm: security.ima
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153396] evm: security.capability
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153471] PM: Registering ACPI NVS region [mem 0xd973e000-0xd9d3efff] (6295552 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153573] PM: Registering ACPI NVS region [mem 0xda61b000-0xda89afff] (2621440 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153615] PM: Registering ACPI NVS region [mem 0xda8a1000-0xda8e3fff] (274432 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153817] pinctrl core: initialized pinctrl subsystem
Jan 24 15:40:31 hugo-K46CA kernel: [    0.153953] RTC time: 17:40:08, date: 01/24/16
Jan 24 15:40:31 hugo-K46CA kernel: [    0.154092] NET: Registered protocol family 16
Jan 24 15:40:31 hugo-K46CA kernel: [    0.156965] cpuidle: using governor ladder
Jan 24 15:40:31 hugo-K46CA kernel: [    0.160952] cpuidle: using governor menu
Jan 24 15:40:31 hugo-K46CA kernel: [    0.161036] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Jan 24 15:40:31 hugo-K46CA kernel: [    0.161038] ACPI: bus type PCI registered
Jan 24 15:40:31 hugo-K46CA kernel: [    0.161040] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Jan 24 15:40:31 hugo-K46CA kernel: [    0.161137] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.161141] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Jan 24 15:40:31 hugo-K46CA kernel: [    0.161259] PCI: Using configuration type 1 for base access
Jan 24 15:40:31 hugo-K46CA kernel: [    0.165487] ACPI: Added _OSI(Module Device)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.165490] ACPI: Added _OSI(Processor Device)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.165492] ACPI: Added _OSI(3.0 _SCP Extensions)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.165493] ACPI: Added _OSI(Processor Aggregator Device)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.168464] ACPI : EC: EC description table is found, configuring boot EC
Jan 24 15:40:31 hugo-K46CA kernel: [    0.171524] ACPI: Executed 1 blocks of module-level executable AML code
Jan 24 15:40:31 hugo-K46CA kernel: [    0.175885] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan 24 15:40:31 hugo-K46CA kernel: [    0.176406] ACPI: Dynamic OEM Table Load:
Jan 24 15:40:31 hugo-K46CA kernel: [    0.176418] ACPI: SSDT 0xFFFF880215359000 000853 (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.177478] ACPI: Dynamic OEM Table Load:
Jan 24 15:40:31 hugo-K46CA kernel: [    0.177486] ACPI: SSDT 0xFFFF88021533A800 000303 (v01 PmRef  ApIst    00003000 INTL 20051117)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.178433] ACPI: Dynamic OEM Table Load:
Jan 24 15:40:31 hugo-K46CA kernel: [    0.178439] ACPI: SSDT 0xFFFF880215335E00 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.180010] ACPI: Interpreter enabled
Jan 24 15:40:31 hugo-K46CA kernel: [    0.180020] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.180027] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.180048] ACPI: (supports S0 S3 S4 S5)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.180050] ACPI: Using IOAPIC for interrupt routing
Jan 24 15:40:31 hugo-K46CA kernel: [    0.180086] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jan 24 15:40:31 hugo-K46CA kernel: [    0.189640] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Jan 24 15:40:31 hugo-K46CA kernel: [    0.189648] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.189973] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.190165] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.190168] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191113] PCI host bridge to bus 0000:00
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191118] pci_bus 0000:00: root bus resource [bus 00-3e]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191120] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191123] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191125] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191127] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191129] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191131] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191134] pci_bus 0000:00: root bus resource [mem 0xdfe00000-0xfeafffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191144] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191275] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191291] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191300] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191307] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191433] pci 0000:00:04.0: [8086:0153] type 00 class 0x118000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191447] pci 0000:00:04.0: reg 0x10: [mem 0xfed98000-0xfed9ffff 64bit]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191615] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191643] pci 0000:00:14.0: reg 0x10: [mem 0xf7e00000-0xf7e0ffff 64bit]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191737] pci 0000:00:14.0: PME# supported from D3hot D3cold
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191801] pci 0000:00:14.0: System wakeup disabled by ACPI
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191857] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191888] pci 0000:00:16.0: reg 0x10: [mem 0xf7e22000-0xf7e2200f 64bit]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.191982] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Jan 24 15:40:31 hugo-K46CA kernel: [    0.192109] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
Jan 24 15:40:31 hugo-K46CA kernel: [    0.192135] pci 0000:00:1a.0: reg 0x10: [mem 0xf7e20000-0xf7e203ff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.192246] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Jan 24 15:40:31 hugo-K46CA kernel: [    0.192311] pci 0000:00:1a.0: System wakeup disabled by ACPI
Jan 24 15:40:31 hugo-K46CA kernel: [    0.192366] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
Jan 24 15:40:31 hugo-K46CA kernel: [    0.192387] pci 0000:00:1b.0: reg 0x10: [mem 0xf7e18000-0xf7e1bfff 64bit]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.192481] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan 24 15:40:31 hugo-K46CA kernel: [    0.192546] pci 0000:00:1b.0: System wakeup disabled by ACPI
Jan 24 15:40:31 hugo-K46CA kernel: [    0.192596] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
Jan 24 15:40:31 hugo-K46CA kernel: [    0.192703] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan 24 15:40:31 hugo-K46CA kernel: [    0.192814] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
Jan 24 15:40:31 hugo-K46CA kernel: [    0.258636] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jan 24 15:40:31 hugo-K46CA kernel: [    0.258756] pci 0000:00:1c.3: [8086:1e16] type 01 class 0x060400
Jan 24 15:40:31 hugo-K46CA kernel: [    0.258863] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jan 24 15:40:31 hugo-K46CA kernel: [    0.258931] pci 0000:00:1c.3: System wakeup disabled by ACPI
Jan 24 15:40:31 hugo-K46CA kernel: [    0.258996] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259025] pci 0000:00:1d.0: reg 0x10: [mem 0xf7e1f000-0xf7e1f3ff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259140] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259203] pci 0000:00:1d.0: System wakeup disabled by ACPI
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259255] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259480] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259506] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259517] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259528] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259538] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259548] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259559] pci 0000:00:1f.2: reg 0x24: [mem 0xf7e1e000-0xf7e1e7ff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259620] pci 0000:00:1f.2: PME# supported from D3hot
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259725] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259746] pci 0000:00:1f.3: reg 0x10: [mem 0xf7e1d000-0xf7e1d0ff 64bit]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259774] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.259979] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.260107] pci 0000:02:00.0: [168c:0032] type 00 class 0x028000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.260144] pci 0000:02:00.0: reg 0x10: [mem 0xf7d00000-0xf7d7ffff 64bit]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.260217] pci 0000:02:00.0: reg 0x30: [mem 0xf7d80000-0xf7d8ffff pref]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.260317] pci 0000:02:00.0: supports D1 D2
Jan 24 15:40:31 hugo-K46CA kernel: [    0.260320] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 24 15:40:31 hugo-K46CA kernel: [    0.260358] pci 0000:02:00.0: System wakeup disabled by ACPI
Jan 24 15:40:31 hugo-K46CA kernel: [    0.266666] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.266675] pci 0000:00:1c.1:   bridge window [mem 0xf7d00000-0xf7dfffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.266792] pci 0000:03:00.0: [10ec:5289] type 00 class 0xff0000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.266820] pci 0000:03:00.0: reg 0x10: [mem 0xf7c00000-0xf7c0ffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.267017] pci 0000:03:00.0: supports D1 D2
Jan 24 15:40:31 hugo-K46CA kernel: [    0.267019] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
Jan 24 15:40:31 hugo-K46CA kernel: [    0.267124] pci 0000:03:00.2: [10ec:8168] type 00 class 0x020000
Jan 24 15:40:31 hugo-K46CA kernel: [    0.267151] pci 0000:03:00.2: reg 0x10: [io  0xe000-0xe0ff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.267191] pci 0000:03:00.2: reg 0x18: [mem 0xf0004000-0xf0004fff 64bit pref]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.267217] pci 0000:03:00.2: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.267335] pci 0000:03:00.2: supports D1 D2
Jan 24 15:40:31 hugo-K46CA kernel: [    0.267337] pci 0000:03:00.2: PME# supported from D0 D1 D2 D3hot D3cold
Jan 24 15:40:31 hugo-K46CA kernel: [    0.267378] pci 0000:03:00.2: System wakeup disabled by ACPI
Jan 24 15:40:31 hugo-K46CA kernel: [    0.274683] pci 0000:00:1c.3: PCI bridge to [bus 03]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.274689] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.274694] pci 0000:00:1c.3:   bridge window [mem 0xf7c00000-0xf7cfffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.274702] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.275587] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.275653] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 12)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.275716] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 12)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.275778] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 12)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.275839] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.275901] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.275963] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 12)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276023] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 10 12)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276271] ACPI: Enabled 4 GPEs in block 00 to 3F
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276365] ACPI : EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276493] vgaarb: setting as boot device: PCI:0000:00:02.0
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276495] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276499] vgaarb: loaded
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276501] vgaarb: bridge control possible 0000:00:02.0
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276805] SCSI subsystem initialized
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276868] libata version 3.00 loaded.
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276902] ACPI: bus type USB registered
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276925] usbcore: registered new interface driver usbfs
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276936] usbcore: registered new interface driver hub
Jan 24 15:40:31 hugo-K46CA kernel: [    0.276960] usbcore: registered new device driver usb
Jan 24 15:40:31 hugo-K46CA kernel: [    0.277297] PCI: Using ACPI for IRQ routing
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279183] PCI: pci_cache_line_size set to 64 bytes
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279193] pci 0000:00:04.0: can't claim BAR 0 [mem 0xfed98000-0xfed9ffff 64bit]: no compatible bridge window
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279264] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279266] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279268] e820: reserve RAM buffer [mem 0xd973e000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279278] e820: reserve RAM buffer [mem 0xd9d59000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279288] e820: reserve RAM buffer [mem 0xd9d61000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279297] e820: reserve RAM buffer [mem 0xd9efd000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279306] e820: reserve RAM buffer [mem 0xd9f4a000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279315] e820: reserve RAM buffer [mem 0xd9f53000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279324] e820: reserve RAM buffer [mem 0xd9f74000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279332] e820: reserve RAM buffer [mem 0xd9f8d000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279340] e820: reserve RAM buffer [mem 0xd9f9b000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279348] e820: reserve RAM buffer [mem 0xd9fab000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279355] e820: reserve RAM buffer [mem 0xd9fb7000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279362] e820: reserve RAM buffer [mem 0xd9fdb000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279369] e820: reserve RAM buffer [mem 0xd9fea000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279375] e820: reserve RAM buffer [mem 0xd9ffd000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279381] e820: reserve RAM buffer [mem 0xda037000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279387] e820: reserve RAM buffer [mem 0xda039000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279392] e820: reserve RAM buffer [mem 0xda03c000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279397] e820: reserve RAM buffer [mem 0xda055000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279401] e820: reserve RAM buffer [mem 0xda8a1000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279404] e820: reserve RAM buffer [mem 0xdacf1000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279407] e820: reserve RAM buffer [mem 0xdb000000-0xdbffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279409] e820: reserve RAM buffer [mem 0x21f200000-0x21fffffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279550] NetLabel: Initializing
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279552] NetLabel:  domain hash size = 128
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279553] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279571] NetLabel:  unlabeled traffic allowed by default
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279661] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Jan 24 15:40:31 hugo-K46CA kernel: [    0.279668] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Jan 24 15:40:31 hugo-K46CA kernel: [    0.281715] Switched to clocksource hpet
Jan 24 15:40:31 hugo-K46CA kernel: [    0.288884] AppArmor: AppArmor Filesystem Enabled
Jan 24 15:40:31 hugo-K46CA kernel: [    0.288973] pnp: PnP ACPI init
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289100] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289105] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289269] system 00:01: [io  0x0680-0x069f] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289272] system 00:01: [io  0x1000-0x100f] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289275] system 00:01: [io  0xffff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289277] system 00:01: [io  0xffff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289280] system 00:01: [io  0x0400-0x0453] could not be reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289283] system 00:01: [io  0x0458-0x047f] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289285] system 00:01: [io  0x0500-0x057f] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289288] system 00:01: [io  0x164e-0x164f] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289291] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289337] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289404] system 00:03: [io  0x0454-0x0457] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289408] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289477] system 00:04: [io  0x04d0-0x04d1] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289480] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289561] pnp 00:05: Plug and Play ACPI device, IDs ETD0108 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289616] pnp 00:06: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289877] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289880] system 00:07: [mem 0xfed10000-0xfed17fff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289883] system 00:07: [mem 0xfed18000-0xfed18fff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289886] system 00:07: [mem 0xfed19000-0xfed19fff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289888] system 00:07: [mem 0xf8000000-0xfbffffff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289891] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289894] system 00:07: [mem 0xfed90000-0xfed93fff] could not be reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289897] system 00:07: [mem 0xfed45000-0xfed8ffff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289900] system 00:07: [mem 0xff000000-0xffffffff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289902] system 00:07: [mem 0xfee00000-0xfeefffff] could not be reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289905] system 00:07: [mem 0xdfe00000-0xdfe00fff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.289908] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.290004] system 00:08: [mem 0xdfe00000-0xdfe00fff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.290007] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.290196] system 00:09: [mem 0x20000000-0x201fffff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.290199] system 00:09: [mem 0x40004000-0x40004fff] has been reserved
Jan 24 15:40:31 hugo-K46CA kernel: [    0.290202] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.290248] pnp: PnP ACPI: found 10 devices
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297210] pci 0000:00:04.0: BAR 0: assigned [mem 0xdfe08000-0xdfe0ffff 64bit]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297219] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297237] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297244] pci 0000:00:1c.1:   bridge window [mem 0xf7d00000-0xf7dfffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297256] pci 0000:00:1c.3: PCI bridge to [bus 03]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297260] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297267] pci 0000:00:1c.3:   bridge window [mem 0xf7c00000-0xf7cfffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297273] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297283] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297286] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297288] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297291] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297293] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297295] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297298] pci_bus 0000:00: resource 10 [mem 0xdfe00000-0xfeafffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297300] pci_bus 0000:02: resource 1 [mem 0xf7d00000-0xf7dfffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297303] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297305] pci_bus 0000:03: resource 1 [mem 0xf7c00000-0xf7cfffff]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297308] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297343] NET: Registered protocol family 2
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297580] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297803] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297948] TCP: Hash tables configured (established 65536 bind 65536)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297969] TCP: reno registered
Jan 24 15:40:31 hugo-K46CA kernel: [    0.297983] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.298024] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    0.298103] NET: Registered protocol family 1
Jan 24 15:40:31 hugo-K46CA kernel: [    0.298125] pci 0000:00:02.0: Video device with shadowed ROM
Jan 24 15:40:31 hugo-K46CA kernel: [    0.337897] PCI: CLS 64 bytes, default 64
Jan 24 15:40:31 hugo-K46CA kernel: [    0.337973] Trying to unpack rootfs image as initramfs...
Jan 24 15:40:31 hugo-K46CA kernel: [    1.010146] Freeing initrd memory: 29124K (ffff88003470e000 - ffff88003637f000)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.010189] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.010193] software IO TLB [mem 0xca773000-0xce773000] (64MB) mapped at [ffff8800ca773000-ffff8800ce772fff]
Jan 24 15:40:31 hugo-K46CA kernel: [    1.010443] RAPL PMU detected, hw unit 2^-16 Joules, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
Jan 24 15:40:31 hugo-K46CA kernel: [    1.010561] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x12
Jan 24 15:40:31 hugo-K46CA kernel: [    1.010571] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x12
Jan 24 15:40:31 hugo-K46CA kernel: [    1.010582] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x12
Jan 24 15:40:31 hugo-K46CA kernel: [    1.010594] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x12
Jan 24 15:40:31 hugo-K46CA kernel: [    1.010657] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jan 24 15:40:31 hugo-K46CA kernel: [    1.010696] Scanning for low memory corruption every 60 seconds
Jan 24 15:40:31 hugo-K46CA kernel: [    1.011123] futex hash table entries: 1024 (order: 4, 65536 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.011144] Initialise system trusted keyring
Jan 24 15:40:31 hugo-K46CA kernel: [    1.011175] audit: initializing netlink subsys (disabled)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.011194] audit: type=2000 audit(1453657207.936:1): initialized
Jan 24 15:40:31 hugo-K46CA kernel: [    1.011686] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan 24 15:40:31 hugo-K46CA kernel: [    1.013681] zpool: loaded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.013686] zbud: loaded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.013900] VFS: Disk quotas dquot_6.5.2
Jan 24 15:40:31 hugo-K46CA kernel: [    1.013946] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.014564] fuse init (API version 7.23)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.014751] Key type big_key registered
Jan 24 15:40:31 hugo-K46CA kernel: [    1.015279] Key type asymmetric registered
Jan 24 15:40:31 hugo-K46CA kernel: [    1.015283] Asymmetric key parser 'x509' registered
Jan 24 15:40:31 hugo-K46CA kernel: [    1.015334] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.015387] io scheduler noop registered
Jan 24 15:40:31 hugo-K46CA kernel: [    1.015392] io scheduler deadline registered (default)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.015447] io scheduler cfq registered
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016073] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016096] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016150] efifb: probing for efifb
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016174] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90004e80000, using 3072k, total 3072k
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016176] efifb: mode is 1024x768x32, linelength=4096, pages=1
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016177] efifb: scrolling: redraw
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016180] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016292] Console: switching to colour frame buffer device 128x48
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016312] fb0: EFI VGA frame buffer device
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016325] intel_idle: MWAIT substates: 0x21120
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016327] intel_idle: v0.4 model 0x3A
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016329] intel_idle: lapic_timer_reliable_states 0xffffffff
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016669] ACPI: AC Adapter [AC0] (off-line)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.016821] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.038217] ACPI: Lid Switch [LID]
Jan 24 15:40:31 hugo-K46CA kernel: [    1.038275] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Jan 24 15:40:31 hugo-K46CA kernel: [    1.038280] ACPI: Sleep Button [SLPB]
Jan 24 15:40:31 hugo-K46CA kernel: [    1.038327] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jan 24 15:40:31 hugo-K46CA kernel: [    1.038330] ACPI: Power Button [PWRF]
Jan 24 15:40:31 hugo-K46CA kernel: [    1.039392] thermal LNXTHERM:00: registered as thermal_zone0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.039395] ACPI: Thermal Zone [THRM] (41 C)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.039445] GHES: HEST is not enabled!
Jan 24 15:40:31 hugo-K46CA kernel: [    1.039652] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jan 24 15:40:31 hugo-K46CA kernel: [    1.042923] Linux agpgart interface v0.103
Jan 24 15:40:31 hugo-K46CA kernel: [    1.044839] brd: module loaded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.045646] loop: module loaded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.045914] libphy: Fixed MDIO Bus: probed
Jan 24 15:40:31 hugo-K46CA kernel: [    1.045918] tun: Universal TUN/TAP device driver, 1.6
Jan 24 15:40:31 hugo-K46CA kernel: [    1.045920] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan 24 15:40:31 hugo-K46CA kernel: [    1.045974] PPP generic driver version 2.4.2
Jan 24 15:40:31 hugo-K46CA kernel: [    1.046218] xhci_hcd 0000:00:14.0: xHCI Host Controller
Jan 24 15:40:31 hugo-K46CA kernel: [    1.046226] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047356] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047480] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047483] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047485] usb usb1: Product: xHCI Host Controller
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047487] usb usb1: Manufacturer: Linux 3.19.0-47-generic xhci-hcd
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047489] usb usb1: SerialNumber: 0000:00:14.0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047626] hub 1-0:1.0: USB hub found
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047639] hub 1-0:1.0: 4 ports detected
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047790] xhci_hcd 0000:00:14.0: xHCI Host Controller
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047795] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047839] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047842] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047844] usb usb2: Product: xHCI Host Controller
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047846] usb usb2: Manufacturer: Linux 3.19.0-47-generic xhci-hcd
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047848] usb usb2: SerialNumber: 0000:00:14.0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.047990] hub 2-0:1.0: USB hub found
Jan 24 15:40:31 hugo-K46CA kernel: [    1.048005] hub 2-0:1.0: 4 ports detected
Jan 24 15:40:31 hugo-K46CA kernel: [    1.048166] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan 24 15:40:31 hugo-K46CA kernel: [    1.048173] ehci-pci: EHCI PCI platform driver
Jan 24 15:40:31 hugo-K46CA kernel: [    1.048312] ehci-pci 0000:00:1a.0: EHCI Host Controller
Jan 24 15:40:31 hugo-K46CA kernel: [    1.048318] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jan 24 15:40:31 hugo-K46CA kernel: [    1.048335] ehci-pci 0000:00:1a.0: debug port 2
Jan 24 15:40:31 hugo-K46CA kernel: [    1.052240] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
Jan 24 15:40:31 hugo-K46CA kernel: [    1.052257] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7e20000
Jan 24 15:40:31 hugo-K46CA kernel: [    1.053045] ACPI: Battery Slot [BAT0] (battery present)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.062092] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Jan 24 15:40:31 hugo-K46CA kernel: [    1.062140] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Jan 24 15:40:31 hugo-K46CA kernel: [    1.062142] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 24 15:40:31 hugo-K46CA kernel: [    1.062144] usb usb3: Product: EHCI Host Controller
Jan 24 15:40:31 hugo-K46CA kernel: [    1.062147] usb usb3: Manufacturer: Linux 3.19.0-47-generic ehci_hcd
Jan 24 15:40:31 hugo-K46CA kernel: [    1.062149] usb usb3: SerialNumber: 0000:00:1a.0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.062326] hub 3-0:1.0: USB hub found
Jan 24 15:40:31 hugo-K46CA kernel: [    1.062335] hub 3-0:1.0: 2 ports detected
Jan 24 15:40:31 hugo-K46CA kernel: [    1.062579] ehci-pci 0000:00:1d.0: EHCI Host Controller
Jan 24 15:40:31 hugo-K46CA kernel: [    1.062586] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
Jan 24 15:40:31 hugo-K46CA kernel: [    1.062601] ehci-pci 0000:00:1d.0: debug port 2
Jan 24 15:40:31 hugo-K46CA kernel: [    1.066497] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
Jan 24 15:40:31 hugo-K46CA kernel: [    1.066515] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7e1f000
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078141] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078208] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078212] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078214] usb usb4: Product: EHCI Host Controller
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078216] usb usb4: Manufacturer: Linux 3.19.0-47-generic ehci_hcd
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078218] usb usb4: SerialNumber: 0000:00:1d.0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078404] hub 4-0:1.0: USB hub found
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078414] hub 4-0:1.0: 2 ports detected
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078538] ehci-platform: EHCI generic platform driver
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078552] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078558] ohci-pci: OHCI PCI platform driver
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078572] ohci-platform: OHCI generic platform driver
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078584] uhci_hcd: USB Universal Host Controller Interface driver
Jan 24 15:40:31 hugo-K46CA kernel: [    1.078663] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Jan 24 15:40:31 hugo-K46CA kernel: [    1.080539] i8042: Detected active multiplexing controller, rev 1.1
Jan 24 15:40:31 hugo-K46CA kernel: [    1.081937] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 24 15:40:31 hugo-K46CA kernel: [    1.081943] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan 24 15:40:31 hugo-K46CA kernel: [    1.081975] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan 24 15:40:31 hugo-K46CA kernel: [    1.082003] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan 24 15:40:31 hugo-K46CA kernel: [    1.082029] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan 24 15:40:31 hugo-K46CA kernel: [    1.082296] mousedev: PS/2 mouse device common for all mice
Jan 24 15:40:31 hugo-K46CA kernel: [    1.082695] rtc_cmos 00:02: RTC can wake from S4
Jan 24 15:40:31 hugo-K46CA kernel: [    1.082839] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.082874] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Jan 24 15:40:31 hugo-K46CA kernel: [    1.082888] i2c /dev entries driver
Jan 24 15:40:31 hugo-K46CA kernel: [    1.082973] device-mapper: uevent: version 1.0.3
Jan 24 15:40:31 hugo-K46CA kernel: [    1.083054] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
Jan 24 15:40:31 hugo-K46CA kernel: [    1.083078] Intel P-state driver initializing.
Jan 24 15:40:31 hugo-K46CA kernel: [    1.083207] Consider also installing thermald for improved thermal control.
Jan 24 15:40:31 hugo-K46CA kernel: [    1.083213] ledtrig-cpu: registered to indicate activity on CPUs
Jan 24 15:40:31 hugo-K46CA kernel: [    1.083220] EFI Variables Facility v0.08 2004-May-17
Jan 24 15:40:31 hugo-K46CA kernel: [    1.086342] PCCT header not found.
Jan 24 15:40:31 hugo-K46CA kernel: [    1.086343] ACPI PCC probe failed.
Jan 24 15:40:31 hugo-K46CA kernel: [    1.086444] TCP: cubic registered
Jan 24 15:40:31 hugo-K46CA kernel: [    1.086528] NET: Registered protocol family 10
Jan 24 15:40:31 hugo-K46CA kernel: [    1.086789] NET: Registered protocol family 17
Jan 24 15:40:31 hugo-K46CA kernel: [    1.086800] Key type dns_resolver registered
Jan 24 15:40:31 hugo-K46CA kernel: [    1.087193] Loading compiled-in X.509 certificates
Jan 24 15:40:31 hugo-K46CA kernel: [    1.088022] Loaded X.509 cert 'Magrathea: Glacier signing key: 8335c30cf45ac8874b83816192bf33dddcb532b6'
Jan 24 15:40:31 hugo-K46CA kernel: [    1.088036] registered taskstats version 1
Jan 24 15:40:31 hugo-K46CA kernel: [    1.089797] Key type trusted registered
Jan 24 15:40:31 hugo-K46CA kernel: [    1.092844] Key type encrypted registered
Jan 24 15:40:31 hugo-K46CA kernel: [    1.092852] AppArmor: AppArmor sha1 policy hashing enabled
Jan 24 15:40:31 hugo-K46CA kernel: [    1.092856] ima: No TPM chip found, activating TPM-bypass!
Jan 24 15:40:31 hugo-K46CA kernel: [    1.092876] evm: HMAC attrs: 0x1
Jan 24 15:40:31 hugo-K46CA kernel: [    1.093215]   Magic number: 0:708:694
Jan 24 15:40:31 hugo-K46CA kernel: [    1.093322] rtc_cmos 00:02: setting system clock to 2016-01-24 17:40:09 UTC (1453657209)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.093401] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 24 15:40:31 hugo-K46CA kernel: [    1.093404] EDD information not available.
Jan 24 15:40:31 hugo-K46CA kernel: [    1.093567] PM: Hibernation image not present or could not be loaded.
Jan 24 15:40:31 hugo-K46CA kernel: [    1.093849] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.093851] Write protecting the kernel read-only data: 12288k
Jan 24 15:40:31 hugo-K46CA kernel: [    1.094050] Freeing unused kernel memory: 256K (ffff8800017c0000 - ffff880001800000)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.094151] Freeing unused kernel memory: 340K (ffff880001bab000 - ffff880001c00000)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.109838] systemd-udevd[137]: starting version 204
Jan 24 15:40:31 hugo-K46CA kernel: [    1.120149] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jan 24 15:40:31 hugo-K46CA kernel: [    1.131012] wmi: Mapper loaded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.134017] rtsx_pci 0000:03:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 27
Jan 24 15:40:31 hugo-K46CA kernel: [    1.136055] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.136066] r8169 0000:03:00.2: can't disable ASPM; OS doesn't have ASPM control
Jan 24 15:40:31 hugo-K46CA kernel: [    1.136390] ahci 0000:00:1f.2: version 3.0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.136920] r8169 0000:03:00.2 eth0: RTL8411 at 0xffffc90004c90000, 60:a4:4c:c5:9e:38, XID 08800800 IRQ 28
Jan 24 15:40:31 hugo-K46CA kernel: [    1.136924] r8169 0000:03:00.2 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jan 24 15:40:31 hugo-K46CA kernel: [    1.137539] [drm] Initialized drm 1.1.0 20060810
Jan 24 15:40:31 hugo-K46CA kernel: [    1.150158] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x7 impl SATA mode
Jan 24 15:40:31 hugo-K46CA kernel: [    1.150163] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
Jan 24 15:40:31 hugo-K46CA kernel: [    1.167138] scsi host0: ahci
Jan 24 15:40:31 hugo-K46CA kernel: [    1.167329] scsi host1: ahci
Jan 24 15:40:31 hugo-K46CA kernel: [    1.167459] scsi host2: ahci
Jan 24 15:40:31 hugo-K46CA kernel: [    1.167601] scsi host3: ahci
Jan 24 15:40:31 hugo-K46CA kernel: [    1.167729] scsi host4: ahci
Jan 24 15:40:31 hugo-K46CA kernel: [    1.167917] scsi host5: ahci
Jan 24 15:40:31 hugo-K46CA kernel: [    1.167993] ata1: SATA max UDMA/133 abar m2048@0xf7e1e000 port 0xf7e1e100 irq 29
Jan 24 15:40:31 hugo-K46CA kernel: [    1.167998] ata2: SATA max UDMA/133 abar m2048@0xf7e1e000 port 0xf7e1e180 irq 29
Jan 24 15:40:31 hugo-K46CA kernel: [    1.168002] ata3: SATA max UDMA/133 abar m2048@0xf7e1e000 port 0xf7e1e200 irq 29
Jan 24 15:40:31 hugo-K46CA kernel: [    1.168004] ata4: DUMMY
Jan 24 15:40:31 hugo-K46CA kernel: [    1.168006] ata5: DUMMY
Jan 24 15:40:31 hugo-K46CA kernel: [    1.168008] ata6: DUMMY
Jan 24 15:40:31 hugo-K46CA kernel: [    1.168820] [drm] Memory usable by graphics device = 2048M
Jan 24 15:40:31 hugo-K46CA kernel: [    1.168825] checking generic (e0000000 300000) vs hw (e0000000 10000000)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.168827] fb: switching to inteldrmfb from EFI VGA
Jan 24 15:40:31 hugo-K46CA kernel: [    1.168853] Console: switching to colour dummy device 80x25
Jan 24 15:40:31 hugo-K46CA kernel: [    1.168933] [drm] Replacing VGA console driver
Jan 24 15:40:31 hugo-K46CA kernel: [    1.190201] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Jan 24 15:40:31 hugo-K46CA kernel: [    1.190203] [drm] Driver supports precise vblank timestamp query.
Jan 24 15:40:31 hugo-K46CA kernel: [    1.190275] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jan 24 15:40:31 hugo-K46CA kernel: [    1.215147] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.217813] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input11
Jan 24 15:40:31 hugo-K46CA kernel: [    1.217893] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.231984] fbcon: inteldrmfb (fb0) is primary device
Jan 24 15:40:31 hugo-K46CA kernel: [    1.232005] Console: switching to colour frame buffer device 170x48
Jan 24 15:40:31 hugo-K46CA kernel: [    1.232025] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Jan 24 15:40:31 hugo-K46CA kernel: [    1.232026] i915 0000:00:02.0: registered panic notifier
Jan 24 15:40:31 hugo-K46CA kernel: [    1.358281] usb 1-1: new high-speed USB device number 2 using xhci_hcd
Jan 24 15:40:31 hugo-K46CA kernel: [    1.374270] usb 3-1: new high-speed USB device number 2 using ehci-pci
Jan 24 15:40:31 hugo-K46CA kernel: [    1.390304] usb 4-1: new high-speed USB device number 2 using ehci-pci
Jan 24 15:40:31 hugo-K46CA kernel: [    1.486353] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.486381] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.486402] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.486841] usb 1-1: New USB device found, idVendor=0bda, idProduct=8179
Jan 24 15:40:31 hugo-K46CA kernel: [    1.486844] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan 24 15:40:31 hugo-K46CA kernel: [    1.486846] usb 1-1: Product: 802.11n NIC
Jan 24 15:40:31 hugo-K46CA kernel: [    1.486847] usb 1-1: Manufacturer: Realtek
Jan 24 15:40:31 hugo-K46CA kernel: [    1.486848] usb 1-1: SerialNumber: 00E04C0001
Jan 24 15:40:31 hugo-K46CA kernel: [    1.487909] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Jan 24 15:40:31 hugo-K46CA kernel: [    1.487933] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.487935] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jan 24 15:40:31 hugo-K46CA kernel: [    1.488202] ata2.00: ATA-8: SG9MSM6D024GPM00, S8FM05.3, max UDMA/133
Jan 24 15:40:31 hugo-K46CA kernel: [    1.488204] ata2.00: 43975008 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 24 15:40:31 hugo-K46CA kernel: [    1.488347] ata3.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.488349] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jan 24 15:40:31 hugo-K46CA kernel: [    1.488709] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Jan 24 15:40:31 hugo-K46CA kernel: [    1.488740] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.488742] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jan 24 15:40:31 hugo-K46CA kernel: [    1.489114] ata2.00: configured for UDMA/133
Jan 24 15:40:31 hugo-K46CA kernel: [    1.489409] ata3.00: ATAPI: MATSHITADVD-RAM UJ8C2 S, 1.00, max UDMA/133
Jan 24 15:40:31 hugo-K46CA kernel: [    1.492194] ata3.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.492216] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jan 24 15:40:31 hugo-K46CA kernel: [    1.492613] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Jan 24 15:40:31 hugo-K46CA kernel: [    1.492725] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.492748] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jan 24 15:40:31 hugo-K46CA kernel: [    1.493327] ata3.00: configured for UDMA/133
Jan 24 15:40:31 hugo-K46CA kernel: [    1.498978] ata1.00: ATA-8: ST500LM012 HN-M500MBB, 2AR10001, max UDMA/133
Jan 24 15:40:31 hugo-K46CA kernel: [    1.499001] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 24 15:40:31 hugo-K46CA kernel: [    1.505285] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Jan 24 15:40:31 hugo-K46CA kernel: [    1.505398] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
Jan 24 15:40:31 hugo-K46CA kernel: [    1.505421] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jan 24 15:40:31 hugo-K46CA kernel: [    1.507147] usb 3-1: New USB device found, idVendor=8087, idProduct=0024
Jan 24 15:40:31 hugo-K46CA kernel: [    1.507150] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.507455] hub 3-1:1.0: USB hub found
Jan 24 15:40:31 hugo-K46CA kernel: [    1.507514] hub 3-1:1.0: 6 ports detected
Jan 24 15:40:31 hugo-K46CA kernel: [    1.511546] ata1.00: configured for UDMA/133
Jan 24 15:40:31 hugo-K46CA kernel: [    1.511703] scsi 0:0:0:0: Direct-Access     ATA      ST500LM012 HN-M5 0001 PQ: 0 ANSI: 5
Jan 24 15:40:31 hugo-K46CA kernel: [    1.511939] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.511943] sd 0:0:0:0: [sda] 4096-byte physical blocks
Jan 24 15:40:31 hugo-K46CA kernel: [    1.511989] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.512033] sd 0:0:0:0: [sda] Write Protect is off
Jan 24 15:40:31 hugo-K46CA kernel: [    1.512038] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 24 15:40:31 hugo-K46CA kernel: [    1.512077] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 24 15:40:31 hugo-K46CA kernel: [    1.512120] scsi 1:0:0:0: Direct-Access     ATA      SG9MSM6D024GPM00 05.3 PQ: 0 ANSI: 5
Jan 24 15:40:31 hugo-K46CA kernel: [    1.512356] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.512365] sd 1:0:0:0: [sdb] 43975008 512-byte logical blocks: (22.5 GB/20.9 GiB)
Jan 24 15:40:31 hugo-K46CA kernel: [    1.512466] sd 1:0:0:0: [sdb] Write Protect is off
Jan 24 15:40:31 hugo-K46CA kernel: [    1.512469] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jan 24 15:40:31 hugo-K46CA kernel: [    1.512501] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 24 15:40:31 hugo-K46CA kernel: [    1.513691] scsi 2:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8C2 S  1.00 PQ: 0 ANSI: 5
Jan 24 15:40:31 hugo-K46CA kernel: [    1.514166]  sdb: sdb1 sdb2
Jan 24 15:40:31 hugo-K46CA kernel: [    1.514536] sd 1:0:0:0: [sdb] Attached SCSI disk
Jan 24 15:40:31 hugo-K46CA kernel: [    1.522716] usb 4-1: New USB device found, idVendor=8087, idProduct=0024
Jan 24 15:40:31 hugo-K46CA kernel: [    1.522718] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.522966] hub 4-1:1.0: USB hub found
Jan 24 15:40:31 hugo-K46CA kernel: [    1.523018] hub 4-1:1.0: 6 ports detected
Jan 24 15:40:31 hugo-K46CA kernel: [    1.528847] sr 2:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 24 15:40:31 hugo-K46CA kernel: [    1.528853] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan 24 15:40:31 hugo-K46CA kernel: [    1.528998] sr 2:0:0:0: Attached scsi CD-ROM sr0
Jan 24 15:40:31 hugo-K46CA kernel: [    1.529082] sr 2:0:0:0: Attached scsi generic sg2 type 5
Jan 24 15:40:31 hugo-K46CA kernel: [    1.569666]  sda: sda1 sda2 sda3 sda4
Jan 24 15:40:31 hugo-K46CA kernel: [    1.570007] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 24 15:40:31 hugo-K46CA kernel: [    1.778476] usb 3-1.1: new full-speed USB device number 3 using ehci-pci
Jan 24 15:40:31 hugo-K46CA kernel: [    1.872622] usb 3-1.1: New USB device found, idVendor=13d3, idProduct=3362
Jan 24 15:40:31 hugo-K46CA kernel: [    1.872639] usb 3-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan 24 15:40:31 hugo-K46CA kernel: [    1.872641] usb 3-1.1: Product: Bluetooth USB Host Controller
Jan 24 15:40:31 hugo-K46CA kernel: [    1.872642] usb 3-1.1: Manufacturer: Atheros Communications
Jan 24 15:40:31 hugo-K46CA kernel: [    1.872644] usb 3-1.1: SerialNumber: Alaska Day 2006
Jan 24 15:40:31 hugo-K46CA kernel: [    1.942552] usb 3-1.3: new high-speed USB device number 4 using ehci-pci
Jan 24 15:40:31 hugo-K46CA kernel: [    2.010547] tsc: Refined TSC clocksource calibration: 1696.146 MHz
Jan 24 15:40:31 hugo-K46CA kernel: [    2.121652] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f01)
Jan 24 15:40:31 hugo-K46CA kernel: [    2.135273] psmouse serio4: elantech: Synaptics capabilities query result 0x00, 0x15, 0x0c.
Jan 24 15:40:31 hugo-K46CA kernel: [    2.137111] usb 3-1.3: New USB device found, idVendor=13d3, idProduct=5165
Jan 24 15:40:31 hugo-K46CA kernel: [    2.137133] usb 3-1.3: New USB device strings: Mfr=3, Product=1, SerialNumber=2
Jan 24 15:40:31 hugo-K46CA kernel: [    2.137134] usb 3-1.3: Product: USB Camera
Jan 24 15:40:31 hugo-K46CA kernel: [    2.137136] usb 3-1.3: Manufacturer: Azurewave
Jan 24 15:40:31 hugo-K46CA kernel: [    2.137137] usb 3-1.3: SerialNumber: NULL
Jan 24 15:40:31 hugo-K46CA kernel: [    2.203483] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input12
Jan 24 15:40:31 hugo-K46CA kernel: [    2.542066] [drm:intel_set_pch_fifo_underrun_reporting [i915]] *ERROR* uncleared pch fifo underrun on pch transcoder A
Jan 24 15:40:31 hugo-K46CA kernel: [    2.542081] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
Jan 24 15:40:31 hugo-K46CA kernel: [    3.011205] Switched to clocksource tsc
Jan 24 15:40:31 hugo-K46CA kernel: [    8.078675] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
Jan 24 15:40:31 hugo-K46CA kernel: [    8.267795] random: nonblocking pool is initialized
Jan 24 15:40:31 hugo-K46CA kernel: [   10.482675] Adding 1052668k swap on /dev/sda2.  Priority:-1 extents:1 across:1052668k FS
Jan 24 15:40:31 hugo-K46CA kernel: [   11.631738] systemd-udevd[414]: starting version 204
Jan 24 15:40:31 hugo-K46CA kernel: [   12.747919] lp: driver loaded but no devices found
Jan 24 15:40:31 hugo-K46CA kernel: [   12.823880] ppdev: user-space parallel port driver
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952772] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000044f (\GPIS) (20141107/utaddress-258)
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952781] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20141107/utaddress-258)
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952787] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952791] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPIO) (20141107/utaddress-258)
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952796] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GP01) (20141107/utaddress-258)
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952800] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952802] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPIO) (20141107/utaddress-258)
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952806] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GP01) (20141107/utaddress-258)
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952811] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952812] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000057f (\GPIO) (20141107/utaddress-258)
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952816] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GP01) (20141107/utaddress-258)
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952821] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan 24 15:40:31 hugo-K46CA kernel: [   14.952823] lpc_ich: Resource conflict(s) found affecting gpio_ich
Jan 24 15:40:31 hugo-K46CA kernel: [   15.040474] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 24 15:40:31 hugo-K46CA kernel: [   15.945233] cfg80211: Calling CRDA to update world regulatory domain
Jan 24 15:40:31 hugo-K46CA kernel: [   16.199222] device-mapper: multipath: version 1.7.0 loaded
Jan 24 15:40:31 hugo-K46CA kernel: [   16.257970] Bluetooth: Core ver 2.20
Jan 24 15:40:31 hugo-K46CA kernel: [   16.257991] NET: Registered protocol family 31
Jan 24 15:40:31 hugo-K46CA kernel: [   16.257993] Bluetooth: HCI device and connection manager initialized
Jan 24 15:40:31 hugo-K46CA kernel: [   16.257998] Bluetooth: HCI socket layer initialized
Jan 24 15:40:31 hugo-K46CA kernel: [   16.258001] Bluetooth: L2CAP socket layer initialized
Jan 24 15:40:31 hugo-K46CA kernel: [   16.258007] Bluetooth: SCO socket layer initialized
Jan 24 15:40:31 hugo-K46CA kernel: [   16.470250] media: Linux media interface: v0.10
Jan 24 15:40:31 hugo-K46CA kernel: [   16.527911] usbcore: registered new interface driver btusb
Jan 24 15:40:31 hugo-K46CA kernel: [   16.544467] Linux video capture interface: v2.00
Jan 24 15:40:31 hugo-K46CA kernel: [   16.670560] AVX version of gcm_enc/dec engaged.
Jan 24 15:40:31 hugo-K46CA kernel: [   16.670564] AES CTR mode by8 optimization enabled
Jan 24 15:40:31 hugo-K46CA kernel: [   16.694311] ath: phy0: Disable PLL PowerSave
Jan 24 15:40:31 hugo-K46CA kernel: [   16.701967] ath: phy0: ASPM enabled: 0x42
Jan 24 15:40:31 hugo-K46CA kernel: [   16.701969] ath: EEPROM regdomain: 0x60
Jan 24 15:40:31 hugo-K46CA kernel: [   16.701969] ath: EEPROM indicates we should expect a direct regpair map
Jan 24 15:40:31 hugo-K46CA kernel: [   16.701971] ath: Country alpha2 being used: 00
Jan 24 15:40:31 hugo-K46CA kernel: [   16.701972] ath: Regpair used: 0x60
Jan 24 15:40:31 hugo-K46CA kernel: [   16.712898] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jan 24 15:40:31 hugo-K46CA kernel: [   16.713262] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90005080000, irq=17
Jan 24 15:40:31 hugo-K46CA kernel: [   17.016975] ath9k 0000:02:00.0 wlan1: renamed from wlan0
Jan 24 15:40:31 hugo-K46CA kernel: [   17.031195] uvcvideo: Found UVC 1.00 device USB Camera (13d3:5165)
Jan 24 15:40:31 hugo-K46CA kernel: [   17.033551] systemd-udevd[458]: renamed network interface wlan0 to wlan1
Jan 24 15:40:31 hugo-K46CA kernel: [   17.042335] input: USB Camera as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/input/input13
Jan 24 15:40:31 hugo-K46CA kernel: [   17.042431] usbcore: registered new interface driver uvcvideo
Jan 24 15:40:31 hugo-K46CA kernel: [   17.042434] USB Video Class driver (1.1.1)
Jan 24 15:40:31 hugo-K46CA kernel: [   17.057306] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
Jan 24 15:40:31 hugo-K46CA kernel: [   17.057312] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Jan 24 15:40:31 hugo-K46CA kernel: [   17.057314] sound hdaudioC0D0:    hp_outs=1 (0x1a/0x0/0x0/0x0/0x0)
Jan 24 15:40:31 hugo-K46CA kernel: [   17.057317] sound hdaudioC0D0:    mono: mono_out=0x0
Jan 24 15:40:31 hugo-K46CA kernel: [   17.057319] sound hdaudioC0D0:    inputs:
Jan 24 15:40:31 hugo-K46CA kernel: [   17.057322] sound hdaudioC0D0:      Mic=0x19
Jan 24 15:40:31 hugo-K46CA kernel: [   17.142012] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
Jan 24 15:40:31 hugo-K46CA kernel: [   17.206692] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
Jan 24 15:40:31 hugo-K46CA kernel: [   17.207822] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
Jan 24 15:40:31 hugo-K46CA kernel: [   17.230449] usbcore: registered new interface driver r8188eu
Jan 24 15:40:31 hugo-K46CA kernel: [   17.232958] input: HDA Intel PCH Headphone Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
Jan 24 15:40:31 hugo-K46CA kernel: [   17.233025] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
Jan 24 15:40:31 hugo-K46CA kernel: [   17.689758] asus_wmi: ASUS WMI generic driver loaded
Jan 24 15:40:31 hugo-K46CA kernel: [   17.697595] asus_wmi: Initialization: 0x1
Jan 24 15:40:31 hugo-K46CA kernel: [   17.697625] asus_wmi: BIOS WMI version: 7.9
Jan 24 15:40:31 hugo-K46CA kernel: [   17.697657] asus_wmi: SFUN value: 0x4a0877
Jan 24 15:40:31 hugo-K46CA kernel: [   17.698783] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input16
Jan 24 15:40:31 hugo-K46CA kernel: [   17.766505] audit: type=1400 audit(1453657226.161:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=498 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   17.766512] audit: type=1400 audit(1453657226.161:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=498 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   17.766516] audit: type=1400 audit(1453657226.161:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=498 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   17.766663] audit: type=1400 audit(1453657226.161:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=631 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   17.766673] audit: type=1400 audit(1453657226.161:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=631 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   17.766679] audit: type=1400 audit(1453657226.161:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=631 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   17.766688] audit: type=1400 audit(1453657226.161:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=543 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   17.766694] audit: type=1400 audit(1453657226.161:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=543 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   17.766700] audit: type=1400 audit(1453657226.161:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=543 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   17.766902] audit: type=1400 audit(1453657226.161:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=498 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   17.796360] asus_wmi: Backlight controlled by ACPI video driver
Jan 24 15:40:31 hugo-K46CA kernel: [   17.862602] usbcore: registered new interface driver ath3k
Jan 24 15:40:31 hugo-K46CA kernel: [   17.957230] usb 3-1.1: USB disconnect, device number 3
Jan 24 15:40:31 hugo-K46CA kernel: [   18.305801] intel_rapl: Found RAPL domain package
Jan 24 15:40:31 hugo-K46CA kernel: [   18.305809] intel_rapl: Found RAPL domain core
Jan 24 15:40:31 hugo-K46CA kernel: [   18.305813] intel_rapl: Found RAPL domain uncore
Jan 24 15:40:31 hugo-K46CA kernel: [   18.772067] cfg80211: World regulatory domain updated:
Jan 24 15:40:31 hugo-K46CA kernel: [   18.772071] cfg80211:  DFS Master region: unset
Jan 24 15:40:31 hugo-K46CA kernel: [   18.772073] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 24 15:40:31 hugo-K46CA kernel: [   18.772075] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:31 hugo-K46CA kernel: [   18.772077] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:31 hugo-K46CA kernel: [   18.772078] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:31 hugo-K46CA kernel: [   18.772079] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:31 hugo-K46CA kernel: [   18.772081] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:31 hugo-K46CA kernel: [   21.530337] init: Failed to spawn smbd main process: unable to execute: No such file or directory
Jan 24 15:40:31 hugo-K46CA kernel: [   21.531496] init: Failed to spawn samba-ad-dc main process: unable to execute: No such file or directory
Jan 24 15:40:31 hugo-K46CA kernel: [   21.711119] init: failsafe main process (832) killed by TERM signal
Jan 24 15:40:31 hugo-K46CA kernel: [   22.852399] audit_printk_skb: 42 callbacks suppressed
Jan 24 15:40:31 hugo-K46CA kernel: [   22.852401] audit: type=1400 audit(1453657231.245:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=995 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   22.852408] audit: type=1400 audit(1453657231.245:27): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=995 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   22.852412] audit: type=1400 audit(1453657231.245:28): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=995 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   22.852771] audit: type=1400 audit(1453657231.245:29): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=995 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   22.852775] audit: type=1400 audit(1453657231.245:30): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=995 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   22.852963] audit: type=1400 audit(1453657231.245:31): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=995 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Jan 24 15:40:31 hugo-K46CA kernel: [   22.967411] audit: type=1400 audit(1453657231.357:32): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/libvirt/virt-aa-helper" pid=998 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA ntpdate[993]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jan 24 15:40:31 hugo-K46CA ntpdate[993]: no servers can be used, exiting
Jan 24 15:40:31 hugo-K46CA kernel: [   23.097919] audit: type=1400 audit(1453657231.493:33): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1000 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   23.103803] audit: type=1400 audit(1453657231.493:34): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=994 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA kernel: [   23.103812] audit: type=1400 audit(1453657231.493:35): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=994 comm="apparmor_parser"
Jan 24 15:40:31 hugo-K46CA dbus[1028]: [system] AppArmor D-Bus mediation is enabled
Jan 24 15:40:32 hugo-K46CA bluetoothd[1071]: Bluetooth daemon 4.101
Jan 24 15:40:32 hugo-K46CA bluetoothd[1071]: Starting SDP server
Jan 24 15:40:32 hugo-K46CA bluetoothd[1071]: DIS cannot start: GATT is disabled
Jan 24 15:40:32 hugo-K46CA bluetoothd[1071]: Failed to init deviceinfo plugin
Jan 24 15:40:32 hugo-K46CA bluetoothd[1071]: Failed to init proximity plugin
Jan 24 15:40:32 hugo-K46CA bluetoothd[1071]: Failed to init time plugin
Jan 24 15:40:32 hugo-K46CA bluetoothd[1071]: Failed to init alert plugin
Jan 24 15:40:32 hugo-K46CA bluetoothd[1071]: Failed to init thermometer plugin
Jan 24 15:40:32 hugo-K46CA kernel: [   24.222491] Bluetooth: RFCOMM TTY layer initialized
Jan 24 15:40:32 hugo-K46CA kernel: [   24.222498] Bluetooth: RFCOMM socket layer initialized
Jan 24 15:40:32 hugo-K46CA kernel: [   24.222504] Bluetooth: RFCOMM ver 1.11
Jan 24 15:40:32 hugo-K46CA kernel: [   24.431918] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan 24 15:40:32 hugo-K46CA kernel: [   24.431922] Bluetooth: BNEP filters: protocol multicast
Jan 24 15:40:32 hugo-K46CA kernel: [   24.431927] Bluetooth: BNEP socket layer initialized
Jan 24 15:40:32 hugo-K46CA bluetoothd[1071]: Failed to init gatt_example plugin
Jan 24 15:40:32 hugo-K46CA bluetoothd[1071]: Bluetooth Management interface initialized
Jan 24 15:40:33 hugo-K46CA ModemManager[1042]: <info>  ModemManager (version 1.0.0) starting...
Jan 24 15:40:33 hugo-K46CA anacron[1158]: Anacron 2.3 started on 2016-01-24
Jan 24 15:40:33 hugo-K46CA cron[1102]: (CRON) INFO (pidfile fd = 3)
Jan 24 15:40:34 hugo-K46CA acpid: starting up with netlink and the input layer
Jan 24 15:40:34 hugo-K46CA cron[1204]: (CRON) STARTUP (fork ok)
Jan 24 15:40:34 hugo-K46CA cron[1204]: (CRON) INFO (Running @reboot jobs)
Jan 24 15:40:34 hugo-K46CA acpid: 9 rules loaded
Jan 24 15:40:34 hugo-K46CA acpid: waiting for events: event logging is off
Jan 24 15:40:34 hugo-K46CA anacron[1158]: Normal exit (0 jobs run)
Jan 24 15:40:34 hugo-K46CA avahi-daemon[1249]: Found user 'avahi' (UID 111) and group 'avahi' (GID 117).
Jan 24 15:40:34 hugo-K46CA avahi-daemon[1249]: Successfully dropped root privileges.
Jan 24 15:40:34 hugo-K46CA avahi-daemon[1249]: avahi-daemon 0.6.31 starting up.
Jan 24 15:40:34 hugo-K46CA kernel: [   26.541680] init: cups main process (1136) killed by HUP signal
Jan 24 15:40:34 hugo-K46CA kernel: [   26.541691] init: cups main process ended, respawning
Jan 24 15:40:35 hugo-K46CA avahi-daemon[1249]: Successfully called chroot().
Jan 24 15:40:35 hugo-K46CA avahi-daemon[1249]: Successfully dropped remaining capabilities.
Jan 24 15:40:35 hugo-K46CA avahi-daemon[1249]: No service file found in /etc/avahi/services.
Jan 24 15:40:35 hugo-K46CA avahi-daemon[1249]: Network interface enumeration completed.
Jan 24 15:40:35 hugo-K46CA avahi-daemon[1249]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jan 24 15:40:35 hugo-K46CA avahi-daemon[1249]: Server startup complete. Host name is hugo-K46CA.local. Local service cookie is 2534835034.
Jan 24 15:40:36 hugo-K46CA NetworkManager[1294]: <info> NetworkManager (version 0.9.8.8) is starting...
Jan 24 15:40:36 hugo-K46CA NetworkManager[1294]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jan 24 15:40:36 hugo-K46CA NetworkManager[1294]: <info> WEXT support is enabled
Jan 24 15:40:37 hugo-K46CA whoopsie[1151]: whoopsie 0.2.24.6ubuntu2 starting up.
Jan 24 15:40:37 hugo-K46CA whoopsie[1151]: Using lock path: /var/lock/whoopsie/lock
Jan 24 15:40:37 hugo-K46CA whoopsie[1312]: Could not get the Network Manager state:
Jan 24 15:40:37 hugo-K46CA whoopsie[1312]: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
Jan 24 15:40:37 hugo-K46CA NetworkManager[1294]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jan 24 15:40:37 hugo-K46CA NetworkManager[1294]: <info> DNS: loaded plugin dnsmasq
Jan 24 15:40:37 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jan 24 15:40:38 hugo-K46CA polkitd[1320]: started daemon version 0.105 using authority implementation `local' version `0.105'
Jan 24 15:40:38 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: init!
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: update_system_hostname
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:       interface-parser: parsing file /etc/network/interfaces
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:       interface-parser: finished parsing file /etc/network/interfaces
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPluginIfupdown: management mode: unmanaged
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0)
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan1, iface: wlan1)
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/eth0, iface: eth0)
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: end _init.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ofono: init!
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ofono: end _init.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> Loaded plugin (null): (null)
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    Ifupdown: get unmanaged devices count: 0
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: (9493232) ... get_connections.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: (9493232) ... get_connections (managed=false): return empty list.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    keyfile: parsing LGroup_Auditorio ... 
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    keyfile:     read connection 'LGroup_Auditorio'
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    keyfile: parsing Outra Dimensao ... 
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    keyfile:     read connection 'Outra Dimensao'
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    keyfile: parsing Outra Dimensao 1 ... 
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    keyfile:     read connection 'Outra Dimensao 1'
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    keyfile: parsing LGroup_Auditorio 1 ... 
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    keyfile:     read connection 'LGroup_Auditorio 1'
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    keyfile: parsing AAA ... 
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    keyfile:     read connection 'AAA'
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ofono: (-1811922736) ... get_connections.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ofono: (-1811922736) connections count: 0
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]:    Ifupdown: get unmanaged devices count: 0
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill0) (driver ath9k)
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> rfkill1: found WiFi radio killswitch (at /sys/devices/platform/asus-nb-wmi/rfkill/rfkill1) (platform driver asus-nb-wmi)
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> Networking is enabled by state file
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> (wlan0): driver supports SSID scans (scan_capa 0x3F).
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> (wlan0): using WEXT for WiFi device control
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> (wlan0): new 802.11 WiFi device (driver: 'r8188eu' ifindex: 4)
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 24 15:40:38 hugo-K46CA NetworkManager[1294]: <info> (wlan0): bringing up device.
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan0): preparing device.
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan0): taking down device.
Jan 24 15:40:39 hugo-K46CA kernel: [   31.016203] MAC Address = c4:e9:84:14:25:9a
Jan 24 15:40:39 hugo-K46CA kernel: [   31.017461] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 24 15:40:39 hugo-K46CA kernel: [   31.019781] R8188EU: ERROR indicate disassoc
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan0): bringing up device.
Jan 24 15:40:39 hugo-K46CA dbus[1028]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan1): using nl80211 for WiFi device control
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan1): driver supports Access Point (AP) mode
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan1): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan1): bringing up device.
Jan 24 15:40:39 hugo-K46CA kernel: [   31.020234] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan1): preparing device.
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (wlan1): deactivating device (reason 'managed') [2]
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <warn> failed to allocate link cache: (-12) Object not found
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (eth0): carrier is OFF
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/2
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (eth0): bringing up device.
Jan 24 15:40:39 hugo-K46CA kernel: [   31.036588] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
Jan 24 15:40:39 hugo-K46CA ModemManager[1042]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1': not supported by any plugin
Jan 24 15:40:39 hugo-K46CA ModemManager[1042]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0': not supported by any plugin
Jan 24 15:40:39 hugo-K46CA ModemManager[1042]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2': not supported by any plugin
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (eth0): preparing device.
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> (eth0): deactivating device (reason 'managed') [2]
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> Added default wired connection 'Conexão cabeada 1' for /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/eth0
Jan 24 15:40:39 hugo-K46CA kernel: [   31.202951] r8169 0000:03:00.2 eth0: link down
Jan 24 15:40:39 hugo-K46CA kernel: [   31.202988] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> urfkill disappeared from the bus
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> ModemManager available in the bus
Jan 24 15:40:39 hugo-K46CA dbus[1028]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan 24 15:40:39 hugo-K46CA NetworkManager[1294]: <info> wpa_supplicant started
Jan 24 15:40:39 hugo-K46CA wpa_supplicant[1332]: Successfully initialized wpa_supplicant
Jan 24 15:40:39 hugo-K46CA wpa_supplicant[1334]: nl80211: Could not configure driver mode
Jan 24 15:40:40 hugo-K46CA NetworkManager[1294]: <info> (wlan0) supports 1 scan SSIDs
Jan 24 15:40:40 hugo-K46CA NetworkManager[1294]: <warn> Trying to remove a non-existant call id.
Jan 24 15:40:40 hugo-K46CA NetworkManager[1294]: <info> (wlan0): supplicant interface state: starting -> ready
Jan 24 15:40:40 hugo-K46CA NetworkManager[1294]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 24 15:40:40 hugo-K46CA wpa_supplicant[1334]: wlan0: Reject scan trigger since one is already pending
Jan 24 15:40:40 hugo-K46CA NetworkManager[1294]: <info> (wlan1) supports 4 scan SSIDs
Jan 24 15:40:40 hugo-K46CA NetworkManager[1294]: <warn> Trying to remove a non-existant call id.
Jan 24 15:40:40 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: starting -> ready
Jan 24 15:40:40 hugo-K46CA NetworkManager[1294]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 24 15:40:40 hugo-K46CA NetworkManager[1294]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jan 24 15:40:40 hugo-K46CA NetworkManager[1294]: <info> (wlan0) supports 1 scan SSIDs
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: ready -> disconnected
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> (wlan1) supports 4 scan SSIDs
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Auto-activating connection 'Outra Dimensao'.
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) starting connection 'Outra Dimensao'
Jan 24 15:40:41 hugo-K46CA kernel: [   32.845964] Ebtables v2.0 registered
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> NetworkManager state is now CONNECTING
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 24 15:40:41 hugo-K46CA whoopsie[1312]: offline
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 24 15:40:41 hugo-K46CA wpa_supplicant[1334]: wlan1: CTRL-EVENT-SCAN-STARTED 
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0/wireless): connection 'Outra Dimensao' has security, and secrets exist.  No new secrets needed.
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Config: added 'ssid' value 'Outra Dimensao'
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Config: added 'scan_ssid' value '1'
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Config: added 'auth_alg' value 'OPEN'
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Config: added 'psk' value '<omitted>'
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Config: set interface ap_scan to 1
Jan 24 15:40:41 hugo-K46CA wpa_supplicant[1334]: wlan0: Trying to associate with f0:82:61:52:98:b1 (SSID='Outra Dimensao' freq=2462 MHz)
Jan 24 15:40:41 hugo-K46CA wpa_supplicant[1334]: wlan0: Association request to the driver failed
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> (wlan0): supplicant interface state: inactive -> associating
Jan 24 15:40:41 hugo-K46CA kernel: [   32.921565] R8188EU: ERROR assoc success
Jan 24 15:40:41 hugo-K46CA wpa_supplicant[1334]: wlan0: Associated with f0:82:61:52:98:b1
Jan 24 15:40:41 hugo-K46CA kernel: [   32.921818] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> (wlan0): supplicant interface state: associating -> associated
Jan 24 15:40:41 hugo-K46CA kernel: [   32.937909] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 24 15:40:41 hugo-K46CA kernel: [   32.973593] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan 24 15:40:41 hugo-K46CA wpa_supplicant[1334]: wlan0: WPA: Key negotiation completed with f0:82:61:52:98:b1 [PTK=CCMP GTK=CCMP]
Jan 24 15:40:41 hugo-K46CA wpa_supplicant[1334]: wlan0: CTRL-EVENT-CONNECTED - Connection to f0:82:61:52:98:b1 completed [id=0 id_str=]
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Outra Dimensao'.
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> dhclient started with pid 1370
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jan 24 15:40:41 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 24 15:40:42 hugo-K46CA dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jan 24 15:40:42 hugo-K46CA dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jan 24 15:40:42 hugo-K46CA dhclient: All rights reserved.
Jan 24 15:40:42 hugo-K46CA dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan 24 15:40:42 hugo-K46CA dhclient: 
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Auto-activating connection 'Outra Dimensao 1'.
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) starting connection 'Outra Dimensao 1'
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 24 15:40:42 hugo-K46CA wpa_supplicant[1334]: wlan1: CTRL-EVENT-SCAN-STARTED 
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1/wireless): connection 'Outra Dimensao 1' has security, and secrets exist.  No new secrets needed.
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Config: added 'ssid' value 'Outra Dimensao'
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Config: added 'scan_ssid' value '1'
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Config: added 'auth_alg' value 'OPEN'
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Config: added 'psk' value '<omitted>'
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: disconnected -> inactive
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Config: set interface ap_scan to 1
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan 24 15:40:42 hugo-K46CA dhclient: Listening on LPF/wlan0/c4:e9:84:14:25:9a
Jan 24 15:40:42 hugo-K46CA dhclient: Sending on   LPF/wlan0/c4:e9:84:14:25:9a
Jan 24 15:40:42 hugo-K46CA dhclient: Sending on   Socket/fallback
Jan 24 15:40:42 hugo-K46CA dhclient: DHCPREQUEST of 192.168.1.10 on wlan0 to 255.255.255.255 port 67 (xid=0x4d8c77bb)
Jan 24 15:40:42 hugo-K46CA dhclient: DHCPACK of 192.168.1.10 from 192.168.1.1
Jan 24 15:40:42 hugo-K46CA dhclient: bound to 192.168.1.10 -- renewal in 36709 seconds.
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info>   address 192.168.1.10
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info>   prefix 24 (255.255.255.0)
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info>   gateway 192.168.1.1
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info>   nameserver '192.168.1.1'
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info>   domain name 'Home'
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jan 24 15:40:42 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jan 24 15:40:42 hugo-K46CA avahi-daemon[1249]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.10.
Jan 24 15:40:42 hugo-K46CA avahi-daemon[1249]: New relevant interface wlan0.IPv4 for mDNS.
Jan 24 15:40:42 hugo-K46CA avahi-daemon[1249]: Registering new address record for 192.168.1.10 on wlan0.IPv4.
Jan 24 15:40:42 hugo-K46CA avahi-daemon[1249]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::c6e9:84ff:fe14:259a.
Jan 24 15:40:42 hugo-K46CA avahi-daemon[1249]: New relevant interface wlan0.IPv6 for mDNS.
Jan 24 15:40:42 hugo-K46CA avahi-daemon[1249]: Registering new address record for fe80::c6e9:84ff:fe14:259a on wlan0.*.
Jan 24 15:40:43 hugo-K46CA wpa_supplicant[1334]: wlan1: SME: Trying to authenticate with f0:82:61:52:98:b1 (SSID='Outra Dimensao' freq=2462 MHz)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.762408] wlan1: authenticate with f0:82:61:52:98:b1
Jan 24 15:40:43 hugo-K46CA kernel: [   34.784082] wlan1: send auth to f0:82:61:52:98:b1 (try 1/3)
Jan 24 15:40:43 hugo-K46CA wpa_supplicant[1334]: wlan1: Trying to associate with f0:82:61:52:98:b1 (SSID='Outra Dimensao' freq=2462 MHz)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.786252] wlan1: authenticated
Jan 24 15:40:43 hugo-K46CA kernel: [   34.789730] wlan1: associate with f0:82:61:52:98:b1 (try 1/3)
Jan 24 15:40:43 hugo-K46CA wpa_supplicant[1334]: wlan1: Associated with f0:82:61:52:98:b1
Jan 24 15:40:43 hugo-K46CA kernel: [   34.796625] wlan1: RX AssocResp from f0:82:61:52:98:b1 (capab=0x411 status=0 aid=6)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.796738] wlan1: associated
Jan 24 15:40:43 hugo-K46CA kernel: [   34.796750] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Jan 24 15:40:43 hugo-K46CA wpa_supplicant[1334]: wlan1: WPA: Key negotiation completed with f0:82:61:52:98:b1 [PTK=CCMP GTK=CCMP]
Jan 24 15:40:43 hugo-K46CA wpa_supplicant[1334]: wlan1: CTRL-EVENT-CONNECTED - Connection to f0:82:61:52:98:b1 completed [id=0 id_str=]
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jan 24 15:40:43 hugo-K46CA wpa_supplicant[1334]: wlan1: SME: Trying to authenticate with f0:82:61:52:98:b1 (SSID='Outra Dimensao' freq=2462 MHz)
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: inactive -> authenticating
Jan 24 15:40:43 hugo-K46CA kernel: [   34.893243] wlan1: deauthenticating from f0:82:61:52:98:b1 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: authenticating -> associating
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: associating -> associated
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jan 24 15:40:43 hugo-K46CA kernel: [   34.903797] cfg80211: Calling CRDA to update world regulatory domain
Jan 24 15:40:43 hugo-K46CA kernel: [   34.903825] wlan1: authenticate with f0:82:61:52:98:b1
Jan 24 15:40:43 hugo-K46CA wpa_supplicant[1334]: wlan1: CTRL-EVENT-DISCONNECTED bssid=f0:82:61:52:98:b1 reason=2 locally_generated=1
Jan 24 15:40:43 hugo-K46CA wpa_supplicant[1334]: wlan1: Trying to associate with f0:82:61:52:98:b1 (SSID='Outra Dimensao' freq=2462 MHz)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.918608] wlan1: send auth to f0:82:61:52:98:b1 (try 1/3)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.920586] wlan1: authenticated
Jan 24 15:40:43 hugo-K46CA kernel: [   34.921746] wlan1: associate with f0:82:61:52:98:b1 (try 1/3)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.925532] wlan1: RX AssocResp from f0:82:61:52:98:b1 (capab=0x411 status=0 aid=6)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.925631] wlan1: associated
Jan 24 15:40:43 hugo-K46CA wpa_supplicant[1334]: wlan1: Associated with f0:82:61:52:98:b1
Jan 24 15:40:43 hugo-K46CA kernel: [   34.929923] cfg80211: World regulatory domain updated:
Jan 24 15:40:43 hugo-K46CA kernel: [   34.929926] cfg80211:  DFS Master region: unset
Jan 24 15:40:43 hugo-K46CA kernel: [   34.929928] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.929930] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.929932] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.929933] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.929935] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:43 hugo-K46CA kernel: [   34.929936] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:43 hugo-K46CA wpa_supplicant[1334]: wlan1: WPA: Key negotiation completed with f0:82:61:52:98:b1 [PTK=CCMP GTK=CCMP]
Jan 24 15:40:43 hugo-K46CA wpa_supplicant[1334]: wlan1: CTRL-EVENT-CONNECTED - Connection to f0:82:61:52:98:b1 completed [id=0 id_str=]
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <info> Policy set 'Outra Dimensao' (wlan0) as default for IPv4 routing and DNS.
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <info> DNS: starting dnsmasq...
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <warn> dnsmasq not available on the bus, can't update servers.
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <error> [1453657243.560417] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <warn> DNS: plugin dnsmasq update failed
Jan 24 15:40:43 hugo-K46CA NetworkManager[1294]: <info> Writing DNS information to /sbin/resolvconf
Jan 24 15:40:43 hugo-K46CA dnsmasq[1431]: iniciado, versão 2.68 cache desabilitado
Jan 24 15:40:43 hugo-K46CA dnsmasq[1431]: opções de tempo de compilação: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jan 24 15:40:43 hugo-K46CA dnsmasq[1431]: suporte a DBus habilitado: conectado ao barramento do sistema
Jan 24 15:40:43 hugo-K46CA dnsmasq[1431]: aviso: não há servidores upstream configurados
Jan 24 15:40:44 hugo-K46CA wpa_supplicant[1334]: wlan1: WPA: Key negotiation completed with f0:82:61:52:98:b1 [PTK=CCMP GTK=CCMP]
Jan 24 15:40:44 hugo-K46CA avahi-daemon[1249]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::de85:deff:fe9d:7dc1.
Jan 24 15:40:44 hugo-K46CA avahi-daemon[1249]: New relevant interface wlan1.IPv6 for mDNS.
Jan 24 15:40:44 hugo-K46CA avahi-daemon[1249]: Registering new address record for fe80::de85:deff:fe9d:7dc1 on wlan1.*.
Jan 24 15:40:44 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) successful, device activated.
Jan 24 15:40:44 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan 24 15:40:44 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: 4-way handshake -> authenticating
Jan 24 15:40:44 hugo-K46CA NetworkManager[1294]: <warn> Connection disconnected (reason -2)
Jan 24 15:40:44 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: authenticating -> associating
Jan 24 15:40:44 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: associating -> associated
Jan 24 15:40:44 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
Jan 24 15:40:44 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
Jan 24 15:40:44 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Outra Dimensao'.
Jan 24 15:40:44 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 24 15:40:44 hugo-K46CA NetworkManager[1294]: <warn> dnsmasq appeared on DBus: :1.15
Jan 24 15:40:44 hugo-K46CA NetworkManager[1294]: <info> Writing DNS information to /sbin/resolvconf
Jan 24 15:40:44 hugo-K46CA dnsmasq[1431]: configurando servidores upstream do DBus
Jan 24 15:40:44 hugo-K46CA dnsmasq[1431]: usando nome de servidor 192.168.1.1#53
Jan 24 15:40:44 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan 24 15:40:46 hugo-K46CA kernel: [   38.202822] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
Jan 24 15:40:47 hugo-K46CA kernel: [   38.762035] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jan 24 15:40:47 hugo-K46CA avahi-daemon[1249]: Joining mDNS multicast group on interface virbr0.IPv4 with address 192.168.122.1.
Jan 24 15:40:47 hugo-K46CA avahi-daemon[1249]: New relevant interface virbr0.IPv4 for mDNS.
Jan 24 15:40:47 hugo-K46CA avahi-daemon[1249]: Registering new address record for 192.168.122.1 on virbr0.IPv4.
Jan 24 15:40:47 hugo-K46CA dnsmasq[1641]: started, version 2.68 cachesize 150
Jan 24 15:40:47 hugo-K46CA dnsmasq[1641]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jan 24 15:40:47 hugo-K46CA dnsmasq-dhcp[1641]: DHCP, IP range 192.168.122.2 -- 192.168.122.254, lease time 1h
Jan 24 15:40:47 hugo-K46CA dnsmasq-dhcp[1641]: DHCP, sockets bound exclusively to interface virbr0
Jan 24 15:40:47 hugo-K46CA dnsmasq[1641]: reading /etc/resolv.conf
Jan 24 15:40:47 hugo-K46CA dnsmasq[1641]: using nameserver 127.0.1.1#53
Jan 24 15:40:47 hugo-K46CA dnsmasq[1641]: read /etc/hosts - 7 addresses
Jan 24 15:40:47 hugo-K46CA dnsmasq[1641]: read /var/lib/libvirt/dnsmasq/default.addnhosts - 0 addresses
Jan 24 15:40:47 hugo-K46CA dnsmasq-dhcp[1641]: read /var/lib/libvirt/dnsmasq/default.hostsfile
Jan 24 15:40:47 hugo-K46CA kernel: [   39.105997] init: Failed to spawn nmbd main process: unable to execute: No such file or directory
Jan 24 15:40:47 hugo-K46CA whoopsie[1312]: Could not determine if this is a default route:
Jan 24 15:40:47 hugo-K46CA whoopsie[1312]: Timeout was reached
Jan 24 15:40:48 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jan 24 15:40:48 hugo-K46CA accounts-daemon[1669]: started daemon version 0.6.35
Jan 24 15:40:48 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jan 24 15:40:49 hugo-K46CA acpid: client connected from 1666[0:0]
Jan 24 15:40:49 hugo-K46CA acpid: 1 client rule loaded
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/virbr0, iface: virbr0)
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/virbr0, iface: virbr0): no ifupdown configuration found.
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]: <warn> failed to allocate link cache: (-12) Object not found
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]: <info> (virbr0): ignoring bridge not created by NetworkManager
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]: <info> WiFi hardware radio set enabled
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]: <info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]: <info> dhclient started with pid 1686
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Beginning IP6 addrconf.
Jan 24 15:40:50 hugo-K46CA avahi-daemon[1249]: Withdrawing address record for fe80::de85:deff:fe9d:7dc1 on wlan1.
Jan 24 15:40:50 hugo-K46CA avahi-daemon[1249]: Leaving mDNS multicast group on interface wlan1.IPv6 with address fe80::de85:deff:fe9d:7dc1.
Jan 24 15:40:50 hugo-K46CA avahi-daemon[1249]: Interface wlan1.IPv6 no longer relevant for mDNS.
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Jan 24 15:40:50 hugo-K46CA dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jan 24 15:40:50 hugo-K46CA dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jan 24 15:40:50 hugo-K46CA dhclient: All rights reserved.
Jan 24 15:40:50 hugo-K46CA dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan 24 15:40:50 hugo-K46CA dhclient: 
Jan 24 15:40:50 hugo-K46CA NetworkManager[1294]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
Jan 24 15:40:50 hugo-K46CA dhclient: Listening on LPF/wlan1/dc:85:de:9d:7d:c1
Jan 24 15:40:50 hugo-K46CA dhclient: Sending on   LPF/wlan1/dc:85:de:9d:7d:c1
Jan 24 15:40:50 hugo-K46CA dhclient: Sending on   Socket/fallback
Jan 24 15:40:50 hugo-K46CA dhclient: DHCPREQUEST of 192.168.1.9 on wlan1 to 255.255.255.255 port 67 (xid=0x7e09f698)
Jan 24 15:40:50 hugo-K46CA kernel: [   41.715622] init: plymouth-upstart-bridge main process ended, respawning
Jan 24 15:40:50 hugo-K46CA kernel: [   41.721354] init: plymouth-upstart-bridge main process (1691) terminated with status 1
Jan 24 15:40:50 hugo-K46CA kernel: [   41.721372] init: plymouth-upstart-bridge main process ended, respawning
Jan 24 15:40:50 hugo-K46CA whoopsie[1312]: online
Jan 24 15:40:50 hugo-K46CA kernel: [   42.086694] cgroup: systemd-logind (1078) created nested cgroup for controller "memory" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
Jan 24 15:40:50 hugo-K46CA kernel: [   42.086698] cgroup: "memory" requires setting use_hierarchy to 1 on the root
Jan 24 15:40:51 hugo-K46CA kernel: [   42.931748] wlan1: deauthenticated from f0:82:61:52:98:b1 (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
Jan 24 15:40:50 hugo-K46CA wpa_supplicant[1334]: message repeated 6 times: [ wlan1: WPA: Key negotiation completed with f0:82:61:52:98:b1 [PTK=CCMP GTK=CCMP]]
Jan 24 15:40:51 hugo-K46CA wpa_supplicant[1334]: wlan1: CTRL-EVENT-DISCONNECTED bssid=f0:82:61:52:98:b1 reason=15
Jan 24 15:40:51 hugo-K46CA NetworkManager[1294]: <warn> Connection disconnected (reason 15)
Jan 24 15:40:51 hugo-K46CA kernel: [   42.961727] cfg80211: Calling CRDA to update world regulatory domain
Jan 24 15:40:51 hugo-K46CA kernel: [   42.964301] cfg80211: World regulatory domain updated:
Jan 24 15:40:51 hugo-K46CA kernel: [   42.964305] cfg80211:  DFS Master region: unset
Jan 24 15:40:51 hugo-K46CA kernel: [   42.964306] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 24 15:40:51 hugo-K46CA kernel: [   42.964308] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:51 hugo-K46CA kernel: [   42.964310] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:51 hugo-K46CA kernel: [   42.964312] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:51 hugo-K46CA kernel: [   42.964313] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:51 hugo-K46CA kernel: [   42.964314] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:40:51 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: completed -> disconnected
Jan 24 15:40:51 hugo-K46CA wpa_supplicant[1334]: wlan1: CTRL-EVENT-SCAN-STARTED 
Jan 24 15:40:51 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: disconnected -> scanning
Jan 24 15:40:51 hugo-K46CA NetworkManager[1294]: <warn> error monitoring device for netlink events: erro ao processar mensagem do netlink: Object busy
Jan 24 15:40:51 hugo-K46CA avahi-daemon[1249]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::de85:deff:fe9d:7dc1.
Jan 24 15:40:51 hugo-K46CA avahi-daemon[1249]: New relevant interface wlan1.IPv6 for mDNS.
Jan 24 15:40:51 hugo-K46CA avahi-daemon[1249]: Registering new address record for fe80::de85:deff:fe9d:7dc1 on wlan1.*.
Jan 24 15:40:52 hugo-K46CA kernel: [   44.006281] wlan1: authenticate with f0:82:61:52:98:b1
Jan 24 15:40:52 hugo-K46CA wpa_supplicant[1334]: wlan1: SME: Trying to authenticate with f0:82:61:52:98:b1 (SSID='Outra Dimensao' freq=2462 MHz)
Jan 24 15:40:52 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: scanning -> authenticating
Jan 24 15:40:52 hugo-K46CA kernel: [   44.028220] wlan1: send auth to f0:82:61:52:98:b1 (try 1/3)
Jan 24 15:40:52 hugo-K46CA wpa_supplicant[1334]: wlan1: Trying to associate with f0:82:61:52:98:b1 (SSID='Outra Dimensao' freq=2462 MHz)
Jan 24 15:40:52 hugo-K46CA kernel: [   44.030331] wlan1: authenticated
Jan 24 15:40:52 hugo-K46CA kernel: [   44.033911] wlan1: associate with f0:82:61:52:98:b1 (try 1/3)
Jan 24 15:40:52 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: authenticating -> associating
Jan 24 15:40:52 hugo-K46CA kernel: [   44.037644] wlan1: RX AssocResp from f0:82:61:52:98:b1 (capab=0x411 status=0 aid=6)
Jan 24 15:40:52 hugo-K46CA kernel: [   44.037753] wlan1: associated
Jan 24 15:40:52 hugo-K46CA wpa_supplicant[1334]: wlan1: Associated with f0:82:61:52:98:b1
Jan 24 15:40:52 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: associating -> associated
Jan 24 15:40:52 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: associated -> 4-way handshake
Jan 24 15:40:52 hugo-K46CA wpa_supplicant[1334]: wlan1: WPA: Key negotiation completed with f0:82:61:52:98:b1 [PTK=CCMP GTK=CCMP]
Jan 24 15:40:52 hugo-K46CA wpa_supplicant[1334]: wlan1: CTRL-EVENT-CONNECTED - Connection to f0:82:61:52:98:b1 completed [id=0 id_str=]
Jan 24 15:40:52 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: 4-way handshake -> completed
Jan 24 15:40:53 hugo-K46CA dhclient: DHCPREQUEST of 192.168.1.9 on wlan1 to 255.255.255.255 port 67 (xid=0x7e09f698)
Jan 24 15:40:53 hugo-K46CA dhclient: DHCPACK of 192.168.1.9 from 192.168.1.1
Jan 24 15:40:53 hugo-K46CA dhclient: bound to 192.168.1.9 -- renewal in 33775 seconds.
Jan 24 15:40:53 hugo-K46CA NetworkManager[1294]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
Jan 24 15:40:53 hugo-K46CA NetworkManager[1294]: <info>   address 192.168.1.9
Jan 24 15:40:53 hugo-K46CA NetworkManager[1294]: <info>   prefix 24 (255.255.255.0)
Jan 24 15:40:53 hugo-K46CA NetworkManager[1294]: <info>   gateway 192.168.1.1
Jan 24 15:40:53 hugo-K46CA NetworkManager[1294]: <info>   nameserver '192.168.1.1'
Jan 24 15:40:53 hugo-K46CA NetworkManager[1294]: <info>   domain name 'Home'
Jan 24 15:40:53 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jan 24 15:40:53 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
Jan 24 15:40:53 hugo-K46CA avahi-daemon[1249]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.9.
Jan 24 15:40:53 hugo-K46CA avahi-daemon[1249]: New relevant interface wlan1.IPv4 for mDNS.
Jan 24 15:40:53 hugo-K46CA avahi-daemon[1249]: Registering new address record for 192.168.1.9 on wlan1.IPv4.
Jan 24 15:40:54 hugo-K46CA NetworkManager[1294]: <info> (wlan1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jan 24 15:40:54 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
Jan 24 15:40:54 hugo-K46CA NetworkManager[1294]: <info> (wlan1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jan 24 15:40:54 hugo-K46CA NetworkManager[1294]: <info> Writing DNS information to /sbin/resolvconf
Jan 24 15:40:54 hugo-K46CA dnsmasq[1431]: configurando servidores upstream do DBus
Jan 24 15:40:54 hugo-K46CA dnsmasq[1431]: usando nome de servidor 192.168.1.1#53
Jan 24 15:40:54 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) successful, device activated.
Jan 24 15:40:56 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jan 24 15:40:56 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jan 24 15:40:56 hugo-K46CA rtkit-daemon[1826]: Successfully called chroot.
Jan 24 15:40:56 hugo-K46CA rtkit-daemon[1826]: Successfully dropped privileges.
Jan 24 15:40:56 hugo-K46CA rtkit-daemon[1826]: Successfully limited resources.
Jan 24 15:40:56 hugo-K46CA rtkit-daemon[1826]: Running.
Jan 24 15:40:56 hugo-K46CA rtkit-daemon[1826]: Watchdog thread running.
Jan 24 15:40:56 hugo-K46CA rtkit-daemon[1826]: Canary thread running.
Jan 24 15:40:56 hugo-K46CA rtkit-daemon[1826]: Successfully made thread 1824 of process 1824 (n/a) owned by '112' high priority at nice level -11.
Jan 24 15:40:56 hugo-K46CA rtkit-daemon[1826]: Supervising 1 threads of 1 processes of 1 users.
Jan 24 15:40:57 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jan 24 15:40:57 hugo-K46CA ntpdate[1554]: adjust time server 91.189.89.199 offset -0.413361 sec
Jan 24 15:40:57 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.UPower'
Jan 24 15:40:58 hugo-K46CA anacron[1977]: Anacron 2.3 started on 2016-01-24
Jan 24 15:40:58 hugo-K46CA anacron[1977]: Normal exit (0 jobs run)
Jan 24 15:40:59 hugo-K46CA rtkit-daemon[1826]: Successfully made thread 2056 of process 1824 (n/a) owned by '112' RT at priority 5.
Jan 24 15:40:59 hugo-K46CA rtkit-daemon[1826]: Supervising 2 threads of 1 processes of 1 users.
Jan 24 15:40:59 hugo-K46CA rtkit-daemon[1826]: Successfully made thread 2057 of process 1824 (n/a) owned by '112' RT at priority 5.
Jan 24 15:40:59 hugo-K46CA rtkit-daemon[1826]: Supervising 3 threads of 1 processes of 1 users.
Jan 24 15:40:59 hugo-K46CA rtkit-daemon[1826]: Successfully made thread 2059 of process 2059 (n/a) owned by '112' high priority at nice level -11.
Jan 24 15:40:59 hugo-K46CA rtkit-daemon[1826]: Supervising 4 threads of 2 processes of 1 users.
Jan 24 15:40:59 hugo-K46CA pulseaudio[2059]: [pulseaudio] pid.c: Daemon already running.
Jan 24 15:41:00 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jan 24 15:41:00 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jan 24 15:41:00 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jan 24 15:41:01 hugo-K46CA colord: Using config file /etc/colord.conf
Jan 24 15:41:01 hugo-K46CA colord: Using mapping database file /var/lib/colord/mapping.db
Jan 24 15:41:01 hugo-K46CA colord: Using device database file /var/lib/colord/storage.db
Jan 24 15:41:01 hugo-K46CA colord: loaded plugin libcd_plugin_camera.so
Jan 24 15:41:01 hugo-K46CA colord: loaded plugin libcd_plugin_scanner.so
Jan 24 15:41:01 hugo-K46CA colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Jan 24 15:41:01 hugo-K46CA colord: Daemon ready for requests
Jan 24 15:41:01 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Jan 24 15:41:01 hugo-K46CA colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.sleep-wake: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:02 hugo-K46CA NetworkManager[1294]: <info> (wlan0): IP6 addrconf timed out or failed.
Jan 24 15:41:02 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan 24 15:41:02 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan 24 15:41:02 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jan 24 15:41:03 hugo-K46CA wpa_supplicant[1334]: wlan1: CTRL-EVENT-SCAN-STARTED 
Jan 24 15:41:04 hugo-K46CA kernel: [   56.027482] audit_printk_skb: 138 callbacks suppressed
Jan 24 15:41:04 hugo-K46CA kernel: [   56.027485] audit: type=1400 audit(1453657264.402:82): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2298 comm="apparmor_parser"
Jan 24 15:41:04 hugo-K46CA kernel: [   56.027492] audit: type=1400 audit(1453657264.402:83): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2298 comm="apparmor_parser"
Jan 24 15:41:04 hugo-K46CA kernel: [   56.027875] audit: type=1400 audit(1453657264.402:84): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2298 comm="apparmor_parser"
Jan 24 15:41:06 hugo-K46CA rtkit-daemon[1826]: Successfully made thread 2353 of process 2353 (n/a) owned by '1000' high priority at nice level -11.
Jan 24 15:41:06 hugo-K46CA rtkit-daemon[1826]: Supervising 4 threads of 2 processes of 2 users.
Jan 24 15:41:07 hugo-K46CA rtkit-daemon[1826]: Successfully made thread 2356 of process 2353 (n/a) owned by '1000' RT at priority 5.
Jan 24 15:41:07 hugo-K46CA rtkit-daemon[1826]: Supervising 5 threads of 2 processes of 2 users.
Jan 24 15:41:07 hugo-K46CA rtkit-daemon[1826]: Successfully made thread 2357 of process 2353 (n/a) owned by '1000' RT at priority 5.
Jan 24 15:41:07 hugo-K46CA rtkit-daemon[1826]: Supervising 6 threads of 2 processes of 2 users.
Jan 24 15:41:07 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Jan 24 15:41:07 hugo-K46CA colord: Device added: xrandr-AU Optronics
Jan 24 15:41:07 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.locale1'
Jan 24 15:41:07 hugo-K46CA colord: Automatic metadata add icc-b448dcf96707810d858c7e35dee3a149 to xrandr-AU Optronics
Jan 24 15:41:07 hugo-K46CA colord: Profile added: icc-b448dcf96707810d858c7e35dee3a149
Jan 24 15:41:07 hugo-K46CA ntpdate[2070]: adjust time server 91.189.89.199 offset -0.410813 sec
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:177:2: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:215:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:238:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:295:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:302:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:313:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:321:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:333:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:352:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:358:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:410:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:417:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:429:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:558:52: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:755:14: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:761:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:808:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:814:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:861:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:867:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:914:15: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:920:15: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1062:13: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1303:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1315:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1331:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1353:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1369:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1628:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1845:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1881:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1888:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1896:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1933:28: No property named '-gtk-icon-transform'
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2169:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2176:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2183:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2196:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2310:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2320:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2330:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2351:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2407:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2414:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2422:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2436:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2458:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2482:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2510:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2526:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2548:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2571:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2594:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2619:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2641:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2675:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2691:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2705:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2720:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2735:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2756:40: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2781:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2829:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2847:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2874:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2901:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2929:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2960:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2983:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3011:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3025:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3061:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3081:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3305:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3316:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3331:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3368:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3375:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3383:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3395:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3572:27: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3602:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3609:31: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3658:35: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3696:52: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3707:58: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3736:50: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3810:23: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: xfce.css:7:36: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:177:2: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:215:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:238:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:295:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:302:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:313:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:321:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:333:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:352:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:358:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:410:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:417:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:429:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:558:52: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:755:14: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:761:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:808:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:814:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:861:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:867:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:914:15: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:920:15: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1062:13: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1303:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1315:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1331:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1353:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1369:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1628:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1845:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1881:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1888:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1896:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1933:28: No property named '-gtk-icon-transform'
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2169:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2176:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2183:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2196:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2310:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2320:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2330:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2351:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2407:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2414:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2422:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2436:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2458:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2482:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2510:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2526:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2548:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2571:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2594:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2619:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2641:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2675:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2691:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2705:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2720:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2735:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2756:40: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2781:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2829:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2847:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2874:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2901:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2929:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2960:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2983:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3011:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3025:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3061:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3081:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3305:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3316:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3331:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3368:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3375:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3383:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3395:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3572:27: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3602:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3609:31: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3658:35: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3696:52: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3707:58: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3736:50: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3810:23: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: xfce.css:7:36: Missing name of pseudo-class
Jan 24 15:41:10 hugo-K46CA NetworkManager[1294]: <info> (wlan1): IP6 addrconf timed out or failed.
Jan 24 15:41:10 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan 24 15:41:10 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan 24 15:41:10 hugo-K46CA NetworkManager[1294]: <info> Activation (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jan 24 15:41:12 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Jan 24 15:41:12 hugo-K46CA udisksd[2505]: udisks daemon version 2.1.3 starting
Jan 24 15:41:12 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Jan 24 15:41:12 hugo-K46CA udisksd[2505]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Jan 24 15:45:54 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jan 24 15:45:54 hugo-K46CA kernel: [  346.368477] systemd-hostnamed[5884]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Jan 24 15:45:54 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jan 24 15:49:58 hugo-K46CA NetworkManager[1294]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Jan 24 15:52:10 hugo-K46CA NetworkManager[1294]: <info> (wlan1): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
Jan 24 15:52:10 hugo-K46CA NetworkManager[1294]: <info> (wlan1): deactivating device (reason 'user-requested') [39]
Jan 24 15:52:10 hugo-K46CA NetworkManager[1294]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 1686
Jan 24 15:52:10 hugo-K46CA avahi-daemon[1249]: Withdrawing address record for 192.168.1.9 on wlan1.
Jan 24 15:52:10 hugo-K46CA avahi-daemon[1249]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.9.
Jan 24 15:52:10 hugo-K46CA avahi-daemon[1249]: Interface wlan1.IPv4 no longer relevant for mDNS.
Jan 24 15:52:10 hugo-K46CA NetworkManager[1294]: <info> Policy set 'Outra Dimensao' (wlan0) as default for IPv4 routing and DNS.
Jan 24 15:52:10 hugo-K46CA NetworkManager[1294]: <info> Writing DNS information to /sbin/resolvconf
Jan 24 15:40:54 hugo-K46CA dnsmasq[1431]: usando nome de servidor 192.168.1.1#53
Jan 24 15:52:10 hugo-K46CA dnsmasq[1431]: configurando servidores upstream do DBus
Jan 24 15:52:10 hugo-K46CA dnsmasq[1431]: usando nome de servidor 192.168.1.1#53
Jan 24 15:52:10 hugo-K46CA kernel: [  723.060790] wlan1: deauthenticating from f0:82:61:52:98:b1 by local choice (Reason: 3=DEAUTH_LEAVING)
Jan 24 15:52:10 hugo-K46CA kernel: [  723.070812] cfg80211: Calling CRDA to update world regulatory domain
Jan 24 15:51:55 hugo-K46CA wpa_supplicant[1334]: message repeated 7 times: [ wlan1: CTRL-EVENT-SCAN-STARTED ]
Jan 24 15:52:10 hugo-K46CA wpa_supplicant[1334]: wlan1: CTRL-EVENT-DISCONNECTED bssid=f0:82:61:52:98:b1 reason=3 locally_generated=1
Jan 24 15:52:10 hugo-K46CA kernel: [  723.073978] cfg80211: World regulatory domain updated:
Jan 24 15:52:10 hugo-K46CA kernel: [  723.073983] cfg80211:  DFS Master region: unset
Jan 24 15:52:10 hugo-K46CA kernel: [  723.073985] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 24 15:52:10 hugo-K46CA kernel: [  723.073989] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:52:10 hugo-K46CA kernel: [  723.073991] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:52:10 hugo-K46CA kernel: [  723.073994] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:52:10 hugo-K46CA kernel: [  723.073996] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:52:10 hugo-K46CA kernel: [  723.073999] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 24 15:52:10 hugo-K46CA NetworkManager[1294]: <warn> Connection disconnected (reason -3)
Jan 24 15:52:10 hugo-K46CA NetworkManager[1294]: <info> (wlan1): supplicant interface state: completed -> disconnected
Jan 24 15:52:10 hugo-K46CA NetworkManager[1294]: <warn> Connection disconnected (reason -3)
Jan 24 15:52:10 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan 24 15:52:10 hugo-K46CA wpa_supplicant[1334]: wlan1: CTRL-EVENT-SCAN-STARTED 
Jan 24 15:52:10 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
```

---

### Post by Petro Dawg on 2016-01-25
I'm not a log reading guru, but a couple things stood out to me.  Hopefully one of the gurus around can look at my excerpts and say yay or nay on if there errors below might be an issue with long log time.  

Looks like your boot up started at 15:40:31 and there are no real significant pauses until you hit 15:41:12 which correlates with some warnings...
```
Jan 24 15:41:12 hugo-K46CA udisksd[2505]: Acquired the name org.freedesktop.UDisks2 on the system message busJan 24 15:45:54 hugo-K46CA dbus[1028]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
**Jan 24 15:45:54 hugo-K46CA kernel: [  346.368477] systemd-hostnamed[5884]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!**
Jan 24 15:45:54 hugo-K46CA dbus[1028]: [system] Successfully activated service 'org.freedesktop.hostname1'
**Jan 24 15:49:58 hugo-K46CA NetworkManager[1294]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted**
Jan 24 15:52:10 hugo-K46CA NetworkManager[1294]: <info> (wlan1): device state change: activated -> disconnected (reason 'user-requested') [100 30 39]
```

I also saw a couple other errors, but they didn't seem to eat up much time as far as the log time-stamp was concerned..

Some NetworkManager warnings (I also get these so I doubt they are a big deal, except for the timeout message at the bottom)...
```
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.sleep-wake: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jan 24 15:41:01 hugo-K46CA NetworkManager[1294]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
**Jan 24 15:41:02 hugo-K46CA NetworkManager[1294]: <info> (wlan0): IP6 addrconf timed out or failed.**
```

And a whole lot of these...
```
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:177:2: Missing name of pseudo-classJan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:215:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:238:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:295:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:302:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:313:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:321:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:333:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:352:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:358:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:410:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:417:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:429:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:558:52: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:755:14: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:761:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:808:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:814:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:861:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:867:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:914:15: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:920:15: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1062:13: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1303:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1315:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1331:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1353:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1369:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1628:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1845:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1881:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1888:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1896:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1933:28: No property named '-gtk-icon-transform'
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2169:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2176:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2183:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2196:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2310:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2320:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2330:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2351:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2407:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2414:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2422:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2436:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2458:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2482:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2510:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2526:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2548:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2571:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2594:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2619:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2641:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2675:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2691:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2705:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2720:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2735:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2756:40: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2781:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2829:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2847:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2874:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2901:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2929:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2960:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2983:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3011:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3025:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3061:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3081:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3305:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3316:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3331:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3368:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3375:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3383:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3395:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3572:27: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3602:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3609:31: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3658:35: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3696:52: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3707:58: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3736:50: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3810:23: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: xfce.css:7:36: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:177:2: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:215:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:238:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:295:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:302:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:313:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:321:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:333:8: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:352:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:358:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:410:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:417:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:429:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:558:52: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:755:14: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:761:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:808:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:814:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:861:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:867:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:914:15: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:920:15: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1062:13: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1303:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1315:17: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1331:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1353:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1369:22: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1628:18: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1845:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1881:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1888:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1896:29: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:1933:28: No property named '-gtk-icon-transform'
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2169:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2176:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2183:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2196:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2310:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2320:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2330:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2351:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2407:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2414:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2422:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2436:32: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2458:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2482:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2510:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2526:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2548:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2571:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2594:16: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2619:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2641:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2675:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2691:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2705:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2720:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2735:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2756:40: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2781:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2829:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2847:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2874:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2901:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2929:39: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2960:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:2983:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3011:20: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3025:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3061:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3081:34: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3305:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3316:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3331:12: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3368:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3375:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3383:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3395:21: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3572:27: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3602:25: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3609:31: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3658:35: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3696:52: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3707:58: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3736:50: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:3810:23: Missing name of pseudo-class
Jan 24 15:41:09 hugo-K46CA gnome-session[2262]: Gtk-WARNING: Theme parsing error: xfce.css:7:36: Missing name of pseudo-class
**Jan 24 15:41:10 hugo-K46CA NetworkManager[1294]: <info> (wlan1): IP6 addrconf timed out or failed**.
```

---

