---
title: "Complete freeze"
date: 2017-05-12
forum: General Help
---

### Post by Brandon_MacEachern on 2017-05-12
I can't get you much more than what I have here, as this happens only on 17.04 on all of my machines of different brands, models, even CPU core types, etc..  It just happens, only common thing here is it's 17.04 Ubuntu 64-bit (and I tried Ubuntu Gnome and Xubuntu--same issue).  Every once in a while, it seems like all operations on the computer just lock up, I can't write to disk, read from it, or load programs, etc.  I can't do anything.  About the only thing that works is whatever happens to already be in RAM.

Therefore, I can't even get logs because they don't get written to disk.  This happens on a Xeon desktop or an i7 laptop, doesn't even matter if it's booted UEFI or Legacy, I get the same odd freeze.  If I run a fresh install, I eventually run into it within a week if the machines stay up long enough.

All I can give you here is a picture of the log viewer, which I left running to show whatever comes up: [http://i.imgur.com/Y19M2JA.jpg](http://i.imgur.com/Y19M2JA.jpg)

That's all I could give you before the log viewer eventually froze, requiring me to hold down power to even restart the machine.  TTY screens are also stuck, asks for username, I enter it, then asks for password, i enter that, the freezes up hard, then complains about timing out, returning me back to the username box.

I'm honestly not sure what could be doing this, because at least two of these machines, have no hardware even similar..  One is a Xeon Harpertown, other is an i7 Haswell.  One has 32GB RAM Kingston, other has 8GB Crucial.  WD vs Sandisk, AMD vs Intel/Nvidia, etc, it goes on.  About the only thing similar between the two is that they run on electricity, lol.

Any ideas, has anyone even seen a log file like this?

EDIT:  For anyone asking what I was doing, it doesn't even matter.  One machine could simply be running Gimp, the other could just be in Thunar, doesn't seem to matter what you are doing, it just does it after a week of use.  Sometimes even within an hour of booting (but that's rare that that happens).

---

### Post by exhile on 2017-05-12
All Linux flavours on a variety of hardware configurations freeze or lockup at some point. Welcome to the freeze club as I've dealt with it at least 5 times a week. All you can do is do a hard reset and continue from there.

---

### Post by Brandon_MacEachern on 2017-05-12
And somehow that's considered acceptable?  This started with 17.04.  From 14.04 to 17.04 on these machines, they never had any of these freezes.

---

### Post by exhile on 2017-05-12
If 14.04.5 never froze then perhaps staying on that edition of Ubuntu is best. 17.04 is not an LTS. Maybe give 16.04.2 a try? I've looked up "freeze" in this forum and it's quite common.

---

### Post by Bashing-om on 2017-05-12
Brandon_MacEachern; Hello;

No:
> 
All you can do is do a hard reset and continue from there.

Not the ubuntu way . We find the cause and get it onto the hands of those who fix it.

Now I too suffered the system crashes :
Installed a SSD in this old box and did the utmost things to support it . Once ubuntu was installed onto the SSD my issues began.
After more than a month of fighting and no solution - because of nothing else to try I  installed a proprietary graphics's driver.

Not even a hick up since - solid as a rock in all respects !
In your case - kernel not happy with cpu0 - Just hard to say !

Not saying it is a graphic's driver issue in your case, as the crashes happen on a variety of hardwares - but certainly worth a try and see

[INDENT][INDENT]what might be the result
[/INDENT][/INDENT]

---

### Post by Brandon_MacEachern on 2017-05-12
Well on the desktop, it has no other option as it's a Radeon 7850, only whatever open source driver it gives me..

The desktop isn't even using a SATA hard drive, it's using a traditional old fashion mechanical 2TB magnetic hard drive, laptop is SSD, but since both have the same issue, it's odd.

I can't use Ubuntu 14.04 as the games I want to use require the video drivers offered in at least LTS 16.04, but that particular one locks up the video card on the desktop (only when playing Team Fortress 2--which was fixed in 17.04, but brought on another problem).

Even then, if I was to go back to a few year old 14.04 release, I lose the ability to run some newer software as it requires a newer kernel, etc.  It's a complete and utter mess and catch 22.

Bashing-om, it's hard to see, but it's showing errors on all cores of the CPU from 0 to 7, same with desktop.  They aren't even running the same Intel power management utility either as I was thinking maybe it was intel pstate, but nope, desktop isn't using it as it's an older Xeon from 2008.

I'm just at a loss.

I'm willing to figure this out and have patience for it, but yall will have to be patient as it can take as long as a week to a couple weeks for it to come back.  Usually within a week though, as my laptop is left on.  My Xeon is shut down every night however due to power bill concerns---not to mention it's a hotter space heater than my space heater itself.

---

### Post by Bashing-om on 2017-05-12
Brandon_MacEachern; Hey ...

Well, was a thought ..

All I can suggest at this point is in separate terminals run
top
journalctl -f

see if you can spot the causation of the fault(s) - what "might" be taking place when the crash occurs .
Mind you, in my case top and watching the logs did no good ; YMMV. When my system crashed could not even ping the machine on the local LAN , DEAD  and absolutely nothing able to log anywhere . Nada, zip - no help .

Is the boot clean ?
anything suspicious in the boot log ( systemd )?
```

journalctl -b -0

```


[INDENT]a long hard road to find something
[INDENT][INDENT][INDENT]we can not see
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Brandon_MacEachern on 2017-05-12
Wooaaah Nelly!!  (Said in the Earthworm Jim voice).  Running "[COLOR=#000000][FONT=&quot]journalctl -b -0" spat out literally a million lines of logs.  In no way can any human process this.  Had to hold down the spacebar for a while for it to get to the end, and by that point, the terminals back buffer had already long lost the beginning.[/FONT][/COLOR]

---

### Post by Brandon_MacEachern on 2017-05-12
You know, thinking back, I "might" have found a common denominator, but it makes no sense.  An hour before each time, I have unplugged an SD card, but they were properly unmounted and ejected each time.

But, it might have been one specific SD card.  I'll try formatting it..  The readers used were both entirely different, my laptops is based off the PCI-express bus, and my desktops were using an old USB one..  But I think it could be the card perhaps not unmounting cleanly (though odd it crashes and burns so hard, and not all the time when this card has been used).

I'll have to figure this out and have that terminal command ready to run.

---

### Post by Bashing-om on 2017-05-12
Brandon_MacEachern; Huh ...

> **Brandon_MacEachern said:**
> Wooaaah Nelly!!  (Said in the Earthworm Jim voice).  Running "[COLOR=#000000][FONT=&quot]journalctl -b -0" spat out literally a million lines of logs.  In no way can any human process this.  Had to hold down the spacebar for a while for it to get to the end, and by that point, the terminals back buffer had already long lost the beginning.[/FONT][/COLOR]

As journalctl pages to more ; gives the output one page at a time - page up and page down keys to control that output .
- q - to quit .

And yeah . I can accept " it might have been one specific SD card " as a likely prospect for the fault . nvme ?


[INDENT][INDENT]could be this
[/INDENT][/INDENT]

---

### Post by Brandon_MacEachern on 2017-05-12
(Obviously not really a million, but long enough to still be unreadable with anyone with children to look after at the same time)[URL="https://paste.ubuntu.com/24564555/"]

https://paste.ubuntu.com/24564555/[/URL]

---

### Post by Bashing-om on 2017-05-12
> 
May 12 19:49:19 BrandonsLaptop kernel: ahci 0000:00:1f.2: version 3.0
May 12 19:49:19 BrandonsLaptop kernel: mmc0: Unknown controller version (3). You may experience problems.

as I continue to read .

edit:
> 
May 12 19:49:19 BrandonsLaptop kernel: nvidia: module verification failed: signature and/or required key missi

secure boot disabled when installing the proprietary driver ???

edit 2:
> 
May 12 19:49:20 BrandonsLaptop systemd[1]: Created slice system-systemd\x2dbacklight.slice.
May 12 19:49:20 BrandonsLaptop systemd[1]: Starting Load/Save Screen Backlight Brightness of backlight:intel_b
May 12 19:49:20 BrandonsLaptop systemd[1]: Started Load/Save Screen Backlight Brightness of backlight:intel_ba
May 12 19:49:20 BrandonsLaptop kernel: ACPI Warning: SystemIO range 0x0000000000001828-0x000000000000182F conf
May 12 19:49:20 BrandonsLaptop kernel: ACPI: If an ACPI driver is available for this device, you should use it
May 12 19:49:20 BrandonsLaptop kernel: ACPI Warning: SystemIO range 0x0000000000000840-0x000000000000084F conf
May 12 19:49:20 BrandonsLaptop kernel: ACPI: If an ACPI driver is available for this device, you should use it
May 12 19:49:20 BrandonsLaptop kernel: ACPI Warning: SystemIO range 0x0000000000000830-0x000000000000083F conf
May 12 19:49:20 BrandonsLaptop kernel: ACPI: If an ACPI driver is available for this device, you should use it
May 12 19:49:20 BrandonsLaptop kernel: ACPI Warning: SystemIO range 0x0000000000000800-0x000000000000082F conf
May 12 19:49:20 BrandonsLaptop kernel: ACPI: If an ACPI driver is available for this device, you should use it
May 12 19:49:20 BrandonsLaptop kernel: lpc_ich: Resource conflict(s) found affecting gpio_ich

will need a closer look

edit: 3 - Ouch !!
> 

May 12 19:49:20 BrandonsLaptop systemd-fsck[824]: fsck.fat 4.0 (2016-05-06)
May 12 19:49:20 BrandonsLaptop systemd-fsck[824]: 0x41: Dirty bit is set. Fs was not properly unmounted and so


edit: 4 this can not be good !
> 
May 12 19:49:22 BrandonsLaptop systemd[1]: Failed to start NVIDIA Persistence Daemon.
May 12 19:49:22 BrandonsLaptop systemd[1]: nvidia-persistenced.service: Unit entered failed state.


edit: 5 This I do not know about . we in a learning mode ?
> 
May 12 19:49:22 BrandonsLaptop smartd[1061]: Device: /dev/sda [SAT], can't monitor Current_Pending_Sector coun
May 12 19:49:22 BrandonsLaptop smartd[1061]: Device: /dev/sda [SAT], can't monitor Offline_Uncorrectable count


edit: 6 - Un-GooD ?? what gives here ??
> 
May 12 19:49:23 BrandonsLaptop kernel: nvidia-uvm: Unloaded the UVM driver in 8 mode
May 12 19:49:23 BrandonsLaptop kernel: [drm] [nvidia-drm] [GPU ID 0x00000100] Unloading driver
May 12 19:49:23 BrandonsLaptop kernel: nvidia-modeset: Unloading
May 12 19:49:23 BrandonsLaptop kernel: nvidia-nvlink: Unregistered the Nvlink Core, major device number 244
May 12 19:49:23 BrandonsLaptop kernel: bbswitch: disabling discrete graphics
May 12 19:49:23 BrandonsLaptop kernel: ACPI Warning: \_SB.PCI0.PEG.VID._DSM: Argument #4 type mismatch - Found
May 12 19:49:23 BrandonsLaptop systemd[1]: Started Detect the available GPUs and deal with any system changes.



patience

---

### Post by Brandon_MacEachern on 2017-05-12
Secure boot is and still is disabled, and always has been, and the nvidia prime drive was installed with secure boot disabled also.  I would never install such an evil microsoft thing.

That mmc0 error has always been there..  Even Windows needs a quirky driver to even see it, Ubuntu sees it out of the box, but the desktop has a standard USB SD reader with no such messages on boot, and has the same freeze.

No one has been able to fix that mmc0 error, I tried a launchpad report years and years ago, as a MacBook Pro 2011 I had also had the same error (and same controller too)---no freezes then either.  I can tell you exactly what controller it is, grab the standard HD this laptop came with from Lenovo, can go into Device Manager and find out who actually makes it.

---

### Post by Brandon_MacEachern on 2017-05-12
For edit 3, that was because I had just rebooted from the freeze, as I explained, you can't shut down when this happens, you have zero choice but to force the power off of the machine.

As for all the other edits...

For edit 6, that's because the Nvidia isn't selected, the Intel is..  This is normal as the Nvidia is suspended until I enable it, to save battery.
For edit 5, no SMART errors reported, seems to be normal.  Besides, this freeze happens on a live boot disk too with the internal disk unmounted, so that can't be the cause, if it was, something isn't doing what it's being told to do.
For edit 4, refer to edit 6 post above.

As for edit 2, can't control what's out of my hands.  There is a UEFI update available, but Lenovo doesn't make it easy for Linux users.  I have to strip the boot utility from the exe, use dd to write it to a USB disk, and hope it boots (sometimes it won't, and I have to swap in the original HD for the computer with it's original Windows 8 install).  I can do it, but none of the changes seem to infer anything regarding IO mapping, and since this freeze happens on an entirely different system consisting of entirely different chipsets, CPU, firmware, etc, it seems very unlikely it's actually the cause, and something else is happening, since nothing under 17.04 did this, and neither does BSD or Windows.  Just strictly 17.04, can't imagine 17.04 hitting the magic byte.

---

### Post by gordintoronto on 2017-05-13
> **Brandon_MacEachern said:**
> I'm willing to figure this out and have patience for it, but yall will have to be patient as it can take as long as a week to a couple weeks for it to come back.  Usually within a week though, as my laptop is left on.  My Xeon is shut down every night however due to power bill concerns---not to mention it's a hotter space heater than my space heater itself.

The main feature of Xeon CPUs is that they run cooler than others. It might be time to clean all the fans, maybe replace the CPU paste. Do you smoke? Have cats? Have you tried lm-sensors?

My main system would freeze from time to time, but I fixed that by putting an ACPI parameter in Grub. These days, I reboot to begin using a new kernel, and my system has not locked up since I made the change in Grub,  many months ago. I have an old netbook, and elderly laptops from HP and Lenovo, and they have never locked up. (This might be strange: I use the netbook as a file server, and its uptime is usually measured in months.)

---

### Post by Hagar Delest on 2017-05-14
Hi,

I've experienced such freeze also on my xubuntu 17.04 machine. It never happened before. I was using the beta version of Firefox, I switched to the standard version and it seems to have stopped.
Here is an extract of my kern.log where I think I suffered such a freeze, if it can help. If there are other information that could be provided to help, just ask.
Note that the freeze was progressive : the first symptom was a non responsive click, I could still switch from one application to another, then even if the mouse was still moving, it had no effect anymore. Once, I opened a Firefox tab with sound and it repeated the beginning of the sound again and again.
```
May  9 20:32:47 HP-G72 kernel: [   29.115260] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
May  9 20:34:21 HP-G72 kernel: [  122.781865] ERROR @wl_notify_scan_status : 
May  9 20:34:21 HP-G72 kernel: [  122.781869] wlp3s0 Scan_results error (-22)
May  9 20:38:52 HP-G72 kernel: [  394.157390] perf: interrupt took too long (2520 > 2500), lowering kernel.perf_event_max_sample_rate to 79250
May  9 20:41:43 HP-G72 kernel: [  564.792267] perf: interrupt took too long (3153 > 3150), lowering kernel.perf_event_max_sample_rate to 63250
May  9 20:46:59 HP-G72 kernel: [  880.429851] perf: interrupt took too long (3945 > 3941), lowering kernel.perf_event_max_sample_rate to 50500
May  9 20:59:55 HP-G72 kernel: [ 1657.048718] perf: interrupt took too long (4940 > 4931), lowering kernel.perf_event_max_sample_rate to 40250
May  9 21:57:32 HP-G72 kernel: [ 5114.495609] ------------[ cut here ]------------
May  9 21:57:32 HP-G72 kernel: [ 5114.495651] kernel BUG at /build/linux-2NWldV/linux-4.10.0/include/linux/swapops.h:129!
May  9 21:57:32 HP-G72 kernel: [ 5114.495693] invalid opcode: 0000 [#1] SMP
May  9 21:57:32 HP-G72 kernel: [ 5114.495715] Modules linked in: nls_iso8859_1 hp_wmi sparse_keymap snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi wl(POE) snd_seq_midi_event snd_rawmidi snd_seq intel_powerclamp uvcvideo coretemp videobuf2_vmalloc intel_cstate videobuf2_memops videobuf2_v4l2 snd_seq_device videobuf2_core snd_timer videodev joydev input_leds media snd cfg80211 serio_raw lpc_ich shpchp soundcore mei_me mei mac_hid parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid i915 psmouse i2c_algo_bit ahci drm_kms_helper libahci syscopyarea sysfillrect r8169 sysimgblt fb_sys_fops drm mii wmi fjes video
May  9 21:57:32 HP-G72 kernel: [ 5114.496014] CPU: 1 PID: 1630 Comm: firefox Tainted: P           OE   4.10.0-20-generic #22-Ubuntu
May  9 21:57:32 HP-G72 kernel: [ 5114.496057] Hardware name: Hewlett-Packard HP G72 Notebook PC              /1439, BIOS F.32                  08/02/2010
May  9 21:57:32 HP-G72 kernel: [ 5114.496109] task: ffff973c3b509540 task.stack: ffffa5e681aa4000
May  9 21:57:32 HP-G72 kernel: [ 5114.496145] RIP: 0010:__migration_entry_wait+0x16a/0x180
May  9 21:57:32 HP-G72 kernel: [ 5114.496173] RSP: 0000:ffffa5e681aa7d68 EFLAGS: 00010246
May  9 21:57:32 HP-G72 kernel: [ 5114.496200] RAX: 000fffffc0048078 RBX: ffffdd6401f52270 RCX: ffffdd6401f52270
May  9 21:57:32 HP-G72 kernel: [ 5114.496235] RDX: 0000000000000001 RSI: ffff973c3d489008 RDI: ffffdd6400228040
May  9 21:57:32 HP-G72 kernel: [ 5114.496270] RBP: ffffa5e681aa7d80 R08: ffff973cd6140f80 R09: ffff973cd6140f80
May  9 21:57:32 HP-G72 kernel: [ 5114.496304] R10: 0000000000000da0 R11: 0000000000002004 R12: ffffdd6400228040
May  9 21:57:32 HP-G72 kernel: [ 5114.496340] R13: 3e00000000008a01 R14: ffffa5e681aa7e30 R15: ffff973c56ab74b0
May  9 21:57:32 HP-G72 kernel: [ 5114.496375] FS:  00007fc634a24b80(0000) GS:ffff973cdbc40000(0000) knlGS:0000000000000000
May  9 21:57:32 HP-G72 kernel: [ 5114.496414] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May  9 21:57:32 HP-G72 kernel: [ 5114.496444] CR2: 00007fc5d7801800 CR3: 000000007b5df000 CR4: 00000000000006e0
May  9 21:57:32 HP-G72 kernel: [ 5114.496479] Call Trace:
May  9 21:57:32 HP-G72 kernel: [ 5114.496497]  migration_entry_wait+0x74/0x80
May  9 21:57:32 HP-G72 kernel: [ 5114.496523]  do_swap_page+0x5b3/0x770
May  9 21:57:32 HP-G72 kernel: [ 5114.496545]  handle_mm_fault+0x873/0x1360
May  9 21:57:32 HP-G72 kernel: [ 5114.496570]  __do_page_fault+0x23e/0x4e0
May  9 21:57:32 HP-G72 kernel: [ 5114.496593]  do_page_fault+0x22/0x30
May  9 21:57:32 HP-G72 kernel: [ 5114.496618]  page_fault+0x28/0x30
May  9 21:57:32 HP-G72 kernel: [ 5114.496637] RIP: 0033:0x415dbf
May  9 21:57:32 HP-G72 kernel: [ 5114.496656] RSP: 002b:00007ffe936f8210 EFLAGS: 00010202
May  9 21:57:32 HP-G72 kernel: [ 5114.496683] RAX: 00000000000017d0 RBX: 00007fc5d78fe820 RCX: 0000000000000003
May  9 21:57:32 HP-G72 kernel: [ 5114.496718] RDX: 00007fc5d78017f0 RSI: 00007fc5d7800000 RDI: 0000000000000003
May  9 21:57:32 HP-G72 kernel: [ 5114.496753] RBP: 00000000000000fe R08: 00007fc633400048 R09: 0000000000002000
May  9 21:57:32 HP-G72 kernel: [ 5114.496788] R10: 0000000000000da0 R11: 0000000000002004 R12: 00007fc5e71a1de0
May  9 21:57:32 HP-G72 kernel: [ 5114.496822] R13: 00007fc633400040 R14: 00007fc5d78fe820 R15: 00007fc633400048
May  9 21:57:32 HP-G72 kernel: [ 5114.496857] Code: ff ff ff 4c 89 e7 e8 96 a2 f8 ff e9 3c ff ff ff 85 d2 0f 84 2a ff ff ff 8d 4a 01 89 d0 f0 41 0f b1 4d 00 39 d0 74 81 89 c2 eb e5 <0f> 0b 4c 89 e7 e8 0c fb f9 ff eb b8 4c 8d 60 ff 4c 8d 68 1b eb 
May  9 21:57:32 HP-G72 kernel: [ 5114.496968] RIP: __migration_entry_wait+0x16a/0x180 RSP: ffffa5e681aa7d68
May  9 21:57:32 HP-G72 kernel: [ 5114.505089] ---[ end trace 1c75aa028c8c3507 ]---
May  9 22:02:39 HP-G72 kernel: [    0.000000] Linux version 4.10.0-20-generic (buildd@lcy01-05) (gcc version 6.3.0 20170406 (Ubuntu 6.3.0-12ubuntu2) ) #22-Ubuntu SMP Thu Apr 20 09:22:42 UTC 2017 (Ubuntu 4.10.0-20.22-generic 4.10.8)

```
The last line is when the system reboots.

---

