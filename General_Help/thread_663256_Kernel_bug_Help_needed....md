---
title: "Kernel bug? Help needed..."
date: 2008-01-09
forum: General Help
---

### Post by jesushero on 2008-01-09
Someone has posted this [http://ubuntuforums.org/showthread.php?t=332693](http://ubuntuforums.org/showthread.php?t=332693)

My problem is different. I have been running Gutsy with various different problems. Last one was:

```
kernel: BUG: unable to handle kernel paging request at a0130d9a

```
I had the exact logs but as I was about to copy paste them in here X restarted (one of my other problems nobody could help me with)

That was on the syslog.

The Messages log has this around the same time:

```
Jan 10 03:01:20 Levendis kernel: [78862.364281] a0130d9a
Jan 10 03:01:20 Levendis kernel: [78862.364299] Modules linked in: isofs udf snd_rtctimer ppdev speedstep_lib cpufreq_stats cpufreq_conservative ipv6 cpufreq_powersave cpufreq_userspace cpufreq_ondemand freq_table button ac sbs dock container video battery lp loop snd_mpu401 snd_mpu401_uart snd_seq_dummy snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul arc4 snd_seq_oss ecb blkcipher snd_emu10k1 snd_seq_midi rc80211_simple snd_rawmidi snd_ac97_codec snd_seq_midi_event ac97_bus nvidia(P) snd_pcm_oss snd_mixer_oss snd_seq rt61pci rt2x00pci rt2x00lib rfkill snd_pcm mac80211 i2c_core cfg80211 emu10k1_gp snd_timer input_polldev snd_page_alloc crc_itu_t snd_util_mem snd_seq_device snd_hwdep eeprom_93cx6 snd usblp iTCO_wdt iTCO_vendor_support intel_agp soundcore agpgart af_packet shpchp parport_pc pci_hotplug parport pcspkr analog gameport evdev joydev ext3 jbd mbcache sg usbhid hid sr_mod cdrom sd_mod ata_piix ata_generic ehci_hcd libata uhci_hcd tulip floppy usbcore scsi_mod thermal processor fan fuse
Jan 10 03:01:20 Levendis kernel: apparmor commoncap
Jan 10 03:01:20 Levendis kernel: [78862.364693] note: softirq-rcu/0[13] exited with preempt_count 1
Jan 10 03:09:23 Levendis syslogd 1.4.1#21ubuntu3: restart.
```

The restart was when the computer crashed. It became very slow and stopped responding when I attempted a software restart. So I hit the reset button, something which I am forced to do far too often nowadays.

Any ideas???

---

### Post by cmnorton on 2008-01-12
Posting some details about your hardware might help.

---

### Post by jesushero on 2008-01-13
Ok, here they are:

CPU Intel Pentium 4 2.6GHz
512mb DDRAM (1 stack)
ASUS Albatron motherboard (Phoenix Award BIOS V6.0 PG)
nVidia NV34 (nvidia FX 5200) graphics controller 8x AGP 128mb
soundblaster SB Live Value CT4832 sound controller PCI
Non-USB keyboard
have tried both USB and serial port mouse (no difference)
have tried both default NV drivers and original NVIDIA restricted drivers (no difference)
PCI Wireless card (sitecom 54g turbo) (but not used, just plugged in)

IDE Primary master: Western Digital 500GB ext3
IDE Primary slave: Western Digital 120GB ext3 (nothing in it now, mounted on a backup directory I rarely use)
IDE Secondary master: Asus DVD-RW 
IDE Secondary slave: Western Digital 20GB swap (yes, 20GB swap)

Floppy Disk (works fine)

Single boot Ubuntu Studio 7.10 Gutsy. All updates up to now installed. Installed flash and javascript runtime environment on firefox. Installed Cinelerra video editor. Installed OpenOffice. Installed gcc compiler. Installed skype.

That's about all there is to it. Let me know if any of those rings any bells or if other people with the same hardware or software have been experiencing similar problems.

Any ideas???

---

