---
title: "System hang"
date: 2006-08-19
forum: General Help
---

### Post by K_V_B on 2006-08-19
Hello,

Today my server locked up completely, resulting in me having to powercycle it (something I absolutely don't like doing to a server).

The Server is a Dell Poweredge SC430, with Pentium D processor. Because this processor has EMT64 extentions I installed the "amd64" veriosn of Ubuntu 6.06 on it. Kernel version is 2.6.15-26-amd64-server

This is what happened:

- In order to copy some stuff from the NAS device this serer will replace I had mounted a SAMBA share using smbmount. After having copied the stuff I wanted to unmount the share, but the system refused that, claiming the mount point was still busy. Thinking I might have overlooked something I executed the folowing command, in order to find out which process might be involved:

sudo fuser -m /mnt/nas

The command hung, and thinking it might just have been the command I tried to ssh in to my server from another window on my desktop. But the ssh failed too. It looked as if the server was completely hung. After a while I just powercycled it.

I then had a look in to the logfiles, and found this in the file kernel.log:

Aug 19 10:23:59 aare kernel: [105974.645413] Unable to handle kernel NULL pointer dereference at 0000000000000001 RIP: 
Aug 19 10:23:59 aare kernel: [105974.645692] <ffffffff882ef7c1>{:smbfs:smbiod+513}
Aug 19 10:23:59 aare kernel: [105974.646227] PGD 465e067 PUD 180a1067 PMD 0 
Aug 19 10:23:59 aare kernel: [105974.646621] Oops: 0000 [1] SMP 
Aug 19 10:23:59 aare kernel: [105974.646902] CPU 0 
Aug 19 10:23:59 aare kernel: [105974.647072] Modules linked in: smbfs ipv6 ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq
_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec i2c_core af_packe
t dm_mod parport_pc lp parport tg3 psmouse serio_raw hw_random pcspkr shpchp pci_hotplug evdev sg ext3 jbd raid0 md_mod ide_generic ehci_hcd uhci_hcd
 usbcore sd_mod ata_piix libata scsi_mod ide_cd cdrom piix generic thermal processor fan capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt 
cfbfillrect fbcon tileblit font bitblit softcursor
Aug 19 10:23:59 aare kernel: [105974.653839] Pid: 7986, comm: smbiod Not tainted 2.6.15-26-amd64-server #1
Aug 19 10:23:59 aare kernel: [105974.654139] RIP: 0010:[_end+132429761/2132131840] <ffffffff882ef7c1>{:smbfs:smbiod+513}
Aug 19 10:23:59 aare kernel: [105974.654566] RSP: 0018:ffff810013f29ee8  EFLAGS: 00010203
Aug 19 10:23:59 aare kernel: [105974.654851] RAX: 0000000000000001 RBX: ffff81001d573c00 RCX: ffff810013f29ed4
Aug 19 10:23:59 aare kernel: [105974.655199] RDX: ffff810013f29fd8 RSI: 0000000000000000 RDI: 000000001d573c08
Aug 19 10:23:59 aare kernel: [105974.664673] RBP: 0000000000000000 R08: ffff810013f28000 R09: 0000000000000026
Aug 19 10:23:59 aare kernel: [105974.683860] R10: 0000000000000001 R11: 0000000000000002 R12: 0000000000000007
Aug 19 10:23:59 aare kernel: [105974.702945] R13: ffff81001d5738b8 R14: 0000000000000001 R15: ffff810013f29ee8
Aug 19 10:23:59 aare kernel: [105974.722624] FS:  00002aaaaadfb6d0(0000) GS:ffffffff80452800(0000) knlGS:0000000000000000
Aug 19 10:23:59 aare kernel: [105974.742963] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 19 10:23:59 aare kernel: [105974.753324] CR2: 0000000000000001 CR3: 000000001fbc8000 CR4: 00000000000006e0
Aug 19 10:23:59 aare kernel: [105974.774211] Process smbiod (pid: 7986, threadinfo ffff810013f28000, task ffff81001fbdb750)
Aug 19 10:23:59 aare kernel: [105974.795400] Stack: 0000000000000000 ffff81001fbdb750 ffffffff80153f80 ffff810013f29f00 
Aug 19 10:23:59 aare kernel: [105974.806477]        ffff810013f29f00 ffff810013f29f08 0000000000000282 0000000000000000 
Aug 19 10:23:59 aare kernel: [105974.827937]        ffff81001d573c00 ffff810014dc5c38 
Aug 19 10:23:59 aare kernel: [105974.838857] Call Trace:<ffffffff80153f80>{autoremove_wake_function+0} <ffffffff80110c6a>{child_rip+8}
Aug 19 10:23:59 aare kernel: [105974.860516]        <ffffffff882ef5c0>{:smbfs:smbiod+0} <ffffffff80110c62>{child_rip+0}
Aug 19 10:23:59 aare kernel: [105974.881960]        
Aug 19 10:23:59 aare kernel: [105974.902271] 
Aug 19 10:23:59 aare kernel: [105974.902272] Code: 49 8b 06 4c 89 f3 74 19 49 89 c6 e9 11 ff ff ff c7 43 10 01 
Aug 19 10:23:59 aare kernel: [105974.933783] RIP <ffffffff882ef7c1>{:smbfs:smbiod+513} RSP <ffff810013f29ee8>
Aug 19 10:23:59 aare kernel: [105974.944488] CR2: 0000000000000001
Aug 19 10:24:26 aare kernel: [105974.961941]  <5>smb_add_request: request [ffff810013211e00, mid=44647] timed out!
Aug 19 10:25:03 aare kernel: [106039.037352] smb_add_request: request [ffff810005222e00, mid=44648] timed out!
Aug 19 10:25:32 aare kernel: [106067.556767] smb_add_request: request [ffff810005222080, mid=44649] timed out!
Aug 19 10:26:02 aare kernel: [106097.549673] smb_add_request: request [ffff810005222080, mid=44652] timed out!

What could have been going on here?

(Luckily I won't be needing samba in the future)

---

