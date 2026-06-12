---
title: "How to pinpoint system crash?"
date: 2018-02-12
forum: General Help
---

### Post by mma8x on 2018-02-12
I built the system about 1-2 years ago. Meant to be used primarily as a mythtv backend server. Running Ubuntu 16.04.1 LTS. IIRC I installed mythbuntu and kde. Since day 1, the system has had random freezes. Sometimes daily, sometimes it will go weeks. Screen will just freeze up, system unresponsive, nothing in the logs that I can find (many times the last entry will just be a cron job). I initially assumed that it was a hardware issue. I have swapped out the MB, RAM, power supply, CPU without change. I haven't necessarily seen a correlation between load/temp and this behavior. I just finished running stress command for 10 minutes. Temps didn't get over 60'C (about 50' when not under load), and no issues. Typically even when recording 2 programs and serving a file, the system CPU is still only 10-20%. So what's the next step to pinpointing this issue? 
.

---

### Post by TheFu on 2018-02-12
Debug the kernel crash. Look through the stack trace.  [https://wiki.ubuntu.com/Kernel/KernelDebuggingTricks](https://wiki.ubuntu.com/Kernel/KernelDebuggingTricks)
Using system monitoring, the system and dmesg logs is usually easier.

Good system monitoring will track open files, processes, RAM, and 20 other things. Having this data over a few months will often show patterns.

---

### Post by mma8x on 2018-02-12
Not sure what specifically you're pointing to in the wiki. Dmesg and the system logs don't show a panic. They are normal until the freeze. Is there another tool or method I should be using?

---

### Post by TheFu on 2018-02-13
I'm very sorry. That wasn't the link I meant to post. [https://wiki.ubuntu.com/Kernel/Debugging](https://wiki.ubuntu.com/Kernel/Debugging) is. 

This is pretty advanced stuff. Knowledge of C and debugging C will be helpful.
At the very bottom, there is a "newbies" link, if you need it.  Having another system to act as a console when the problem happens is very helpful when nothing shows up in the normal log files. 

I haven't had to debug the kernel in about 10 yrs.

---

### Post by mma8x on 2018-02-14
My kernel compiling days are well behind me, and even if I got that far I don't know how much it would help. HOWEVER, I did go through the kernel logs for (maybe) the first time, and came upon the below entry. I was watching TV until about 2200 or so (and this morning the system had crashed overnight), so the output from 15:39 doesn't occur every time, but this certainly looks like a clue. Don't know if it means a bad memory module? The last entries don't appear in syslog. Last thing in syslog was a CUPS scheduler message. 

```
Feb 13 15:12:54 mythtv kernel: [ 5556.862698] perf interrupt took too long (2519 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Feb 13 15:39:19 mythtv kernel: [ 7141.852224] Corrupted low memory at ffff880000006000 (6000 phys) = 001ad82e
Feb 13 15:39:19 mythtv kernel: [ 7141.852244] ------------[ cut here ]------------
Feb 13 15:39:19 mythtv kernel: [ 7141.852256] WARNING: CPU: 2 PID: 10822 at /build/linux-HSAA8v/linux-4.4.0/arch/x86/kernel/check.c:141 check_for_bios_corruption.part.1+0xaf/0x100()
Feb 13 15:39:19 mythtv kernel: [ 7141.852258] Memory corruption detected in low memory
Feb 13 15:39:19 mythtv kernel: [ 7141.852261] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_via snd_hda_codec_generic intel_rapl intel_soc_dts_iosf intel_powerclamp coretemp kvm_intel snd_intel_sst_acpi kvm snd_intel_sst_core snd_soc_sst_mfld_platform snd_soc_core snd_hda_intel snd_usb_audio snd_hda_codec uvcvideo snd_hda_core irqbypass snd_compress ac97_bus snd_pcm_dmaengine punit_atom_debug snd_usbmidi_lib videobuf2_vmalloc snd_seq_midi videobuf2_memops videobuf2_v4l2 snd_seq_midi_event snd_hwdep videobuf2_core v4l2_common snd_rawmidi snd_pcm snd_seq videodev media crct10dif_pclmul crc32_pclmul ghash_clmulni_intel joydev snd_seq_device snd_timer cryptd mei_txe snd mei input_leds mac_hid soundcore serio_raw snd_soc_sst_acpi 8250_fintek shpchp lpc_ich intel_smartconnect nfsd auth_rpcgss nfs_acl lockd grace sunrpc parport_pc ppdev lp parport autofs4 hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper syscopyarea r8169 sysfillrect mii sysimgblt ahci fb_sys_fops libahci drm fjes video
Feb 13 15:39:19 mythtv kernel: [ 7141.852356] CPU: 2 PID: 10822 Comm: kworker/2:2 Not tainted 4.4.0-112-generic #135-Ubuntu
Feb 13 15:39:19 mythtv kernel: [ 7141.852359] Hardware name: ECS BAT-I/BAT-I, BIOS 5.6.5 04/22/2014
Feb 13 15:39:19 mythtv kernel: [ 7141.852364] Workqueue: events check_corruption
Feb 13 15:39:19 mythtv kernel: [ 7141.852367]  0000000000000286 a46b229cb3250620 ffff8800a65d7d20 ffffffff813fc233
Feb 13 15:39:19 mythtv kernel: [ 7141.852372]  ffff8800a65d7d68 ffffffff81cb25e0 ffff8800a65d7d58 ffffffff81081f82
Feb 13 15:39:19 mythtv kernel: [ 7141.852377]  0000000000000000 ffff880000010000 ffffffff8210d1f0 0000000000000001
Feb 13 15:39:19 mythtv kernel: [ 7141.852382] Call Trace:
Feb 13 15:39:19 mythtv kernel: [ 7141.852390]  [<ffffffff813fc233>] dump_stack+0x63/0x90
Feb 13 15:39:19 mythtv kernel: [ 7141.852397]  [<ffffffff81081f82>] warn_slowpath_common+0x82/0xc0
Feb 13 15:39:19 mythtv kernel: [ 7141.852401]  [<ffffffff8108201c>] warn_slowpath_fmt+0x5c/0x80
Feb 13 15:39:19 mythtv kernel: [ 7141.852406]  [<ffffffff8106555f>] check_for_bios_corruption.part.1+0xaf/0x100
Feb 13 15:39:19 mythtv kernel: [ 7141.852411]  [<ffffffff810655c8>] check_corruption+0x18/0x50
Feb 13 15:39:19 mythtv kernel: [ 7141.852417]  [<ffffffff8109b815>] process_one_work+0x165/0x480
Feb 13 15:39:19 mythtv kernel: [ 7141.852421]  [<ffffffff8109bb7b>] worker_thread+0x4b/0x4d0
Feb 13 15:39:19 mythtv kernel: [ 7141.852426]  [<ffffffff8109bb30>] ? process_one_work+0x480/0x480
Feb 13 15:39:19 mythtv kernel: [ 7141.852430]  [<ffffffff810a1eb5>] kthread+0xe5/0x100
Feb 13 15:39:19 mythtv kernel: [ 7141.852435]  [<ffffffff810a1dd0>] ? kthread_create_on_node+0x1e0/0x1e0
Feb 13 15:39:19 mythtv kernel: [ 7141.852440]  [<ffffffff81845b9f>] ret_from_fork+0x3f/0x70
Feb 13 15:39:19 mythtv kernel: [ 7141.852445]  [<ffffffff810a1dd0>] ? kthread_create_on_node+0x1e0/0x1e0
Feb 13 15:39:19 mythtv kernel: [ 7141.852448] ---[ end trace 172d682c9c47ec10 ]---
Feb 13 16:53:37 mythtv kernel: [11600.144288] perf interrupt took too long (6046 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
Feb 13 17:58:19 mythtv kernel: [15481.820401] Corrupted low memory at ffff880000006000 (6000 phys) = 001e4c1a
Feb 13 21:53:19 mythtv kernel: [29581.916245] Corrupted low memory at ffff880000006000 (6000 phys) = 00729c55

```

---

### Post by TheFu on 2018-02-14
I don't think you have to compile a kernel.  Just get the core dump file and load it up. The stack trace should be inside from the core.  Main thing is to enable a core file to be created.

I can't tell anything useful from that trace - unless you want to search for "process_one_work" ... which I would start somewhere in the systemd stuff.  But I really haven't any clue, perhaps my hatred of systemd is bleeding through with this assumption?  

And a simple fix for many BIOS issues is to replace the CMOS battery.

---

### Post by mma8x on 2018-02-16
Well, that might have been a red herring. Multiple crashes since, but no error messages. Some googling suggests that the corrupted low memory issue is informational only. So back to square one...

---

### Post by mma8x on 2018-03-06
Ok, so I swapped the hard drive onto another desktop, and everything ran smoothly for a week. On the offending machine, I ran memtest for a long time without errors. Also ran a fedora live image, and ran the Intel Processor Diagnostic Tool, no problems. Then ran stress-ng with a few different parameters for hours. Nothing. Well after it stopped, I tried to scroll through the logs (still on the live image), at which point it froze. This is getting really annoying. I just unplugged everything from the MOBO except for the ethernet cable. We'll see if that does anything. Next step is swap out the motherboard I guess, though I've already swapped motherboard and CPU. So WTF.

---

### Post by TheFu on 2018-03-06
Sounds like you've done more than I would have. Only have this advice - simplify and test. Keep doing that until the crashes stop. 

I assume you've already rebuilt the system to avoid any bad configs getting pulled forward from older versions of the different tools causing conflicts.

Just throwing out a few more ideas below ... 

Once had a failing GPU cause lockups, but no other issues. $20 replacement and that system has been running trouble free the last 7 yrs.  The only other problem with lockups was directly connected to running virtualbox on it. That was fairly clear.  Switched to KVM and it has been happy the last 7 yrs.

There are some types of systems that have been trouble. Doubt you have one, but there's an Atom-based system that has issues when the network load gets high. That type of system is usually deployed for routers.  Ryzen systems where problems last year, but I think that has all been sorted.

Sorry, really don't have many good ideas left.

---

### Post by mma8x on 2018-03-08
Well, last idea didn't work either. Just reviewing the hardware system, and I was getting this build confused with another. This was an embedded celeron/mobo combo. I did have that whole combo replaced, and did swap out the power supply, but I can't find that I bought another stick of RAM. I thought that I had some good g skil stuff in there, but apparently I have some hynix ebay special (really thought that I swapped it out though). I just bought a new mobo/cpu to try out, but I'd bet that the RAM is the issue at this point, despite not showing up as an error in memtest. Luckily it's a cheap build. 

"I assume you've already rebuilt the system to avoid any bad configs getting pulled forward from older versions of the different tools causing conflicts."

Not sure what you mean by this, unless you mean fresh OS installs (yes).

---

### Post by TheFu on 2018-03-08
> 
"I assume you've already rebuilt the system to avoid any bad configs getting pulled forward from older versions of the different tools causing conflicts."
> **mma8x said:**
> 
Not sure what you mean by this, unless you mean fresh OS installs (yes).

Yes. That is what I meant.  

I don't remember if you'd swapped the physical disk or cables?  Since you've changed everything else, that was probably something done last month. There should be errors in the logs if the disk reads were being corrupted.

---

### Post by mma8x on 2018-03-08
I swapped the disk into a working system without problems. And the problem system froze while running a live usb distro as well (with the HDD disconnected)

---

### Post by mma8x on 2018-04-06
Just an update, I swapped out the MB/CPU combo with a new one, and it's been stable ever since. I also swapped my pico PSU for a traditional one (the new MB needed an add'l 4 pin power connector that the pico didn't have), so it's possible that it was the PSU, though at some point in the distant past I had used the traditional PSU with the old board and still had issues. Strange thing is I had already tried a new MB/CPU early on, and had the same problems.

---

