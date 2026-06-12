---
title: "Kernel crash, sound stopped working"
date: 2006-11-12
forum: General Help
---

### Post by michalg on 2006-11-12
i got a dell dimension 9200 a few weeks ago with onboard audio. ubuntu edgy worked great on this, until last night. (i used edgy because i got the system a week before edgy eft was announced, and wanted to get things going quickly, and the 6.06 disc didn't recognize my gigabit ethernet controller.)

anyway, my system crashed yesterday evening. the keyboard was unresponsive, ssh was not responding but ping was, so i cycled the power and the system came back up. /var/log/kern.log for this event reads:

```

Nov 11 01:18:27 moo kernel: [17809551.116000] Trying to vfree() nonexistent vm area (f8dba000)
Nov 11 01:18:27 moo kernel: [17809551.116000] BUG: warning at mm/vmalloc.c:316/__vunmap()
Nov 11 01:18:27 moo kernel: [17809551.116000]  <f8a25c20> snd_pcm_plugin_free+0x20/0x30 [snd_pcm_oss]  <f8a22048> snd_pcm_oss_plugin_clear+0x18/0x40 [snd_pcm_oss]
Nov 11 01:18:27 moo kernel: [17809551.116000]  <f8a22845> snd_pcm_oss_change_params+0x455/0xc80 [snd_pcm_oss]  <f8a22577> snd_pcm_oss_change_params+0x187/0xc80 [snd_pcm_oss]
Nov 11 01:18:27 moo kernel: [17809551.116000]  <f8a230c9> snd_pcm_oss_make_ready+0x59/0x70 [snd_pcm_oss]  <f8a24679> snd_pcm_oss_ioctl+0x269/0xa60 [snd_pcm_oss]
Nov 11 01:18:27 moo kernel: [17809551.116000]  <f8a24410> snd_pcm_oss_ioctl+0x0/0xa60 [snd_pcm_oss]  <c017d64b> do_ioctl+0x2b/0x90
Nov 11 01:18:27 moo kernel: [17809551.116000]  <c017d70c> vfs_ioctl+0x5c/0x2b0  <c010e98a> get_offset_hpet+0xa/0x30
Nov 11 01:18:27 moo kernel: [17809551.116000]  <c017d9d2> sys_ioctl+0x72/0x90  <c0102fbb> sysenter_past_esp+0x54/0x79
Nov 11 01:18:27 moo kernel: [17809551.116000] Trying to vfree() nonexistent vm area (f8e61000)
Nov 11 01:18:27 moo kernel: [17809551.116000] BUG: warning at mm/vmalloc.c:316/__vunmap()
Nov 11 01:18:27 moo kernel: [17809551.116000]  <f8a25c20> snd_pcm_plugin_free+0x20/0x30 [snd_pcm_oss]  <f8a22048> snd_pcm_oss_plugin_clear+0x18/0x40 [snd_pcm_oss]
Nov 11 01:18:27 moo kernel: [17809551.116000]  <f8a22845> snd_pcm_oss_change_params+0x455/0xc80 [snd_pcm_oss]  <f8a22577> snd_pcm_oss_change_params+0x187/0xc80 [snd_pcm_oss]
Nov 11 01:18:27 moo kernel: [17809551.116000]  <f8a230c9> snd_pcm_oss_make_ready+0x59/0x70 [snd_pcm_oss]  <f8a24679> snd_pcm_oss_ioctl+0x269/0xa60 [snd_pcm_oss]
Nov 11 01:18:27 moo kernel: [17809551.116000]  <f8a24410> snd_pcm_oss_ioctl+0x0/0xa60 [snd_pcm_oss]  <c017d64b> do_ioctl+0x2b/0x90
Nov 11 01:18:27 moo kernel: [17809551.116000]  <c017d70c> vfs_ioctl+0x5c/0x2b0  <c010e98a> get_offset_hpet+0xa/0x30
Nov 11 01:18:27 moo kernel: [17809551.116000]  <c017d9d2> sys_ioctl+0x72/0x90  <c0102fbb> sysenter_past_esp+0x54/0x79

```

now the system will not make any sound. (to be clear, it did prior to this crash.)

"aplay -l" reports "no soundcards found...". i've followed the instructions at [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide) and see that no snd_* modules are loaded after bootup. lspci -vvv reports this audio item:

```

00:1b.0 Audio device: Intel Corporation HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01db
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)

```

from this output i suspect the driver should be "hda-intel". i followed the instructions under "Getting the ALSA drivers from a *fresh* kernel" and reached a failure in step 4. i then followed the "Using alsa-source" instructions, succeeded, and continued at step 4 of the "General Help" (modprobe snd-[NAME OF YOUR SOUND CARD'S DRIVER]) which fails:

```

WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.17-10-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

the only files in this path are:

```

/lib/modules/2.6.17-10-generic/kernel/sound/core/
/lib/modules/2.6.17-10-generic/kernel/sound/core/oss
/lib/modules/2.6.17-10-generic/kernel/sound/core/seq
/lib/modules/2.6.17-10-generic/kernel/sound/core/seq/instr
/lib/modules/2.6.17-10-generic/kernel/sound/core/seq/oss

```

so of course they arn't being found. the dmesg output now includes these lines:

```

[17180992.420000] snd_hda_codec: Unknown symbol snd_ctl_add
[17180992.420000] snd_hda_codec: Unknown symbol snd_card_proc_new
[17180992.420000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[17180992.420000] snd_hda_codec: Unknown symbol snd_verbose_printk
[17180992.420000] snd_hda_codec: Unknown symbol snd_ctl_new1
[17180992.420000] snd_hda_codec: Unknown symbol snd_component_add
[17180992.420000] snd_hda_codec: Unknown symbol snd_iprintf
[17180992.420000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[17180992.420000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[17180992.420000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[17180992.420000] snd_hda_codec: Unknown symbol snd_device_new
[17180992.420000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[17180992.420000] snd_hda_codec: Unknown symbol snd_pcm_format_width
[17180992.420000] snd_hda_intel: Unknown symbol snd_pcm_new
[17180992.420000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[17180992.420000] snd_hda_intel: Unknown symbol snd_card_register
[17180992.420000] snd_hda_intel: Unknown symbol snd_card_free
[17180992.420000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[17180992.420000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[17180992.420000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[17180992.420000] snd_hda_intel: Unknown symbol snd_verbose_printk
[17180992.420000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[17180992.420000] snd_hda_intel: Unknown symbol snd_dma_free_pages
[17180992.420000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[17180992.420000] snd_hda_intel: Unknown symbol snd_card_new
[17180992.420000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[17180992.420000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[17180992.420000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[17180992.420000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[17180992.420000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[17180992.420000] snd_hda_intel: Unknown symbol snd_hda_suspend
[17180992.420000] snd_hda_intel: Unknown symbol snd_device_new
[17180992.420000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[17180992.420000] snd_hda_intel: Unknown symbol snd_hda_resume
[17180992.420000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[17180992.420000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[17180992.420000] snd_hda_intel: Unknown symbol snd_dma_alloc_pages
[17180992.420000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed

```

i got tired of this, and burned a 6.10 "Edgy Eft" disc (the final version of what i had been running), popped it in, and booted into the live cd. this live-cd also does not recognize my sound card (aplay -l reports no soundcards).

so now i'm lost and confused. is my integrated audio board broken?

-Michal

---

### Post by .t. on 2006-11-12
No. Why don't you try reinstalling the kernel? "sudo aptitude purge linux-image-`uname -r` && sudo aptitude install linux-image-`uname -r` linux-restricted-modules-`uname -r`" kind of thing...

---

### Post by michalg on 2006-11-12
> **.t. said:**
> No. Why don't you try reinstalling the kernel? "sudo aptitude purge linux-image-`uname -r` && sudo aptitude install linux-image-`uname -r` linux-restricted-modules-`uname -r`" kind of thing...

Okay, I ran these commands. I was asked two times if I wanted to accept  proposed dependency solutions, which I did. The first was to upgrade the kernel from ".22 (now)" to ".33 (edgy)", but "uname -r" still reports what it did in the past (" 2.6.17-10-generic") so i don't know if it worked or not. (didn't get any errors or warnings, though.) The second was with updating glx to match the current kernel, from whatever version i have/had to one from edgy-security or something like that. Anyway, I rebooted afterwards.

Then I tried to add the snd-hda-intel module but got:

> 
root@moo:~# modprobe -v snd-hda-intel
insmod /lib/modules/2.6.17-10-generic/kernel/sound/core/snd-timer.ko 
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-10-generic/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
install /sbin/modprobe --ignore-install snd-pcm  && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
insmod /lib/modules/2.6.17-10-generic/kernel/sound/core/snd-timer.ko 
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-10-generic/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
insmod /lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-pcm.ko 
FATAL: Error inserting snd_pcm (/lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
insmod /lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-codec.ko 
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
insmod /lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko 
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


so i recompiled alsa from source as per instructions in aforementioned document which did:

> 
cp snd-page-alloc.ko snd-pcm.ko snd-rtctimer.ko snd-timer.ko snd.ko 
cp snd-mixer-oss.ko snd-pcm-oss.ko 
cp snd-seq-device.ko snd-seq-midi-event.ko snd-seq.ko 
cp snd-seq-oss.ko /lib/modules/2.6.17-10-generic/kernel/sound/acore/seq/oss
cp snd-hda-codec.ko snd-hda-intel.ko /lib/modules/2.6.17-10-generic/kernel/sound/pci/hda


now i tried:

> 
root@moo:~# modprobe -v snd-hda-intel
insmod /lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-timer.ko 
install /sbin/modprobe --ignore-install snd-pcm  && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
insmod /lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-pcm.ko 
insmod /lib/modules/2.6.17-10-generic/kernel/sound/acore/oss/snd-mixer-oss.ko 
insmod /lib/modules/2.6.17-10-generic/kernel/sound/acore/oss/snd-pcm-oss.ko 
insmod /lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-codec.ko 
insmod /lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko 


and lsmod|grep snd shows:

> 
root@moo:~# lsmod | grep snd
snd_hda_intel          20500  0 
snd_hda_codec         169088  1 snd_hda_intel
snd_pcm_oss            47232  0 
snd_mixer_oss          19712  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              24964  1 snd_pcm
snd                    60036  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm


but

> 
root@moo:~# tail /var/log/kern.log |grep ALSA
Nov 12 14:35:43 moo kernel: [17182135.764000] ALSA /moo/mikeg/tmp/sound-problem/src/alsa/alsa-driver-1.0.12/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1554: hda-intel: no codecs found!


and

> 
mikeg@moo:~ >aplay -l
aplay: device_list:222: no soundcards found...


so... i'm thinking about just reinstalling the system to be edgy eft from scratch and seeing what happens. i've been meaning to do this anyways, and my partition scheme will guarantee the safety of important data anyways. it's just odd that the edgy live cd doesn't load the necessary audio drivers either.

---

### Post by .t. on 2006-11-12
I don't have enough experience with this, so it may be your only choice. However, you shouldn't have to and someone more knowlegeable would surely be able to fix it without resorting to that. Try reinstalling the kernel again ("sudo aptitude reinstall linux-image-`uname -r`"), first, though. And then reboot.

---

### Post by michalg on 2006-11-12
> **.t. said:**
> I don't have enough experience with this, so it may be your only choice. However, you shouldn't have to and someone more knowlegeable would surely be able to fix it without resorting to that. Try reinstalling the kernel again ("sudo aptitude reinstall linux-image-`uname -r`"), first, though. And then reboot.

You've been helpful so far, i very much appreciate it.

I agree a reinstall is a drastic thing, but it is conveniently something i've been meaning to do anyways. In some Ubuntu troubleshooting guides there are suggestions to test things in Windows! I think that's kinda weird too, but I'm not willing to go thaaaat far.

I'll try redoing the kernel a bit more and report back here what I find. Most likely though I'll just install edgy 'cuz I've been wanting to do that since the beginning anyway.

thanks again for your help!

---

### Post by michalg on 2006-11-12
> **michalg said:**
> You've been helpful so far, i very much appreciate it.

I agree a reinstall is a drastic thing, but it is conveniently something i've been meaning to do anyways. In some Ubuntu troubleshooting guides there are suggestions to test things in Windows! I think that's kinda weird too, but I'm not willing to go thaaaat far.

I'll try redoing the kernel a bit more and report back here what I find. Most likely though I'll just install edgy 'cuz I've been wanting to do that since the beginning anyway.

thanks again for your help!


installing edgy eft from scratch does not resolve my problem. :-k 

will follow the comprehensive guide... again. ](*,)

---

### Post by michalg on 2006-11-13
> **michalg said:**
> installing edgy eft from scratch does not resolve my problem. :-k 

will follow the comprehensive guide... again. ](*,)

i'm continuing this discussion here:

[http://ubuntuforums.org/showthread.php?p=1750804#post1750804](http://ubuntuforums.org/showthread.php?p=1750804#post1750804)

---

