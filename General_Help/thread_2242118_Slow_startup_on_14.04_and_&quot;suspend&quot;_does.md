---
title: "Slow startup on 14.04 and &quot;suspend&quot; doesn't work at all"
date: 2014-08-30
forum: General Help
---

### Post by mark allyn on 2014-08-30
Hello everyone,

This thread is related toi an earlier one.  I thought it sufficiently different to warrant a new thread.  I hope you agree.

I have just installed 14.04 from a CD-ROM.  The installation went fine.  However, when I boot up from a cold start it takes about 20 minutes for the screen to light up.  After that, everything proceeds normally.

If I hit the suspend tab, the machine shuts down.  However, when I attempt to wake it up, it apparently never does, although I can hear the drive wake up--but after that, nothing happens.  I say apparently because it is unresponsive after half an hour.

I've scanned around the internet (including this forum) and found nothing useful.  Perhaps you folks might have a suggestion.  The delays are intolerable, and if I can't fix the problem I will revert to 12.04.

Regards,
Mark Allyn

---

### Post by whitesmith on 2014-08-30
Have you poked around the logs? One of our more astute contributors has put together a tutorial on the subject ([http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)) that may help you find the problem. *Linux logs everything!*

---

### Post by mark allyn on 2014-08-30
Hello Whitesmith,

Thanks for the tip.  I have timed the delay from the moment I reboot until a screen appears.  It is pretty nearly exactly 10 minutes from the cold start.  It is very reliably this length of time--at least to within my skill at watch reading.

I'll have a look at the link you suggest.  I'm completely baffled.

Mark

---

### Post by mark allyn on 2014-08-31
Good morning, whitesmith and everyone else,

OK, here is a copy of /var/log/syslog rresults.  At 6:30 AM EST I booted up from a cold start.  Ten minutes later the screen lit up, and I issued the command:  egrep -i 'error|warning" /var/log/*log.  The following appeared.  The time stamp indicates the precise time (after the screen lights up) as 10 minutes following the boot.


```
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [    0.216247] ACPI BIOS Error (bug): \_SB_.PCI0._OSC: Excess arguments - ASL declared 5, ACPI requires 4 (20131115/nsarguments-189)
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [    0.216295] ACPI Error: [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS (20131115/dsfield-211)
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [    0.216299] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7026cf0), AE_ALREADY_EXISTS (20131115/psparse-536)
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [    0.216305] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [  605.840059] tpm_tis 00:0a: A TPM error (7) occurred attempting to read a pcr value
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [  613.138224] WARNING: CPU: 0 PID: 298 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_opregion.c:266 swsci+0x2c9/0x2e0 [i915]()
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [  613.164917] WARNING! power/level is deprecated; use power/control instead
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [  613.244029] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 184
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [  613.324632] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 184
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [  613.397649] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 184
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [  613.468033] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 184
/var/log/syslog:Aug 31 06:40:28 mark-HP-Compaq-dc5800-Microtower kernel: [  616.337134] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Aug 31 06:40:30 mark-HP-Compaq-dc5800-Microtower hp-firmware: hp-firmware[522]: error: Firmware file '/usr/share/hplip/data/firmware/hp_laserjet_p1505.fw.gz' not found.
/var/log/syslog:Aug 31 06:40:30 mark-HP-Compaq-dc5800-Microtower hp-firmware: hp-firmware[522]: error: Firmware download failed.
/var/log/syslog:Aug 31 06:40:30 mark-HP-Compaq-dc5800-Microtower hp-config_usb_printer: hp-config_usb_printer[357]: warning: Failed to download firmware to hp:/usb/HP_LaserJet_P1505?serial=CA50077 device
/var/log/syslog:Aug 31 06:40:56 mark-HP-Compaq-dc5800-Microtower NetworkManager[788]: <error> [1409481656.43664] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Aug 31 06:40:56 mark-HP-Compaq-dc5800-Microtower dnsmasq[1464]: warning: no upstream servers configured
/var/log/Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

```

Clearly, there are multiple problems.  If its like most of these sorts of things there is one trigger error and then things fall apart from there on in a cascade of software agony.  That kind of logic would suggest that the initial error concerning the BIOS is likely the cause.  But, my reasoning could be faulty.  Certainly, the BIOS error needs to be corrected, but I haven't a clue as to how to do this.  I am guessing that I gotta do something with the GRUB.  But what?

Regards,
Mark

---

