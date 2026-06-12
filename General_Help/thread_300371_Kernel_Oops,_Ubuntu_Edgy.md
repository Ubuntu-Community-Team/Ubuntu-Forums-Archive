---
title: "Kernel Oops, Ubuntu Edgy"
date: 2006-11-15
forum: General Help
---

### Post by radu.c on 2006-11-15
The Oops, in all its glory:

[17201926.276000] BUG: unable to handle kernel paging request at virtual address fa9faa00
[17201926.276000]  printing eip:
[17201926.276000] c0168cf7
[17201926.276000] *pde = 00000000
[17201926.276000] Oops: 0000 [#1]
[17201926.276000] SMP
[17201926.276000] Modules linked in: ipv6 binfmt_misc rfcomm l2cap bluetooth powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi sbs pcc_acpi i2c_ec hotkey dev_acpi container button battery asus_acpi ac sbp2 lp af_packet tsdev psmouse serio_raw parport_pc evdev pcspkr parport snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc shpchp pci_hotplug agpgart i2c_core ext3 jbd ohci1394 ieee1394 ohci_hcd forcedeth ehci_hcd usbcore ide_generic ide_disk ide_cd cdrom generic amd74xx sata_nv libata scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability
commoncap
[17201926.276000] CPU:    0
[17201926.276000] EIP:    0060:[<c0168cf7>]    Not tainted VLI
[17201926.276000] EFLAGS: 00010286   (2.6.17-10-generic #2)
[17201926.276000] EIP is at __dentry_open+0x67/0x1e0
[17201926.276000] eax: fa9faa00   ebx: df3b7a40   ecx: 00000000   edx: c1857ec0
[17201926.276000] esi: d3bdc6b0   edi: c2111f44   ebp: 00000000   esp: c2111f10
[17201926.276000] ds: 007b   es: 007b   ss: 0068
[17201926.276000] Process cc1 (pid: 23824, threadinfo=c2110000 task=dff9e030)
[17201926.276000] Stack: c1857ec0 c9850090 df3b7a40 ffffff9c c2111f44 00000004 c0168f25 df3b7a40
[17201926.276000]        00000000 00000100 c0168f80 000001b6 c2111f44 c9850090 c1857ec0 00000000
[17201926.276000]        007d402a 00000000 00000101 00000001 00000000 0000001c 00000004 dfc19e08
[17201926.276000] Call Trace:
[17201926.276000]  <c0168f25> nameidata_to_filp+0x35/0x40  <c0168f80> do_filp_open+0x50/0x60
[17201926.276000]  <c0168c23> get_unused_fd+0x53/0xc0  <c0168fda> do_sys_open+0x4a/0xe0
[17201926.276000]  <c01690ac> sys_open+0x1c/0x20  <c0102fbb> sysenter_past_esp+0x54/0x79
[17201926.276000] Code: 00 00 8b 44 24 04 89 43 08 8b 04 24 c7 43 20 00 00 00 00 c7 43 24 00 00 00 00 89 43 0c 8b 86 98 00 00 00 85 c0 0f 84 5e 01 00 00 <8b> 10 85 d2 74 25 b8 00
e0 ff ff 21 e0 83 3a 02 8b 40 10 0f 84
[17201926.276000] EIP: [<c0168cf7>] __dentry_open+0x67/0x1e0 SS:ESP 0068:c2111f10
[17201926.276000]


# cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 47
model name      : AMD Athlon(tm) 64 Processor 3000+
stepping        : 2
cpu MHz         : 1800.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips        : 3643.40

# uname -a
Linux alx-desktop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux


# free
             total       used       free     shared    buffers     cached
Mem:        970464     950340      20124          0     117840     599152
-/+ buffers/cache:     233348     737116
Swap:      2843464      17620    2825844


Motherboard: [ASUS A8N-VM CSM]("http://www.asus.com/products.aspx?l1=3&l2=15&l3=210&model=766&modelmenu=1")

IDE Hard drive

What I was doing at the time: I was compiling two things at the same time (the Oops killed one of them).



Any ideas what could cause this?

---

### Post by po0f on 2006-11-15
radu.c,

What were you compiling at the same time?  Could have something to do with it.  Plus the fact that you were compiling two things at the same time.  ;)

---

### Post by radu.c on 2006-11-15
Got another one. I'll go check my memory for errors.

[17205047.568000] CPU:    0
[17205047.568000] EIP:    0060:[<c017a8d2>]    Not tainted VLI
[17205047.568000] EFLAGS: 00010286   (2.6.17-10-generic #2)
[17205047.568000] EIP is at __link_path_walk+0x7c2/0xf20
[17205047.568000] eax: d896d5b8   ebx: cb5390d4   ecx: 00000000   edx: faa08200
[17205047.568000] esi: c93f78a4   edi: 24ce92b1   ebp: dfc0f04f   esp: c8f3fe14
[17205047.568000] ds: 007b   es: 007b   ss: 0068
[17205047.568000] Process cc1plus (pid: 18965, threadinfo=c8f3e000 task=d380e030)
[17205047.568000] Stack: c8f3ff44 dfc0f045 00000101 c8f3e000 00000001 00000001 ffffffff 00000000
[17205047.568000]        24ce92b1 0000000a dfc0f045 c1857ec0 d896d5b8 c8f3e000 c1857ec0 c19b35b8
[17205047.568000]        c8f3ff44 c017b081 dfc0f000 c19b35b8 c1857ec0 00000000 007d881d 00000000
[17205047.568000] Call Trace:
[17205047.568000]  <c017b081> link_path_walk+0x51/0xf0  <c0168c23> get_unused_fd+0x53/0xc0
[17205047.568000]  <c017b368> do_path_lookup+0xb8/0x260  <c017bff1> __path_lookup_intent_open+0x51/0xa0
[17205047.568000]  <c017c0d0> path_lookup_open+0x20/0x30  <c017c1da> open_namei+0x5a/0x6b0
[17205047.568000]  <c015921a> __handle_mm_fault+0x4ea/0x900  <c0168f63> do_filp_open+0x33/0x60
[17205047.568000]  <c0168c23> get_unused_fd+0x53/0xc0  <c0168fda> do_sys_open+0x4a/0xe0
[17205047.568000]  <c01690ac> sys_open+0x1c/0x20  <c0102fbb> sysenter_past_esp+0x54/0x79
[17205047.568000] Code: fa ff ff 8b 44 24 30 f6 44 24 08 01 8b 58 0c 0f 84 b4 03 00 00 85 db 0f 84 ac 03 00 00 8b 93 94 00 00 00 85 d2 0f 84 9e 03 00 00 <8b> 4a 28 85 c9 0f 84 93
03 00 00 be 00 e0 ff ff 21 e6 8b 16 83
[17205047.568000] EIP: [<c017a8d2>] __link_path_walk+0x7c2/0xf20 SS:ESP 0068:c8f3fe14
[17205047.568000]

---

### Post by radu.c on 2006-11-15
> **po0f said:**
> radu.c,

What were you compiling at the same time?  Could have something to do with it.  Plus the fact that you were compiling two things at the same time.  ;)

Some big userland software which takes a while to compile (10-20 minutes). One of them was the SDL library with some patches - this one is the one that got killed, but re-starting the build didn't Oops again. The second Oops came also while I was compiling something. I'd say it has something to do with high CPU load, yet the machine worked just fine with Debian Sarge.

---

### Post by radu.c on 2006-11-16
Yep, I have some very strange random memory error. Out of 29 passes, 7 of them display red in test 7 (one is in test 6), same bits each time, but at unrelated positions in memory. Last failed pass is 18. Each failed pass has a count of 1.

Now, there are a few possibile points of failure:
1. memory "dead pixel"-style bits (on my monitor, if I push the dead pixels with my finger, they come back to life for a while)
2. memory slot bad contacts
3. memory controller (which is intergrated in the CPU) random failure
4. faulty memory access paths on the motheboard

I'm voting for door number 2.

---

### Post by po0f on 2006-11-16
radu.c,

What you could try to do is pull your memory modules out of their sockets, clean the contacts with distilled water (and maybe the sockets themselves if you have a small enough brush), and firmly replace them after they dry.  If that doesn't work, it's probably bum memory chips and/or mobo.

[EDIT]

You mentioned high CPU usage.  Are the temps really high?  This will sometimes affect certain components in a computer the way you are describing.

---

### Post by radu.c on 2006-11-17
> **po0f said:**
> radu.c,

What you could try to do is pull your memory modules out of their sockets, clean the contacts with distilled water (and maybe the sockets themselves if you have a small enough brush), and firmly replace them after they dry.  If that doesn't work, it's probably bum memory chips and/or mobo.

[EDIT]

You mentioned high CPU usage.  Are the temps really high?  This will sometimes affect certain components in a computer the way you are describing.

I already moved the memory modules to another computer and they're OK there. In the meantime, a colleague of mine switched the original computer's power supply voltage from 220V to 110V and fried it, so... But the second computer works just fine.

Thanks for your help.

---

### Post by sisooktom on 2006-12-01
I have the same CPU and I'm getting pretty much the same oops.  My machine is completely unusable w/Edgy; it hardlocks shortly after this.  It's not a hardware problem either, the machine runs perfectly with Dapper and FC6...

---

