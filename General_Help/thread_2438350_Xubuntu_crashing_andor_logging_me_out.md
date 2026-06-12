---
title: "Xubuntu crashing and/or logging me out"
date: 2020-03-10
forum: General Help
---

### Post by peyre on 2020-03-10
I've had trouble for a number of weeks now with Xubuntu freezing or logging me out for no apparent reason.

More often it freezes: I'll be navigating in Thunar or maybe using Firefox, and the computer simply stops responding to mouse clicks or keyboard commands.  I can move the mouse cursor as much as I like, but I can't do anything with it.  Usually I have music playing, and it keeps playing when the system stops responding, so this might be a problem with X specifically.  Anyhow, the only thing I'm able to do then is to physically power the machine off and start up again.  Often this will happen in two or three times in a row, followed by a period of hours before it does it again.

Sometimes, instead, it logs me off.  Then I can log back in just fine, but if I was backing up my data, I have to start over from scratch.  This happens less often than the freezing, but still annoying.

More information can be found at my post at [https://ubuntuforums.org/showthread.php?t=2421945]("https://ubuntuforums.org/showthread.php?t=2421945"), but here's a synopsis.

[LIST]
[*]I was running Xubuntu 19.10 and people suggested I switch to LTS, so I reinstalled 18.04 from scratch.
[*]People suggested I check the SMART data for my system drive (an SSD) and my data drive (1TB mechanical).  They pass the tests with flying colors, as far as I can tell.  Now I know SMART is notorious for giving false negatives at times, but still...
[*]In the end someone suggested I might have a problem with my motherboard, so I changed computers.  I pulled my drives and graphics card out of my old computer and plugged them into a newer one, and the problem continues.
[*]I thought maybe it's the graphics card at fault, so I changed it out for another, without effect.
[*]I could reinstall Xubuntu from scratch again, but that's a big deal - there are so many things to set up and configure when I reinstall my OS, I don't want to do it for a *second* time on a "maybe this time" basis.
[/LIST]

Does anyone have any suggestions?  I'm at a loss here.

---

### Post by peyre on 2020-03-27
Hmm, I've tried turning off Google Chrome hardware acceleration, as suggested at [https://unix.stackexchange.com/questions/487346/ubuntu-18-04-is-freezing-randomly]("https://unix.stackexchange.com/questions/487346/ubuntu-18-04-is-freezing-randomly") and [https://help.ubuntu.com/stable/ubuntu-help/session-screenlocks.html.en]("https://help.ubuntu.com/stable/ubuntu-help/session-screenlocks.html.en").  So far it hasn't locked up on me since (which is kind of odd as I don't use Chrome very often), but maybe that's done the trick...if I haven't just jinxed it by posting this.

---

### Post by peyre on 2020-03-28
Ha! No.  I just fired up my computer this morning; it ran for a while, but then it locked up.  I turned it back on and it locked up again pretty much immediately.  And again.  And again - it locked up on me four times in quick succession.  Then it worked for a little bit and logged me off.  What is *with* this OS?!

The lockups do seem to run in series like this.  Don't know why, but maybe it's a clue as to what's going on.

---

### Post by Autodave on 2020-03-28
Are you sure that it is the OS and not your hardware?  It really sounds like a hardware issue to me.  You could have a RAM chip going bad, a power supply failing, or a number of other things.

Overheating?  Have you cleaned it lately?  Fans operating?

Is this a laptop or desktop?

---

### Post by peyre on 2020-03-28
That's a fair question.  Someone suggested that on a previous thread where I brought this up.  So I changed **computers**.  My wife got an upgrade for her computer, so I pulled the hard drives and video card out of my old box and installed them in her old system (and blew out the dust while I was at it).  The problem continued, so I swapped out the video card for an old one we had lying around, and the problem still continued.  So, it's followed me from one physical computer to another.

It's possible there's a problem with the hard drives (an SSD and a mechanical), but I've checked them several times with S.M.A.R.T. utilities, and the test results are all good.  I know SMART is known for giving false negatives, but changing out the drives isn't something real easy to do, and it's a lot to try on a "maybe".

---

### Post by ajgreeny on 2020-03-28
I fully agree with Autodave about this being more likely to be a hardware problem; certainly it is not what is normal for the OS itself, ie, Xubuntu 18.04, which I've been running on a laptop and desktop now since 18.04 was released, and as far as I can remember I have never once in that period had either of those two systems lock up on me.

As you keep shifting the same hard disk from machine to machine it does rather point to the disk, I agree, even though SMART tells you it's all OK.

As a test can you run a live version of 18.04.4 and see if that also suffers in the same way.  It might also be worth running command ```
sudo e2fsck /dev/sdx#
``` where the sdx# is the root partition of your problem OS.  You may need to run ***sudo blkid*** to make sure you get that right in the command.

Finally, using the problem OS and machine, can you please show the output of command ```
inxi -Fzx
```

---

### Post by peyre on 2020-03-29
Ah, thanks!  Let's see...

```
**sudo e2fsck /dev/sda1**
e2fsck 1.44.4 (18-Aug-2018)
/dev/sda1: clean, 545739/15269888 files, 44356354/61049088 blocks

**sudo e2fsck /dev/sdb1**
e2fsck 1.44.4 (18-Aug-2018)
Storage: clean, 167460/61054976 files, 178647257/244189952 blocks

**inxi -Fzx**
System:    Host: peyre Kernel: 5.3.0-42-generic x86_64 bits: 64 gcc: 7.4.0
           Desktop: Xfce 4.12.3 (Gtk 2.24.31) Distro: Ubuntu 18.04.4 LTS
Machine:   Device: desktop System: Dell product: Inspiron 3847 serial: N/A
           Mobo: Dell model: 088DT1 v: A01 serial: N/A
           BIOS: Dell v: A11 date: 05/07/2019
CPU:       Quad core Intel Core i5-4460 (-MCP-) 
           arch: Haswell rev.3 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 25542
           clock speeds: max: 3400 MHz 1: 1430 MHz 2: 1498 MHz 3: 1619 MHz
           4: 1471 MHz
Graphics:  Card-1: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Card-2: NVIDIA G94 [GeForce 9600 GT] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.20.5 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1280x1024@60.02hz, 1280x1024@60.02hz
           OpenGL: renderer: NV94 version: 3.3 Mesa 19.2.8 Direct Render: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k5.3.0-42-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 port: d000 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k bus-ID: 04:00.0
           IF: wlp4s0 state: down mac: <filter>
           Card-3: Atheros usb-ID: 003-008
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 1250.3GB (71.3% used)
           ID-1: /dev/sda model: Samsung_SSD_860 size: 250.1GB
           ID-2: /dev/sdb model: ST1000DM003 size: 1000.2GB
Partition: ID-1: / size: 229G used: 165G (76%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 33.0C mobo: N/A gpu: 41.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 252 Uptime: 0 min Memory: 1277.4/7879.2MB
           Init: systemd runlevel: 5 Gcc sys: 7.5.0
           Client: Shell (bash 4.4.201) inxi: 2.3.56
```

---

### Post by peyre on 2020-03-31
Am I right in thinking that it's more likely the system drive (the SSD) that's at fault, rather than the data drive (HDD)?

---

### Post by peyre on 2020-03-31
Other observations: as I mentioned above if I have music playing, it continues to play.  However, Audacious seems to lock up as well when the current song ends, or at some point it starts repeating the last chord over and over.  Holding down the power button for a few seconds seems to free it up to keep playing.  Doesn't fix the computer lock though.

Also, these lockups seem to occur most often when I'm navigating the file system, so I've wondered if Thunar might be at fault.  I reinstalled it in Synaptic though, so that doesn't seem to be it either.

---

### Post by Autodave on 2020-03-31
It could be either drive.  Personally, I would suspect the spinner one first since SSDs don't normally have intermittant issues: they either work or they don't.

---

### Post by ajgreeny on 2020-03-31
Have you tried running the live system as I suggested before.

I imagine you may have done so in order to run the e2fsck commands but you didn't say how long it was running nor whether there were problems running it live.

---

### Post by peyre on 2020-03-31
Oh!  Yes, I booted from a Xubuntu 19.10 DVD I had close to hand.

Well, and I may have found the problem.  Seems I was out of free space (or dangerously near).  My shell script to back up my data had made a couple copies of my backup to my system drive!  I'll have to take a look at how that happened.  Once I get over feeling like a total noob, anyway.

---

### Post by ajgreeny on 2020-04-01
Yes, that would do it, most definitely!

Keep an eye on how things go now and if all is well after a while please mark as **SOLVED** from the **Thread Tools** up top.

---

### Post by peyre on 2020-04-02
Thanks, I've been waiting to see if it really remains stable - it's an intermittent issue, and I've had times when it seemed stable for several days, only to crash on me when I least expected.

Anyhow, I appreciate you taking time to offer me suggestions on this.  It actually did help, since it was while running from a live disk that I spotted the lack of free space.

---

### Post by peyre on 2020-04-02
And, it's just logged me off again!  But I still have 164GB free on my system drive.  ](*,)

Any idea what might cause these spontaneous logoffs, assuming they're a separate issue from the lockups?

---

### Post by ajgreeny on 2020-04-03
I am not sure what might do that, and a search has not been any help, but you might find a clue if you look in /var/log/syslog, searching for the word **session**.

---

### Post by peyre on 2020-04-03
Well, I got home, turned my system on, and . . . it froze on me again.  What ---- it's very tempting to employ a colorful metaphor, after all this.

I still have 164GB free.

/var/log/syslog cats as follows:
```
Apr  3 19:46:57 peyre rsyslogd:  [origin software="rsyslogd" swVersion="8.32.0" x-pid="701" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Apr  3 19:46:58 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:47:05 peyre gvfsd-metadata[1732]: message repeated 25 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Apr  3 19:47:05 peyre anacron[713]: Job `cron.daily' terminated
Apr  3 19:47:05 peyre anacron[713]: Normal exit (1 job run)
Apr  3 19:47:11 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:47:11 peyre gvfsd-metadata[1732]: message repeated 5 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Apr  3 19:47:51 peyre systemd-resolved[519]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Apr  3 19:47:51 peyre systemd-resolved[519]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Apr  3 19:48:01 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:48:01 peyre kernel: [  369.143628] audit: type=1400 audit(1585968481.779:79): apparmor="DENIED" operation="capable" profile="snap.okteta.okteta" pid=3435 comm="okteta" capability=2  capname="dac_read_search"
Apr  3 19:48:01 peyre kernel: [  369.143640] audit: type=1400 audit(1585968481.779:80): apparmor="DENIED" operation="capable" profile="snap.okteta.okteta" pid=3435 comm="okteta" capability=1  capname="dac_override"

```

If it matters, /var/logs/lastlog cats as:
```
&#65533;&#65533;^tty1|w&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;$mU&#65533;&#65533;wM&#65533;p&&#65533;$mUp&&#65533;$mU&#65533;&#65533;L&#65533;&#65533;&#65533;wM&#65533;p&&#65533;$mUp&&#65533;$mU&#65533;&#65533;$mUf&#65533;wM&#65533;@&#65533;&#65533;$mU&#65533;&#1032;t&#65533;J/&#65533;&#65533;$mU&#65533;&#65533;$mUD"xM&#65533;&#65533;T&#65533;M&#65533;PZ&#65533;Z&#65533;p&&#65533;$mU&#65533;&#65533;wM&#65533;&#65533;&#1032;t&#65533;J/HZ&#65533;Z&#65533;@&#65533;&#65533;$mU&#65533;p&&#65533;$mU&#65533;&#65533;
```

There's also a /var/logs/syslog.1, which cats as:
```
d0/input8
Apr  3 19:41:57 peyre kernel: [    4.320532] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9
Apr  3 19:41:57 peyre kernel: [    4.320559] input: HDA Intel HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/sound/card0/input10
Apr  3 19:41:57 peyre kernel: [    4.320586] input: HDA Intel HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:03.0/sound/card0/input11
Apr  3 19:41:57 peyre kernel: [    4.321344] ath: phy0: WB335 1-ANT card detected
Apr  3 19:41:57 peyre kernel: [    4.321345] ath: phy0: Set BT/WLAN RX diversity capability
Apr  3 19:41:57 peyre kernel: [    4.322842] snd_hda_codec_realtek hdaudioC1D2: autoconfig for ALC662 rev3: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
Apr  3 19:41:57 peyre kernel: [    4.322844] snd_hda_codec_realtek hdaudioC1D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Apr  3 19:41:57 peyre kernel: [    4.322845] snd_hda_codec_realtek hdaudioC1D2:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Apr  3 19:41:57 peyre kernel: [    4.322845] snd_hda_codec_realtek hdaudioC1D2:    mono: mono_out=0x0
Apr  3 19:41:57 peyre kernel: [    4.322846] snd_hda_codec_realtek hdaudioC1D2:    inputs:
Apr  3 19:41:57 peyre kernel: [    4.322847] snd_hda_codec_realtek hdaudioC1D2:      Rear Mic=0x19
Apr  3 19:41:57 peyre kernel: [    4.322848] snd_hda_codec_realtek hdaudioC1D2:      Front Mic=0x18
Apr  3 19:41:57 peyre kernel: [    4.322849] snd_hda_codec_realtek hdaudioC1D2:      Line=0x1a
Apr  3 19:41:57 peyre kernel: [    4.334928] ath: phy0: Enable LNA combining
Apr  3 19:41:57 peyre kernel: [    4.335176] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
Apr  3 19:41:57 peyre kernel: [    4.335209] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13
Apr  3 19:41:57 peyre kernel: [    4.335239] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14
Apr  3 19:41:57 peyre kernel: [    4.335270] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input15
Apr  3 19:41:57 peyre kernel: [    4.335298] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input16
Apr  3 19:41:57 peyre kernel: [    4.337787] ath: phy0: ASPM enabled: 0x43
Apr  3 19:41:57 peyre kernel: [    4.337788] ath: EEPROM regdomain: 0x60
Apr  3 19:41:57 peyre kernel: [    4.337788] ath: EEPROM indicates we should expect a direct regpair map
Apr  3 19:41:57 peyre kernel: [    4.337789] ath: Country alpha2 being used: 00
Apr  3 19:41:57 peyre kernel: [    4.337790] ath: Regpair used: 0x60
Apr  3 19:41:57 peyre kernel: [    4.342325] AVX2 version of gcm_enc/dec engaged.
Apr  3 19:41:57 peyre kernel: [    4.342326] AES CTR mode by8 optimization enabled
Apr  3 19:41:57 peyre kernel: [    4.349590] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Apr  3 19:41:57 peyre kernel: [    4.349849] ieee80211 phy0: Atheros AR9565 Rev:1 mem=0xffffa98940980000, irq=16
Apr  3 19:41:57 peyre kernel: [    4.350948] [TTM] Zone  kernel: Available graphics memory: 4034140 KiB
Apr  3 19:41:57 peyre kernel: [    4.350949] [TTM] Zone   dma32: Available graphics memory: 2097152 KiB
Apr  3 19:41:57 peyre kernel: [    4.350950] [TTM] Initializing pool allocator
Apr  3 19:41:57 peyre kernel: [    4.350953] [TTM] Initializing DMA pool allocator
Apr  3 19:41:57 peyre kernel: [    4.350970] nouveau 0000:01:00.0: DRM: VRAM: 512 MiB
Apr  3 19:41:57 peyre kernel: [    4.350971] nouveau 0000:01:00.0: DRM: GART: 1048576 MiB
Apr  3 19:41:57 peyre kernel: [    4.350974] nouveau 0000:01:00.0: DRM: TMDS table version 2.0
Apr  3 19:41:57 peyre kernel: [    4.350975] nouveau 0000:01:00.0: DRM: DCB version 4.0
Apr  3 19:41:57 peyre kernel: [    4.350976] nouveau 0000:01:00.0: DRM: DCB outp 00: 02000300 00000028
Apr  3 19:41:57 peyre kernel: [    4.350977] nouveau 0000:01:00.0: DRM: DCB outp 01: 01000302 00020030
Apr  3 19:41:57 peyre kernel: [    4.350978] nouveau 0000:01:00.0: DRM: DCB outp 02: 04011310 00000028
Apr  3 19:41:57 peyre kernel: [    4.350979] nouveau 0000:01:00.0: DRM: DCB outp 03: 02022322 00020010
Apr  3 19:41:57 peyre kernel: [    4.350980] nouveau 0000:01:00.0: DRM: DCB conn 00: 00001030
Apr  3 19:41:57 peyre kernel: [    4.350980] nouveau 0000:01:00.0: DRM: DCB conn 01: 00000100
Apr  3 19:41:57 peyre kernel: [    4.350981] nouveau 0000:01:00.0: DRM: DCB conn 02: 00002261
Apr  3 19:41:57 peyre kernel: [    4.352952] nouveau 0000:01:00.0: DRM: MM: using CRYPT for buffer copies
Apr  3 19:41:57 peyre kernel: [    4.358560] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Apr  3 19:41:57 peyre kernel: [    4.358560] [drm] Driver supports precise vblank timestamp query.
Apr  3 19:41:57 peyre kernel: [    4.407546] usb 3-10: new full-speed USB device number 9 using xhci_hcd
Apr  3 19:41:57 peyre kernel: [    4.420198] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.3)
Apr  3 19:41:57 peyre kernel: [    4.424465] nouveau 0000:01:00.0: DRM: allocated 1280x1024 fb: 0x70000, bo 00000000e10a75c2
Apr  3 19:41:57 peyre kernel: [    4.424600] fbcon: nouveaudrmfb (fb0) is primary device
Apr  3 19:41:57 peyre kernel: [    4.424668] Console: switching to colour frame buffer device 160x64
Apr  3 19:41:57 peyre kernel: [    4.424682] nouveau 0000:01:00.0: fb0: nouveaudrmfb frame buffer device
Apr  3 19:41:57 peyre systemd[1]: Started D-Bus System Message Bus.
Apr  3 19:41:57 peyre anacron[713]: Will run job `cron.daily' in 5 min.
Apr  3 19:41:57 peyre anacron[713]: Jobs will be executed sequentially
Apr  3 19:41:57 peyre kernel: [    4.444543] [drm] Initialized nouveau 1.3.1 20120801 for 0000:01:00.0 on minor 1
Apr  3 19:41:57 peyre systemd-udevd[404]: link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
Apr  3 19:41:57 peyre dbus-daemon[721]: dbus[721]: Unknown group "power" in message bus configuration file
Apr  3 19:41:57 peyre acpid: starting up with netlink and the input layer
Apr  3 19:41:57 peyre acpid: 8 rules loaded
Apr  3 19:41:57 peyre acpid: waiting for events: event logging is off
Apr  3 19:41:57 peyre dbus-daemon[721]: [system] AppArmor D-Bus mediation is enabled
Apr  3 19:41:57 peyre dbus-daemon[721]: [system] Successfully activated service 'org.freedesktop.systemd1'
Apr  3 19:41:57 peyre systemd[1]: Started Login Service.
Apr  3 19:41:57 peyre systemd[1]: Starting Network Manager...
Apr  3 19:41:57 peyre systemd[1]: Starting LSB: Speech Dispatcher...
Apr  3 19:41:57 peyre systemd[1]: Starting Modem Manager...
Apr  3 19:41:57 peyre systemd[1]: Starting Initialize hardware monitoring sensors...
Apr  3 19:41:57 peyre thermald[703]: NO RAPL sysfs present
Apr  3 19:41:57 peyre thermald[703]: 13 CPUID levels; family:model:stepping 0x6:3c:3 (6:60:3)
Apr  3 19:41:57 peyre thermald[703]: Polling mode is enabled: 4
Apr  3 19:41:57 peyre thermald[703]: Thermal DTS: No coretemp sysfs found
Apr  3 19:41:57 peyre systemd[1]: Started Set the CPU Frequency Scaling governor.
Apr  3 19:41:57 peyre systemd[1]: Starting LSB: Record successful boot for GRUB...
Apr  3 19:41:57 peyre dbus-daemon[721]: [system] Activating via systemd: service name='org.freedesktop.ColorManager' unit='colord.service' requested by ':1.4' (uid=0 pid=708 comm="/usr/sbin/cupsd -l " label="/usr/sbin/cupsd (enforce)")
Apr  3 19:41:57 peyre systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Apr  3 19:41:57 peyre systemd[1]: Starting Restore /etc/resolv.conf if the system crashed before the ppp link was shut down...
Apr  3 19:41:57 peyre systemd[1]: Starting WPA supplicant...
Apr  3 19:41:57 peyre systemd[1]: Starting LSB: EPSON Custom Backend Daemon...
Apr  3 19:41:57 peyre systemd[1]: Starting Detect the available GPUs and deal with any system changes...
Apr  3 19:41:57 peyre systemd[1]: Starting Save/Restore Sound Card State...
Apr  3 19:41:57 peyre systemd[1]: Starting Disk Manager...
Apr  3 19:41:57 peyre systemd[1]: Starting Accounts Service...
Apr  3 19:41:57 peyre avahi-daemon[741]: Found user 'avahi' (UID 117) and group 'avahi' (GID 124).
Apr  3 19:41:57 peyre avahi-daemon[741]: Successfully dropped root privileges.
Apr  3 19:41:57 peyre avahi-daemon[741]: avahi-daemon 0.7 starting up.
Apr  3 19:41:57 peyre avahi-daemon[741]: Successfully called chroot().
Apr  3 19:41:57 peyre avahi-daemon[741]: Successfully dropped remaining capabilities.
Apr  3 19:41:57 peyre systemd[1]: Started System Logging Service.
Apr  3 19:41:57 peyre thermald[703]: Thermal DTS or hwmon: No Zones present Need to configure manually
Apr  3 19:41:57 peyre avahi-daemon[741]: No service file found in /etc/avahi/services.
Apr  3 19:41:57 peyre ecbd[746]: Starting ecbd:.
Apr  3 19:41:57 peyre avahi-daemon[741]: Joining mDNS multicast group on interface lo.IPv6 with address ::1.
Apr  3 19:41:57 peyre avahi-daemon[741]: New relevant interface lo.IPv6 for mDNS.
Apr  3 19:41:57 peyre avahi-daemon[741]: Joining mDNS multicast group on interface lo.IPv4 with address 127.0.0.1.
Apr  3 19:41:57 peyre avahi-daemon[741]: New relevant interface lo.IPv4 for mDNS.
Apr  3 19:41:57 peyre avahi-daemon[741]: Network interface enumeration completed.
Apr  3 19:41:57 peyre avahi-daemon[741]: Registering new address record for ::1 on lo.*.
Apr  3 19:41:57 peyre avahi-daemon[741]: Registering new address record for 127.0.0.1 on lo.IPv4.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for core18, revision 1668.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for vlc, revision 1397.
Apr  3 19:41:57 peyre systemd[1]: Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down.
Apr  3 19:41:57 peyre systemd[1]: Started LSB: EPSON Custom Backend Daemon.
Apr  3 19:41:57 peyre ModemManager[735]: <info>  ModemManager (version 1.10.0) starting in system bus...
Apr  3 19:41:57 peyre udisksd[751]: udisks daemon version 2.7.6 starting
Apr  3 19:41:57 peyre sensors[766]: dell_smm-virtual-0
Apr  3 19:41:57 peyre sensors[766]: Adapter: Virtual device
Apr  3 19:41:57 peyre sensors[766]: Processor Fan:    485 RPM
Apr  3 19:41:57 peyre sensors[766]: Motherboard Fan:  837 RPM
Apr  3 19:41:57 peyre sensors[766]: Other:            +27.0°C
Apr  3 19:41:57 peyre sensors[766]: nouveau-pci-0100
Apr  3 19:41:57 peyre sensors[766]: Adapter: PCI adapter
Apr  3 19:41:57 peyre sensors[766]: GPU core:     +1.00 V  (min =  +0.90 V, max =  +1.00 V)
Apr  3 19:41:57 peyre sensors[766]: temp1:        +38.0°C  (high = +95.0°C, hyst =  +3.0°C)
Apr  3 19:41:57 peyre sensors[766]:                        (crit = +105.0°C, hyst =  +5.0°C)
Apr  3 19:41:57 peyre sensors[766]:                        (emerg = +115.0°C, hyst =  +2.0°C)
Apr  3 19:41:57 peyre dbus-daemon[721]: [system] Activating via systemd: service name='org.freedesktop.PolicyKit1' unit='polkit.service' requested by ':1.7' (uid=0 pid=735 comm="/usr/sbin/ModemManager --filter-policy=strict " label="unconfined")
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for gtk-common-themes, revision 1474.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for gnome-system-monitor, revision 135.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for core18, revision 1705.
Apr  3 19:41:57 peyre systemd[1]: Started Initialize hardware monitoring sensors.
Apr  3 19:41:57 peyre gpu-manager[747]: Error: can't open /lib/modules/5.3.0-45-generic/updates/dkms
Apr  3 19:41:57 peyre gpu-manager[747]: Error: can't open /lib/modules/5.3.0-45-generic/updates/dkms
Apr  3 19:41:57 peyre wpa_supplicant[744]: Successfully initialized wpa_supplicant
Apr  3 19:41:57 peyre apport[707]:  * Starting automatic crash report generation: apport
Apr  3 19:41:57 peyre systemd[1]: Started Detect the available GPUs and deal with any system changes.
Apr  3 19:41:57 peyre speech-dispatcher[734]:  * speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Apr  3 19:41:57 peyre udisksd[751]: failed to load module mdraid: libbd_mdraid.so.2: cannot open shared object file: No such file or directory
Apr  3 19:41:57 peyre systemd[1]: Started LSB: Speech Dispatcher.
Apr  3 19:41:57 peyre apport[707]:    ...done.
Apr  3 19:41:57 peyre systemd[1]: Started LSB: automatic crash report generation.
Apr  3 19:41:57 peyre systemd[1]: Started Thermal Daemon Service.
Apr  3 19:41:57 peyre grub-common[740]:  * Recording successful boot for GRUB
Apr  3 19:41:57 peyre systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Apr  3 19:41:57 peyre systemd[1]: Started Save/Restore Sound Card State.
Apr  3 19:41:57 peyre udisksd[751]: Failed to load the 'mdraid' libblockdev plugin
Apr  3 19:41:57 peyre systemd[1]: Started WPA supplicant.
Apr  3 19:41:57 peyre systemd[1]: Starting Authorization Manager...
Apr  3 19:41:57 peyre systemd[1]: Started Make remote CUPS printers available locally.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.3481] NetworkManager (version 1.10.6) is starting... (for the first time)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.3482] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, no-mac-addr-change.conf) (run: 10-globally-managed-devices.conf) (etc: default-wifi-powersave-on.conf)
Apr  3 19:41:57 peyre systemd[1]: Starting Manage, Install and Generate Color Profiles...
Apr  3 19:41:57 peyre systemd[1]: Listening on Load/Save RF Kill Switch Status /dev/rfkill Watch.
Apr  3 19:41:57 peyre systemd[1]: Starting Load/Save RF Kill Switch Status...
Apr  3 19:41:57 peyre grub-common[740]:    ...done.
Apr  3 19:41:57 peyre systemd[1]: Started LSB: Record successful boot for GRUB.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.3579] manager[0x5568cbb94060]: monitoring kernel firmware directory '/lib/firmware'.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.3581] monitoring ifupdown state file '/run/network/ifstate'.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for gimp, revision 246.
Apr  3 19:41:57 peyre dbus-daemon[721]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.10' (uid=0 pid=733 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Apr  3 19:41:57 peyre systemd[1]: Starting Hostname Service...
Apr  3 19:41:57 peyre polkitd[817]: started daemon version 0.105 using authority implementation `local' version `0.105'
Apr  3 19:41:57 peyre dbus-daemon[721]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Apr  3 19:41:57 peyre accounts-daemon[752]: started daemon version 0.6.45
Apr  3 19:41:57 peyre systemd[1]: Started Authorization Manager.
Apr  3 19:41:57 peyre systemd[1]: Started Accounts Service.
Apr  3 19:41:57 peyre dbus-daemon[721]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for gtk-common-themes, revision 1440.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for skype, revision 115.
Apr  3 19:41:57 peyre systemd[1]: Started Manage, Install and Generate Color Profiles.
Apr  3 19:41:57 peyre dbus-daemon[721]: [system] Successfully activated service 'org.freedesktop.hostname1'
Apr  3 19:41:57 peyre systemd[1]: Started Hostname Service.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.3942] hostname: hostname: using hostnamed
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.3942] hostname: hostname changed from (none) to "peyre"
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.3944] dns-mgr[0x5568cbb861a0]: init: dns=systemd-resolved, rc-manager=symlink, plugin=systemd-resolved
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.3951] rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/ieee80211/phy0/rfkill0) (driver ath9k)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.3952] manager[0x5568cbb94060]: rfkill: WiFi hardware radio set enabled
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.3952] manager[0x5568cbb94060]: rfkill: WWAN hardware radio set enabled
Apr  3 19:41:57 peyre systemd[1]: Started Network Manager.
Apr  3 19:41:57 peyre systemd[1]: Reached target Network.
Apr  3 19:41:57 peyre systemd[1]: Starting Permit User Sessions...
Apr  3 19:41:57 peyre systemd[1]: Started Unattended Upgrades Shutdown.
Apr  3 19:41:57 peyre systemd[1]: Starting Network Manager Wait Online...
Apr  3 19:41:57 peyre systemd[1]: Started Permit User Sessions.
Apr  3 19:41:57 peyre systemd[1]: Started Modem Manager.
Apr  3 19:41:57 peyre systemd[1]: Starting Light Display Manager...
Apr  3 19:41:57 peyre systemd[1]: Starting Hold until boot process finishes up...
Apr  3 19:41:57 peyre dbus-daemon[721]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.10' (uid=0 pid=733 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Apr  3 19:41:57 peyre systemd[1]: Starting Network Manager Script Dispatcher Service...
Apr  3 19:41:57 peyre networkd-dispatcher[715]: WARNING: systemd-networkd is not running, output will be incomplete.
Apr  3 19:41:57 peyre dbus-daemon[721]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr  3 19:41:57 peyre systemd[1]: Started Network Manager Script Dispatcher Service.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4232] init!
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4239]       interface-parser: parsing file /etc/network/interfaces
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4240]       interface-parser: finished parsing file /etc/network/interfaces
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4241] management mode: unmanaged
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4244] devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0, iface: enp3s0)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4244] device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0, iface: enp3s0): no ifupdown configuration found.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4245] devices added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/wlan0, iface: wlan0)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4245] device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4245] devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4245] device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4245] end _init.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4245] settings: loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ifupdown.so)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4246] settings: loaded plugin keyfile: (c) 2007 - 2016 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4246] (-876811072) ... get_connections.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4246] (-876811072) ... get_connections (managed=false): return empty list.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4249] get unmanaged devices count: 0
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4249] manager: rfkill: WiFi enabled by radio killswitch; enabled by state file
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4249] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4249] manager: Networking is enabled by state file
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4250] dhcp-init: Using DHCP client 'dhclient'
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4254] Loaded device plugin: NMBondDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4254] Loaded device plugin: NMBridgeDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4254] Loaded device plugin: NMDummyDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4254] Loaded device plugin: NMEthernetDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4254] Loaded device plugin: NMInfinibandDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4254] Loaded device plugin: NMIPTunnelDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4254] Loaded device plugin: NMMacsecDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4254] Loaded device plugin: NMMacvlanDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4255] Loaded device plugin: NMPppDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4255] Loaded device plugin: NMTunDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4255] Loaded device plugin: NMVethDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4255] Loaded device plugin: NMVlanDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4255] Loaded device plugin: NMVxlanDeviceFactory (internal)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4280] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
Apr  3 19:41:57 peyre nm-dispatcher: req:1 'hostname': new request (1 scripts)
Apr  3 19:41:57 peyre nm-dispatcher: req:1 'hostname': start running ordered scripts...
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4334] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-team.so)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4354] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4404] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Apr  3 19:41:57 peyre systemd[1]: Started Dispatcher daemon for systemd-networkd.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4416] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4435] device (lo): carrier: link connected
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4440] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4449] manager: (enp3s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4459] keyfile: add connection in-memory (b3aa4745-a3e7-3d91-aa0a-cc004a8e3726,"Wired connection 1")
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4471] settings: (enp3s0): created default wired connection 'Wired connection 1'
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.4479] device (enp3s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Apr  3 19:41:57 peyre kernel: [    4.664680] Generic Realtek PHY r8169-300:00: attached PHY driver [Generic Realtek PHY] (mii_bus:phy_addr=r8169-300:00, irq=IGNORE)
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for skype, revision 118.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for gtk2-common-themes, revision 9.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for okteta, revision 11.
Apr  3 19:41:57 peyre systemd[1]: Started Hold until boot process finishes up.
Apr  3 19:41:57 peyre systemd[1]: Received SIGRTMIN+21 from PID 514 (n/a).
Apr  3 19:41:57 peyre systemd[1]: Starting Set console scheme...
Apr  3 19:41:57 peyre systemd[1]: Started Light Display Manager.
Apr  3 19:41:57 peyre systemd[1]: Started Set console scheme.
Apr  3 19:41:57 peyre systemd[1]: Created slice system-getty.slice.
Apr  3 19:41:57 peyre systemd[1]: Started Getty on tty1.
Apr  3 19:41:57 peyre systemd[1]: Reached target Login Prompts.
Apr  3 19:41:57 peyre colord[822]: failed to get session [pid 708]: No data available
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for gnome-system-monitor, revision 127.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for gedit, revision 537.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for gimp, revision 252.
Apr  3 19:41:57 peyre systemd[1]: Reached target Sound Card.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.5766] wifi-nl80211: (wlan0): using nl80211 for WiFi device control
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.5768] device (wlan0): driver supports Access Point (AP) mode
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.5775] manager: (wlan0): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/3)
Apr  3 19:41:57 peyre NetworkManager[733]: <warn>  [1585968117.5780] Error: failed to open /run/network/ifstate
Apr  3 19:41:57 peyre kernel: [    4.788308] r8169 0000:03:00.0 enp3s0: Link is Down
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for kde-frameworks-5-core18, revision 32.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.5920] modem-manager: ModemManager available
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.5920] supplicant: wpa_supplicant running
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for gnome-3-28-1804, revision 116.
Apr  3 19:41:57 peyre systemd-udevd[404]: link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
Apr  3 19:41:57 peyre kernel: [    4.824106] ath9k 0000:04:00.0 wlp4s0: renamed from wlan0
Apr  3 19:41:57 peyre systemd[1]: Started Load/Save RF Kill Switch Status.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.6341] devices added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/wlp4s0, iface: wlp4s0)
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.6341] device added (path: /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/wlp4s0, iface: wlp4s0): no ifupdown configuration found.
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.6343] device (wlp4s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for solitaire, revision 2.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for gedit, revision 371.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for chromium, revision 1071.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for core, revision 8689.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for gtk2-common-themes, revision 5.
Apr  3 19:41:57 peyre systemd[1]: Mounted Mount unit for core, revision 8935.
Apr  3 19:41:57 peyre systemd[1]: Starting Snappy daemon...
Apr  3 19:41:57 peyre kernel: [    4.903466] intel_rapl_common: Found RAPL domain package
Apr  3 19:41:57 peyre kernel: [    4.903467] intel_rapl_common: Found RAPL domain core
Apr  3 19:41:57 peyre kernel: [    4.903468] intel_rapl_common: Found RAPL domain uncore
Apr  3 19:41:57 peyre kernel: [    4.903468] intel_rapl_common: Found RAPL domain dram
Apr  3 19:41:57 peyre kernel: [    4.903470] intel_rapl_common: RAPL package-0 domain package locked by BIOS
Apr  3 19:41:57 peyre kernel: [    4.903474] intel_rapl_common: RAPL package-0 domain dram locked by BIOS
Apr  3 19:41:57 peyre wpa_supplicant[744]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed
Apr  3 19:41:57 peyre wpa_supplicant[744]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Apr  3 19:41:57 peyre wpa_supplicant[744]: dbus: Failed to construct signal
Apr  3 19:41:57 peyre wpa_supplicant[744]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.7214] device (wlp4s0): supplicant interface state: starting -> ready
Apr  3 19:41:57 peyre NetworkManager[733]: <info>  [1585968117.7215] device (wlp4s0): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-state: 'managed')
Apr  3 19:41:57 peyre kernel: [    4.958134] EXT4-fs (sdb1): recovery complete
Apr  3 19:41:57 peyre snapd[1072]: AppArmor status: apparmor is enabled and all features are available
Apr  3 19:41:57 peyre systemd[1]: Mounted /mnt/Storage.
Apr  3 19:41:57 peyre kernel: [    4.993661] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Apr  3 19:41:57 peyre systemd[1]: Started Disk Manager.
Apr  3 19:41:57 peyre udisksd[751]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Apr  3 19:41:58 peyre snapd[1072]: AppArmor status: apparmor is enabled and all features are available
Apr  3 19:41:58 peyre snapd[1072]: daemon.go:343: started snapd/2.44.1 (series 16; classic) ubuntu/18.04 (amd64) linux/5.3.0-45-generic.
Apr  3 19:41:58 peyre snapd[1072]: daemon.go:436: adjusting startup timeout by 1m40s (pessimistic estimate of 30s plus 5s per snap)
Apr  3 19:41:58 peyre avahi-daemon[741]: Server startup complete. Host name is peyre.local. Local service cookie is 1323571080.
Apr  3 19:41:58 peyre systemd[1]: Started Snappy daemon.
Apr  3 19:41:58 peyre systemd[1]: Starting Wait until snapd is fully seeded...
Apr  3 19:41:58 peyre systemd[1]: Created slice User Slice of lightdm.
Apr  3 19:41:58 peyre systemd[1]: Starting User Manager for UID 110...
Apr  3 19:41:58 peyre systemd[1]: Started Session c1 of user lightdm.
Apr  3 19:41:58 peyre systemd[1168]: Reached target Paths.
Apr  3 19:41:58 peyre systemd[1168]: Listening on GnuPG cryptographic agent and passphrase cache (restricted).
Apr  3 19:41:58 peyre systemd[1168]: Starting D-Bus User Message Bus Socket.
Apr  3 19:41:58 peyre systemd[1168]: Listening on GnuPG network certificate management daemon.
Apr  3 19:41:58 peyre systemd[1168]: Listening on GnuPG cryptographic agent and passphrase cache (access for web browsers).
Apr  3 19:41:58 peyre systemd[1168]: Listening on GnuPG cryptographic agent and passphrase cache.
Apr  3 19:41:58 peyre systemd[1168]: Reached target Timers.
Apr  3 19:41:58 peyre systemd[1168]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
Apr  3 19:41:58 peyre systemd[1168]: Listening on REST API socket for snapd user session agent.
Apr  3 19:41:58 peyre systemd[1168]: Listening on D-Bus User Message Bus Socket.
Apr  3 19:41:58 peyre systemd[1168]: Reached target Sockets.
Apr  3 19:41:58 peyre systemd[1168]: Reached target Basic System.
Apr  3 19:41:58 peyre systemd[1]: Started User Manager for UID 110.
Apr  3 19:41:58 peyre systemd[1168]: Reached target Default.
Apr  3 19:41:58 peyre systemd[1168]: Startup finished in 44ms.
Apr  3 19:41:58 peyre systemd[1168]: Started D-Bus User Message Bus.
Apr  3 19:41:58 peyre dbus-daemon[1193]: [session uid=110 pid=1193] AppArmor D-Bus mediation is enabled
Apr  3 19:41:58 peyre dbus-daemon[1193]: [session uid=110 pid=1193] Activating via systemd: service name='org.a11y.Bus' unit='at-spi-dbus-bus.service' requested by ':1.1' (uid=110 pid=1186 comm="/usr/sbin/lightdm-gtk-greeter " label="unconfined")
Apr  3 19:41:58 peyre systemd[1168]: Starting Accessibility services bus...
Apr  3 19:41:58 peyre dbus-daemon[1193]: [session uid=110 pid=1193] Successfully activated service 'org.a11y.Bus'
Apr  3 19:41:58 peyre systemd[1168]: Started Accessibility services bus.
Apr  3 19:41:58 peyre at-spi-bus-launcher[1194]: dbus-daemon[1199]: Activating service name='org.a11y.atspi.Registry' requested by ':1.0' (uid=110 pid=1186 comm="/usr/sbin/lightdm-gtk-greeter " label="unconfined")
Apr  3 19:41:58 peyre dbus-daemon[1193]: [session uid=110 pid=1193] Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service' requested by ':1.3' (uid=110 pid=1186 comm="/usr/sbin/lightdm-gtk-greeter " label="unconfined")
Apr  3 19:41:58 peyre systemd[1168]: Starting Virtual filesystem service...
Apr  3 19:41:58 peyre at-spi-bus-launcher[1194]: dbus-daemon[1199]: Successfully activated service 'org.a11y.atspi.Registry'
Apr  3 19:41:58 peyre at-spi-bus-launcher[1194]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Apr  3 19:41:58 peyre dbus-daemon[1193]: [session uid=110 pid=1193] Successfully activated service 'org.gtk.vfs.Daemon'
Apr  3 19:41:58 peyre systemd[1168]: Started Virtual filesystem service.
Apr  3 19:41:58 peyre systemd[1]: Started Wait until snapd is fully seeded.
Apr  3 19:41:59 peyre ModemManager[735]: <info>  Couldn't check support for device '/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0': not supported by any plugin
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.0719] device (enp3s0): carrier: link connected
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.0722] device (enp3s0): state change: unavailable -> disconnected (reason 'carrier-changed', sys-iface-state: 'managed')
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.0726] policy: auto-activating connection 'Wired connection 1'
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.0734] device (enp3s0): Activation: starting connection 'Wired connection 1' (b3aa4745-a3e7-3d91-aa0a-cc004a8e3726)
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.0736] device (enp3s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.0737] manager: NetworkManager state is now CONNECTING
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.0739] device (enp3s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.0742] device (enp3s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Apr  3 19:42:00 peyre kernel: [    7.284265] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control off
Apr  3 19:42:00 peyre kernel: [    7.284274] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.0748] dhcp4 (enp3s0): activation: beginning transaction (timeout in 45 seconds)
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.0785] dhcp4 (enp3s0): dhclient started with pid 1247
Apr  3 19:42:00 peyre avahi-daemon[741]: Joining mDNS multicast group on interface enp3s0.IPv6 with address fe80::c045:43cb:9917:dec4.
Apr  3 19:42:00 peyre avahi-daemon[741]: New relevant interface enp3s0.IPv6 for mDNS.
Apr  3 19:42:00 peyre avahi-daemon[741]: Registering new address record for fe80::c045:43cb:9917:dec4 on enp3s0.*.
Apr  3 19:42:00 peyre dhclient[1247]: DHCPREQUEST of 192.168.1.76 on enp3s0 to 255.255.255.255 port 67 (xid=0x22f24082)
Apr  3 19:42:00 peyre dhclient[1247]: DHCPACK of 192.168.1.76 from 192.168.1.254
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1083] dhcp4 (enp3s0):   address 192.168.1.76
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1083] dhcp4 (enp3s0):   plen 24 (255.255.255.0)
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1083] dhcp4 (enp3s0):   gateway 192.168.1.254
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1083] dhcp4 (enp3s0):   lease time 86400
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1083] dhcp4 (enp3s0):   nameserver '192.168.1.254'
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1083] dhcp4 (enp3s0):   domain name 'attlocal.net'
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1083] dhcp4 (enp3s0): state changed unknown -> bound
Apr  3 19:42:00 peyre avahi-daemon[741]: Joining mDNS multicast group on interface enp3s0.IPv4 with address 192.168.1.76.
Apr  3 19:42:00 peyre avahi-daemon[741]: New relevant interface enp3s0.IPv4 for mDNS.
Apr  3 19:42:00 peyre avahi-daemon[741]: Registering new address record for 192.168.1.76 on enp3s0.IPv4.
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1090] device (enp3s0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1096] device (enp3s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1097] device (enp3s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1098] manager: NetworkManager state is now CONNECTED_LOCAL
Apr  3 19:42:00 peyre dhclient[1247]: bound to 192.168.1.76 -- renewal in 36337 seconds.
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1133] manager: NetworkManager state is now CONNECTED_SITE
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1134] policy: set 'Wired connection 1' (enp3s0) as default for IPv4 routing and DNS
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1136] device (enp3s0): Activation: successful, device activated.
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1139] manager: startup complete
Apr  3 19:42:00 peyre NetworkManager[733]: <info>  [1585968120.1141] manager: NetworkManager state is now CONNECTED_GLOBAL
Apr  3 19:42:00 peyre nm-dispatcher: req:2 'up' [enp3s0]: new request (1 scripts)
Apr  3 19:42:00 peyre nm-dispatcher: req:2 'up' [enp3s0]: start running ordered scripts...
Apr  3 19:42:00 peyre nm-dispatcher: req:3 'connectivity-change': new request (1 scripts)
Apr  3 19:42:00 peyre systemd[1]: Started Network Manager Wait Online.
Apr  3 19:42:00 peyre systemd[1]: Reached target Network is Online.
Apr  3 19:42:00 peyre systemd[1]: Starting Tool to automatically collect and submit kernel crash signatures...
Apr  3 19:42:00 peyre systemd[1]: Starting LSB: disk temperature monitoring daemon...
Apr  3 19:42:00 peyre systemd[1]: Starting Samba NMB Daemon...
Apr  3 19:42:00 peyre systemd[1]: Started crash report submission daemon.
Apr  3 19:42:00 peyre systemd[1]: kerneloops.service: Found left-over process 1268 (kerneloops) in control group while starting unit. Ignoring.
Apr  3 19:42:00 peyre systemd[1]: This usually indicates unclean termination of a previous run, or service implementation deficiencies.
Apr  3 19:42:00 peyre systemd[1]: Started LSB: disk temperature monitoring daemon.
Apr  3 19:42:00 peyre systemd[1]: Started Tool to automatically collect and submit kernel crash signatures.
Apr  3 19:42:00 peyre whoopsie[1265]: [19:42:00] Using lock path: /var/lock/whoopsie/lock
Apr  3 19:42:00 peyre ModemManager[735]: <info>  Couldn't check support for device '/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0': not supported by any plugin
Apr  3 19:42:00 peyre whoopsie[1265]: [19:42:00] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Apr  3 19:42:00 peyre whoopsie[1265]: [19:42:00] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Apr  3 19:42:00 peyre whoopsie[1265]: [19:42:00] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Apr  3 19:42:00 peyre systemd[1]: Started Samba NMB Daemon.
Apr  3 19:42:00 peyre systemd[1]: Starting Samba SMB Daemon...
Apr  3 19:42:00 peyre avahi-daemon[741]: Got SIGTERM, quitting.
Apr  3 19:42:00 peyre systemd[1]: Stopping Avahi mDNS/DNS-SD Stack...
Apr  3 19:42:00 peyre avahi-daemon[741]: Leaving mDNS multicast group on interface enp3s0.IPv6 with address fe80::c045:43cb:9917:dec4.
Apr  3 19:42:00 peyre avahi-daemon[741]: Leaving mDNS multicast group on interface enp3s0.IPv4 with address 192.168.1.76.
Apr  3 19:42:00 peyre avahi-daemon[741]: Leaving mDNS multicast group on interface lo.IPv6 with address ::1.
Apr  3 19:42:00 peyre avahi-daemon[741]: Leaving mDNS multicast group on interface lo.IPv4 with address 127.0.0.1.
Apr  3 19:42:00 peyre dbus-daemon[721]: [system] Activating via systemd: service name='org.freedesktop.Avahi' unit='dbus-org.freedesktop.Avahi.service' requested by ':1.33' (uid=0 pid=820 comm="/usr/sbin/cups-browsed " label="/usr/sbin/cups-browsed (enforce)")
Apr  3 19:42:00 peyre nm-dispatcher[867]: Job for avahi-daemon.service canceled.
Apr  3 19:42:00 peyre nm-dispatcher[867]: Job for avahi-daemon.socket canceled.
Apr  3 19:42:00 peyre avahi: Avahi detected that your currently configured local DNS server serves
Apr  3 19:42:00 peyre avahi: a domain .local. This is inherently incompatible with Avahi and thus
Apr  3 19:42:00 peyre avahi: Avahi stopped itself. If you want to use Avahi in this network, please
Apr  3 19:42:00 peyre avahi: contact your administrator and convince him to use a different DNS domain,
Apr  3 19:42:00 peyre avahi: since .local should be used exclusively for Zeroconf technology.
Apr  3 19:42:00 peyre avahi: For more information, see [http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)
Apr  3 19:42:00 peyre avahi-daemon[741]: avahi-daemon 0.7 exiting.
Apr  3 19:42:00 peyre systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Apr  3 19:42:00 peyre avahi-daemon[1313]: Process 741 died: No such process; trying to remove PID file. (/run/avahi-daemon//pid)
Apr  3 19:42:00 peyre avahi-daemon[1313]: Found user 'avahi' (UID 117) and group 'avahi' (GID 124).
Apr  3 19:42:00 peyre avahi-daemon[1313]: Successfully dropped root privileges.
Apr  3 19:42:00 peyre avahi-daemon[1313]: avahi-daemon 0.7 starting up.
Apr  3 19:42:00 peyre dbus-daemon[721]: [system] Successfully activated service 'org.freedesktop.Avahi'
Apr  3 19:42:00 peyre systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Apr  3 19:42:00 peyre avahi-daemon[1313]: Successfully called chroot().
Apr  3 19:42:00 peyre avahi-daemon[1313]: Successfully dropped remaining capabilities.
Apr  3 19:42:00 peyre avahi-daemon[1313]: No service file found in /etc/avahi/services.
Apr  3 19:42:00 peyre avahi-daemon[1313]: Joining mDNS multicast group on interface enp3s0.IPv6 with address fe80::c045:43cb:9917:dec4.
Apr  3 19:42:00 peyre avahi-daemon[1313]: New relevant interface enp3s0.IPv6 for mDNS.
Apr  3 19:42:00 peyre avahi-daemon[1313]: Joining mDNS multicast group on interface enp3s0.IPv4 with address 192.168.1.76.
Apr  3 19:42:00 peyre avahi-daemon[1313]: New relevant interface enp3s0.IPv4 for mDNS.
Apr  3 19:42:00 peyre avahi-daemon[1313]: Joining mDNS multicast group on interface lo.IPv6 with address ::1.
Apr  3 19:42:00 peyre avahi-daemon[1313]: New relevant interface lo.IPv6 for mDNS.
Apr  3 19:42:00 peyre avahi-daemon[1313]: Joining mDNS multicast group on interface lo.IPv4 with address 127.0.0.1.
Apr  3 19:42:00 peyre avahi-daemon[1313]: New relevant interface lo.IPv4 for mDNS.
Apr  3 19:42:00 peyre avahi-daemon[1313]: Network interface enumeration completed.
Apr  3 19:42:00 peyre avahi-daemon[1313]: Registering new address record for fe80::c045:43cb:9917:dec4 on enp3s0.*.
Apr  3 19:42:00 peyre avahi-daemon[1313]: Registering new address record for 192.168.1.76 on enp3s0.IPv4.
Apr  3 19:42:00 peyre avahi-daemon[1313]: Registering new address record for ::1 on lo.*.
Apr  3 19:42:00 peyre avahi-daemon[1313]: Registering new address record for 127.0.0.1 on lo.IPv4.
Apr  3 19:42:00 peyre nm-dispatcher: req:3 'connectivity-change': start running ordered scripts...
Apr  3 19:42:00 peyre systemd[1]: Started Samba SMB Daemon.
Apr  3 19:42:00 peyre systemd[1]: Reached target Multi-User System.
Apr  3 19:42:00 peyre systemd[1]: Reached target Graphical Interface.
Apr  3 19:42:00 peyre systemd[1]: Starting Update UTMP about System Runlevel Changes...
Apr  3 19:42:00 peyre systemd[1]: Started Stop ureadahead data collection 45s after completed startup.
Apr  3 19:42:00 peyre systemd[1]: Started Update UTMP about System Runlevel Changes.
Apr  3 19:42:00 peyre systemd[1]: Startup finished in 3.538s (kernel) + 3.937s (userspace) = 7.475s.
Apr  3 19:42:00 peyre set-cpufreq[739]: Setting powersave scheduler for all CPUs
Apr  3 19:42:01 peyre avahi-daemon[1313]: Server startup complete. Host name is peyre.local. Local service cookie is 732577996.
Apr  3 19:42:01 peyre avahi-daemon[1313]: Leaving mDNS multicast group on interface enp3s0.IPv6 with address fe80::c045:43cb:9917:dec4.
Apr  3 19:42:01 peyre avahi-daemon[1313]: Joining mDNS multicast group on interface enp3s0.IPv6 with address 2600:1702:3651:2910:a21:b2d3:76a5:7cb8.
Apr  3 19:42:01 peyre avahi-daemon[1313]: Registering new address record for 2600:1702:3651:2910:a21:b2d3:76a5:7cb8 on enp3s0.*.
Apr  3 19:42:01 peyre avahi-daemon[1313]: Withdrawing address record for fe80::c045:43cb:9917:dec4 on enp3s0.
Apr  3 19:42:01 peyre NetworkManager[733]: <info>  [1585968121.9296] policy: set 'Wired connection 1' (enp3s0) as default for IPv6 routing and DNS
Apr  3 19:42:02 peyre kernel: [    9.664677] usb 3-10: New USB device found, idVendor=0cf3, idProduct=0036, bcdDevice= 0.02
Apr  3 19:42:02 peyre kernel: [    9.664679] usb 3-10: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Apr  3 19:42:02 peyre systemd[1]: Starting Bluetooth service...
Apr  3 19:42:02 peyre bluetoothd[1355]: Bluetooth daemon 5.48
Apr  3 19:42:02 peyre systemd[1]: Started Bluetooth service.
Apr  3 19:42:02 peyre systemd[1]: Reached target Bluetooth.
Apr  3 19:42:02 peyre bluetoothd[1355]: Starting SDP server
Apr  3 19:42:02 peyre kernel: [    9.700225] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  3 19:42:02 peyre kernel: [    9.700226] Bluetooth: BNEP filters: protocol multicast
Apr  3 19:42:02 peyre kernel: [    9.700229] Bluetooth: BNEP socket layer initialized
Apr  3 19:42:02 peyre bluetoothd[1355]: Bluetooth management interface 1.14 initialized
Apr  3 19:42:02 peyre NetworkManager[733]: <info>  [1585968122.4935] bluez: use BlueZ version 5
Apr  3 19:42:02 peyre colord-sane: [bjnp] create_broadcast_socket: ERROR - bind socket to local address failed - Cannot assign requested address
Apr  3 19:42:02 peyre colord-sane: [bjnp] create_broadcast_socket: ERROR - bind socket to local address failed - Cannot assign requested address
Apr  3 19:42:02 peyre NetworkManager[733]: <info>  [1585968122.5515] bluez5: NAP: added interface 18:4F:32:68:D6:7C
Apr  3 19:42:03 peyre avahi-daemon[1313]: Registering new address record for 2600:1702:3651:2910:2556:c28d:5bdd:8d47 on enp3s0.*.
Apr  3 19:42:04 peyre systemd[1]: session-c1.scope: Killing process 1127 (lightdm) with signal SIGTERM.
Apr  3 19:42:04 peyre systemd[1]: session-c1.scope: Killing process 1182 (gnome-keyring-d) with signal SIGTERM.
Apr  3 19:42:04 peyre systemd[1]: session-c1.scope: Killing process 1185 (lightdm-greeter) with signal SIGTERM.
Apr  3 19:42:04 peyre systemd[1]: session-c1.scope: Killing process 1186 (lightdm-gtk-gre) with signal SIGTERM.
Apr  3 19:42:04 peyre systemd[1]: Stopping Session c1 of user lightdm.
Apr  3 19:42:04 peyre systemd[1]: Created slice User Slice of leon.
Apr  3 19:42:04 peyre systemd[1]: Starting User Manager for UID 1000...
Apr  3 19:42:04 peyre systemd[1]: Started Session c2 of user leon.
Apr  3 19:42:04 peyre systemd[1]: Stopped Session c1 of user lightdm.
Apr  3 19:42:04 peyre systemd[1]: Stopping User Manager for UID 110...
Apr  3 19:42:04 peyre systemd[1168]: Stopped target Default.
Apr  3 19:42:04 peyre systemd[1168]: Stopping Accessibility services bus...
Apr  3 19:42:04 peyre systemd[1168]: Stopping Virtual filesystem service...
Apr  3 19:42:04 peyre systemd[1168]: Stopping D-Bus User Message Bus...
Apr  3 19:42:04 peyre systemd[1168]: Stopped Virtual filesystem service.
Apr  3 19:42:04 peyre systemd[1168]: Stopped D-Bus User Message Bus.
Apr  3 19:42:04 peyre systemd[1423]: Listening on GnuPG network certificate management daemon.
Apr  3 19:42:04 peyre kernel: [   11.982615] systemd-journald[356]: File /var/log/journal/f8f447cc20ed4be580bd0cdb953799c9/user-1000.journal corrupted or uncleanly shut down, renaming and replacing.
Apr  3 19:42:04 peyre systemd[1423]: Reached target Timers.
Apr  3 19:42:04 peyre systemd[1423]: Reached target Paths.
Apr  3 19:42:04 peyre systemd[1423]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
Apr  3 19:42:04 peyre systemd[1423]: Listening on GnuPG cryptographic agent and passphrase cache (restricted).
Apr  3 19:42:04 peyre systemd[1423]: Listening on GnuPG cryptographic agent and passphrase cache.
Apr  3 19:42:04 peyre systemd[1423]: Listening on REST API socket for snapd user session agent.
Apr  3 19:42:04 peyre systemd[1423]: Listening on GnuPG cryptographic agent and passphrase cache (access for web browsers).
Apr  3 19:42:04 peyre systemd[1423]: Starting D-Bus User Message Bus Socket.
Apr  3 19:42:04 peyre systemd[1423]: Listening on D-Bus User Message Bus Socket.
Apr  3 19:42:04 peyre systemd[1423]: Reached target Sockets.
Apr  3 19:42:04 peyre systemd[1423]: Reached target Basic System.
Apr  3 19:42:04 peyre systemd[1423]: Reached target Default.
Apr  3 19:42:04 peyre systemd[1423]: Startup finished in 33ms.
Apr  3 19:42:04 peyre systemd[1]: Started User Manager for UID 1000.
Apr  3 19:42:04 peyre systemd[1168]: Stopped Accessibility services bus.
Apr  3 19:42:04 peyre systemd[1168]: Stopped target Basic System.
Apr  3 19:42:04 peyre systemd[1168]: Stopped target Paths.
Apr  3 19:42:04 peyre systemd[1168]: Stopped target Timers.
Apr  3 19:42:04 peyre systemd[1168]: Stopped target Sockets.
Apr  3 19:42:04 peyre systemd[1168]: Closed D-Bus User Message Bus Socket.
Apr  3 19:42:04 peyre systemd[1168]: Closed GnuPG network certificate management daemon.
Apr  3 19:42:04 peyre systemd[1168]: Closed GnuPG cryptographic agent and passphrase cache.
Apr  3 19:42:04 peyre systemd[1168]: Closed GnuPG cryptographic agent and passphrase cache (restricted).
Apr  3 19:42:04 peyre systemd[1168]: Closed GnuPG cryptographic agent and passphrase cache (access for web browsers).
Apr  3 19:42:04 peyre systemd[1168]: Closed GnuPG cryptographic agent (ssh-agent emulation).
Apr  3 19:42:04 peyre systemd[1168]: Closed REST API socket for snapd user session agent.
Apr  3 19:42:04 peyre systemd[1168]: Reached target Shutdown.
Apr  3 19:42:04 peyre systemd[1168]: Starting Exit the Session...
Apr  3 19:42:04 peyre systemd[1168]: Received SIGRTMIN+24 from PID 1438 (kill).
Apr  3 19:42:04 peyre systemd[1]: Stopped User Manager for UID 110.
Apr  3 19:42:04 peyre systemd[1]: Removed slice User Slice of lightdm.
Apr  3 19:42:04 peyre systemd[1423]: Started D-Bus User Message Bus.
Apr  3 19:42:04 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] AppArmor D-Bus mediation is enabled
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating service name='org.xfce.Xfconf' requested by ':1.4' (uid=1000 pid=1543 comm="xfce4-session " label="unconfined")
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.xfce.Xfconf'
Apr  3 19:42:05 peyre dbus-daemon[721]: [system] Activating via systemd: service name='org.freedesktop.UPower' unit='upower.service' requested by ':1.50' (uid=1000 pid=1558 comm="xfsettingsd --display :0.0 --sm-client-id 2cc6d1c6" label="unconfined")
Apr  3 19:42:05 peyre systemd[1]: Starting Daemon for power management...
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service' requested by ':1.13' (uid=1000 pid=1560 comm="xfdesktop --display :0.0 --sm-client-id 29565e4be-" label="unconfined")
Apr  3 19:42:05 peyre systemd[1423]: Starting Virtual filesystem service...
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating via systemd: service name='org.a11y.Bus' unit='at-spi-dbus-bus.service' requested by ':1.16' (uid=1000 pid=1580 comm="/usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0 " label="unconfined")
Apr  3 19:42:05 peyre systemd[1423]: Starting Accessibility services bus...
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.gtk.vfs.Daemon'
Apr  3 19:42:05 peyre systemd[1423]: Started Virtual filesystem service.
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating service name='org.freedesktop.thumbnails.Thumbnailer1' requested by ':1.14' (uid=1000 pid=1560 comm="xfdesktop --display :0.0 --sm-client-id 29565e4be-" label="unconfined")
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.a11y.Bus'
Apr  3 19:42:05 peyre systemd[1423]: Started Accessibility services bus.
Apr  3 19:42:05 peyre at-spi-bus-launcher[1595]: dbus-daemon[1612]: Activating service name='org.a11y.atspi.Registry' requested by ':1.0' (uid=1000 pid=1580 comm="/usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0 " label="unconfined")
Apr  3 19:42:05 peyre at-spi-bus-launcher[1595]: dbus-daemon[1612]: Successfully activated service 'org.a11y.atspi.Registry'
Apr  3 19:42:05 peyre at-spi-bus-launcher[1595]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating via systemd: service name='org.gtk.vfs.UDisks2VolumeMonitor' unit='gvfs-udisks2-volume-monitor.service' requested by ':1.22' (uid=1000 pid=1583 comm="/usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 " label="unconfined")
Apr  3 19:42:05 peyre systemd[1423]: Starting Virtual filesystem service - disk device monitor...
Apr  3 19:42:05 peyre org.freedesktop.thumbnails.Thumbnailer1[1458]: Registered thumbailer atril-thumbnailer -s %s %u %o
Apr  3 19:42:05 peyre org.freedesktop.thumbnails.Thumbnailer1[1458]: Registered thumbailer gnome-thumbnail-font --size %s %u %o
Apr  3 19:42:05 peyre org.freedesktop.thumbnails.Thumbnailer1[1458]: Registered thumbailer /usr/bin/gdk-pixbuf-thumbnailer -s %s %u %o
Apr  3 19:42:05 peyre org.freedesktop.thumbnails.Thumbnailer1[1458]: Registered thumbailer /usr/bin/gdk-pixbuf-thumbnailer -s %s %u %o
Apr  3 19:42:05 peyre dbus-daemon[721]: [system] Successfully activated service 'org.freedesktop.UPower'
Apr  3 19:42:05 peyre systemd[1]: Started Daemon for power management.
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.gtk.vfs.UDisks2VolumeMonitor'
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating via systemd: service name='org.gtk.vfs.MTPVolumeMonitor' unit='gvfs-mtp-volume-monitor.service' requested by ':1.22' (uid=1000 pid=1583 comm="/usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 " label="unconfined")
Apr  3 19:42:05 peyre systemd[1423]: Started Virtual filesystem service - disk device monitor.
Apr  3 19:42:05 peyre systemd[1423]: Starting Virtual filesystem service - Media Transfer Protocol monitor...
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.gtk.vfs.MTPVolumeMonitor'
Apr  3 19:42:05 peyre systemd[1423]: Started Virtual filesystem service - Media Transfer Protocol monitor.
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating via systemd: service name='org.freedesktop.Notifications' unit='xfce4-notifyd.service' requested by ':1.27' (uid=1000 pid=1634 comm="xfce4-power-manager --restart --sm-client-id 21888" label="unconfined")
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating via systemd: service name='org.gtk.vfs.GPhoto2VolumeMonitor' unit='gvfs-gphoto2-volume-monitor.service' requested by ':1.22' (uid=1000 pid=1583 comm="/usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 " label="unconfined")
Apr  3 19:42:05 peyre systemd[1423]: Starting Virtual filesystem service - digital camera monitor...
Apr  3 19:42:05 peyre systemd[1423]: Starting XFCE notifications service...
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.gtk.vfs.GPhoto2VolumeMonitor'
Apr  3 19:42:05 peyre systemd[1423]: Started Virtual filesystem service - digital camera monitor.
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating via systemd: service name='org.gtk.vfs.GoaVolumeMonitor' unit='gvfs-goa-volume-monitor.service' requested by ':1.22' (uid=1000 pid=1583 comm="/usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 " label="unconfined")
Apr  3 19:42:05 peyre systemd[1423]: Starting Virtual filesystem service - GNOME Online Accounts monitor...
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.gtk.vfs.GoaVolumeMonitor'
Apr  3 19:42:05 peyre systemd[1423]: Started Virtual filesystem service - GNOME Online Accounts monitor.
Apr  3 19:42:05 peyre systemd[1423]: Started Indicator Messages Service.
Apr  3 19:42:05 peyre systemd[1423]: Reached target Target to start indicators for the xfce4-indicator-plugin.
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating via systemd: service name='org.gtk.vfs.AfcVolumeMonitor' unit='gvfs-afc-volume-monitor.service' requested by ':1.22' (uid=1000 pid=1583 comm="/usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 " label="unconfined")
Apr  3 19:42:05 peyre systemd[1423]: Starting Virtual filesystem service - Apple File Conduit monitor...
Apr  3 19:42:05 peyre gvfs-afc-volume-monitor[1683]: Volume monitor alive
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.gtk.vfs.AfcVolumeMonitor'
Apr  3 19:42:05 peyre systemd[1423]: Started Virtual filesystem service - Apple File Conduit monitor.
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.freedesktop.Notifications'
Apr  3 19:42:05 peyre systemd[1423]: Started XFCE notifications service.
Apr  3 19:42:05 peyre kernel: [   13.011022] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv84_xuc00f failed with error -2
Apr  3 19:42:05 peyre kernel: [   13.011024] nouveau 0000:01:00.0: vp: unable to load firmware nouveau/nv84_xuc00f
Apr  3 19:42:05 peyre kernel: [   13.011026] nouveau 0000:01:00.0: vp: init failed, -2
Apr  3 19:42:05 peyre kernel: [   13.011048] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv84_xuc103 failed with error -2
Apr  3 19:42:05 peyre kernel: [   13.011050] nouveau 0000:01:00.0: bsp: unable to load firmware nouveau/nv84_xuc103
Apr  3 19:42:05 peyre kernel: [   13.011050] nouveau 0000:01:00.0: bsp: init failed, -2
Apr  3 19:42:05 peyre dbus-daemon[721]: [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service' requested by ':1.56' (uid=1000 pid=1705 comm="/usr/bin/pulseaudio --start --log-target=syslog " label="unconfined")
Apr  3 19:42:05 peyre systemd[1]: Starting RealtimeKit Scheduling Policy Service...
Apr  3 19:42:05 peyre dbus-daemon[721]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Apr  3 19:42:05 peyre systemd[1]: Started RealtimeKit Scheduling Policy Service.
Apr  3 19:42:05 peyre rtkit-daemon[1706]: Successfully called chroot.
Apr  3 19:42:05 peyre rtkit-daemon[1706]: Successfully dropped privileges.
Apr  3 19:42:05 peyre rtkit-daemon[1706]: Successfully limited resources.
Apr  3 19:42:05 peyre rtkit-daemon[1706]: Running.
Apr  3 19:42:05 peyre rtkit-daemon[1706]: Watchdog thread running.
Apr  3 19:42:05 peyre rtkit-daemon[1706]: Canary thread running.
Apr  3 19:42:05 peyre rtkit-daemon[1706]: Successfully made thread 1705 of process 1705 (n/a) owned by '1000' high priority at nice level -11.
Apr  3 19:42:05 peyre rtkit-daemon[1706]: Supervising 1 threads of 1 processes of 1 users.
Apr  3 19:42:05 peyre spice-vdagent[1721]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.freedesktop.thumbnails.Thumbnailer1'
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating via systemd: service name='org.gtk.vfs.Metadata' unit='gvfs-metadata.service' requested by ':1.13' (uid=1000 pid=1560 comm="xfdesktop --display :0.0 --sm-client-id 29565e4be-" label="unconfined")
Apr  3 19:42:05 peyre systemd[1423]: Starting Virtual filesystem metadata service...
Apr  3 19:42:05 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.gtk.vfs.Metadata'
Apr  3 19:42:05 peyre systemd[1423]: Started Virtual filesystem metadata service.
Apr  3 19:42:06 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating service name='ca.desrt.dconf' requested by ':1.63' (uid=1000 pid=1757 comm="light-locker " label="unconfined")
Apr  3 19:42:06 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'ca.desrt.dconf'
Apr  3 19:42:06 peyre rtkit-daemon[1706]: Supervising 1 threads of 1 processes of 1 users.
Apr  3 19:42:06 peyre rtkit-daemon[1706]: Successfully made thread 1805 of process 1705 (n/a) owned by '1000' RT at priority 5.
Apr  3 19:42:06 peyre rtkit-daemon[1706]: Supervising 2 threads of 1 processes of 1 users.
Apr  3 19:42:06 peyre rtkit-daemon[1706]: Supervising 2 threads of 1 processes of 1 users.
Apr  3 19:42:06 peyre rtkit-daemon[1706]: Successfully made thread 1806 of process 1705 (n/a) owned by '1000' RT at priority 5.
Apr  3 19:42:06 peyre rtkit-daemon[1706]: Supervising 3 threads of 1 processes of 1 users.
Apr  3 19:42:06 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Activating via systemd: service name='org.bluez.obex' unit='dbus-org.bluez.obex.service' requested by ':1.68' (uid=1000 pid=1719 comm="/usr/bin/python3 /usr/bin/blueman-applet " label="unconfined")
Apr  3 19:42:06 peyre systemd[1423]: Starting Bluetooth OBEX service...
Apr  3 19:42:06 peyre obexd[1807]: OBEX daemon 5.48
Apr  3 19:42:06 peyre dbus-daemon[1458]: [session uid=1000 pid=1458] Successfully activated service 'org.bluez.obex'
Apr  3 19:42:06 peyre systemd[1423]: Started Bluetooth OBEX service.
Apr  3 19:42:06 peyre pulseaudio[1705]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Apr  3 19:42:06 peyre rtkit-daemon[1706]: Successfully made thread 1812 of process 1812 (n/a) owned by '1000' high priority at nice level -11.
Apr  3 19:42:06 peyre rtkit-daemon[1706]: Supervising 4 threads of 2 processes of 1 users.
Apr  3 19:42:06 peyre pulseaudio[1812]: [pulseaudio] pid.c: Daemon already running.
Apr  3 19:42:06 peyre bluetoothd[1355]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSource
Apr  3 19:42:06 peyre bluetoothd[1355]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSink
Apr  3 19:42:06 peyre kernel: [   13.541577] Bluetooth: RFCOMM TTY layer initialized
Apr  3 19:42:06 peyre kernel: [   13.541582] Bluetooth: RFCOMM socket layer initialized
Apr  3 19:42:06 peyre kernel: [   13.541585] Bluetooth: RFCOMM ver 1.11
Apr  3 19:42:06 peyre dbus-daemon[721]: [system] Activating service name='org.blueman.Mechanism' requested by ':1.62' (uid=1000 pid=1719 comm="/usr/bin/python3 /usr/bin/blueman-applet " label="unconfined") (using servicehelper)
Apr  3 19:42:06 peyre org.blueman.Mechanism[721]: Unable to init server: Could not connect: Connection refused
Apr  3 19:42:06 peyre org.blueman.Mechanism[721]: Unable to init server: Could not connect: Connection refused
Apr  3 19:42:06 peyre blueman-mechanism: Starting blueman-mechanism
Apr  3 19:42:06 peyre dbus-daemon[721]: [system] Successfully activated service 'org.blueman.Mechanism'
Apr  3 19:42:06 peyre blueman-mechani[1817]: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Apr  3 19:42:06 peyre blueman-mechanism: loading RfKill
Apr  3 19:42:06 peyre blueman-mechanism: loading Rfcomm
Apr  3 19:42:06 peyre blueman-mechanism: loading Network
Apr  3 19:42:06 peyre blueman-mechanism: loading Ppp
Apr  3 19:42:09 peyre kernel: [   17.051628] usb 3-7: new high-speed USB device number 10 using xhci_hcd
Apr  3 19:42:09 peyre kernel: [   17.075012] usb 3-7: New USB device found, idVendor=0930, idProduct=6544, bcdDevice= 1.00
Apr  3 19:42:09 peyre kernel: [   17.075017] usb 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr  3 19:42:09 peyre kernel: [   17.075021] usb 3-7: Product: DataTraveler 2.0
Apr  3 19:42:09 peyre kernel: [   17.075024] usb 3-7: Manufacturer: Kingston
Apr  3 19:42:09 peyre kernel: [   17.075026] usb 3-7: SerialNumber: 001731807A84CE60193C386E
Apr  3 19:42:09 peyre kernel: [   17.079448] usb-storage 3-7:1.0: USB Mass Storage device detected
Apr  3 19:42:09 peyre kernel: [   17.080711] scsi host8: usb-storage 3-7:1.0
Apr  3 19:42:09 peyre mtp-probe: checking bus 3, device 10: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7"
Apr  3 19:42:09 peyre mtp-probe: bus: 3, device: 10 was not an MTP device
Apr  3 19:42:09 peyre upowerd[1565]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0
Apr  3 19:42:09 peyre upowerd[1565]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:14.0/usb3/3-7
Apr  3 19:42:10 peyre kernel: [   18.111412] scsi 8:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 4
Apr  3 19:42:10 peyre kernel: [   18.111976] sd 8:0:0:0: [sdf] 15148608 512-byte logical blocks: (7.76 GB/7.22 GiB)
Apr  3 19:42:10 peyre kernel: [   18.112159] sd 8:0:0:0: [sdf] Write Protect is off
Apr  3 19:42:10 peyre kernel: [   18.112160] sd 8:0:0:0: [sdf] Mode Sense: 45 00 00 00
Apr  3 19:42:10 peyre kernel: [   18.112167] sd 8:0:0:0: Attached scsi generic sg6 type 0
Apr  3 19:42:10 peyre kernel: [   18.112412] sd 8:0:0:0: [sdf] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  3 19:42:10 peyre kernel: [   18.113911]  sdf:
Apr  3 19:42:10 peyre kernel: [   18.115208] sd 8:0:0:0: [sdf] Attached SCSI removable disk
Apr  3 19:42:14 peyre systemd-resolved[519]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Apr  3 19:42:14 peyre systemd-resolved[519]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Apr  3 19:42:16 peyre systemd[1]: Created slice system-clean\x2dmount\x2dpoint.slice.
Apr  3 19:42:16 peyre systemd[1]: Started Clean the /media/leon/KINGSTON8GB mount point.
Apr  3 19:42:16 peyre udisksd[751]: Mounted /dev/sdf at /media/leon/KINGSTON8GB on behalf of uid 1000
Apr  3 19:42:22 peyre rtkit-daemon[1706]: Supervising 3 threads of 1 processes of 1 users.
Apr  3 19:42:22 peyre rtkit-daemon[1706]: message repeated 3 times: [ Supervising 3 threads of 1 processes of 1 users.]
Apr  3 19:42:22 peyre rtkit-daemon[1706]: Successfully made thread 2046 of process 1974 (n/a) owned by '1000' RT at priority 10.
Apr  3 19:42:22 peyre rtkit-daemon[1706]: Supervising 4 threads of 2 processes of 1 users.
Apr  3 19:42:26 peyre rtkit-daemon[1706]: message repeated 8 times: [ Supervising 4 threads of 2 processes of 1 users.]
Apr  3 19:42:27 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:42:27 peyre gvfsd-metadata[1732]: message repeated 7 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Apr  3 19:42:27 peyre systemd-timesyncd[522]: Synchronized to time server [2001:67c:1560:8003::c7]:123 (ntp.ubuntu.com).
Apr  3 19:42:27 peyre kernel: [   34.758984] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv84_xuc00f failed with error -2
Apr  3 19:42:27 peyre kernel: [   34.758987] nouveau 0000:01:00.0: vp: unable to load firmware nouveau/nv84_xuc00f
Apr  3 19:42:27 peyre kernel: [   34.758988] nouveau 0000:01:00.0: vp: init failed, -2
Apr  3 19:42:27 peyre kernel: [   34.759004] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv84_xuc103 failed with error -2
Apr  3 19:42:27 peyre kernel: [   34.759005] nouveau 0000:01:00.0: bsp: unable to load firmware nouveau/nv84_xuc103
Apr  3 19:42:27 peyre kernel: [   34.759005] nouveau 0000:01:00.0: bsp: init failed, -2
Apr  3 19:42:27 peyre kernel: [   34.842201] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv84_xuc00f failed with error -2
Apr  3 19:42:27 peyre kernel: [   34.842205] nouveau 0000:01:00.0: vp: unable to load firmware nouveau/nv84_xuc00f
Apr  3 19:42:27 peyre kernel: [   34.842206] nouveau 0000:01:00.0: vp: init failed, -2
Apr  3 19:42:27 peyre kernel: [   34.842221] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv84_xuc103 failed with error -2
Apr  3 19:42:27 peyre kernel: [   34.842222] nouveau 0000:01:00.0: bsp: unable to load firmware nouveau/nv84_xuc103
Apr  3 19:42:27 peyre kernel: [   34.842222] nouveau 0000:01:00.0: bsp: init failed, -2
Apr  3 19:42:27 peyre kernel: [   34.843598] nouveau 0000:01:00.0: gr: TRAP_PROP - TP 0 - 00001000 [RT_LINEAR_MISMATCH] - Address 0000000000
Apr  3 19:42:27 peyre kernel: [   34.843601] nouveau 0000:01:00.0: gr: TRAP_PROP - TP 0 - e0c: 00000000, e18: 00000000, e1c: 00100020, e20: 00001800, e24: 00220000
Apr  3 19:42:27 peyre kernel: [   34.843608] nouveau 0000:01:00.0: gr: TRAP_PROP - TP 1 - 00001000 [RT_LINEAR_MISMATCH] - Address 0000000000
Apr  3 19:42:27 peyre kernel: [   34.843609] nouveau 0000:01:00.0: gr: TRAP_PROP - TP 1 - e0c: 00000000, e18: 00000000, e1c: 00100030, e20: 00001800, e24: 00220000
Apr  3 19:42:27 peyre kernel: [   34.843615] nouveau 0000:01:00.0: gr: TRAP_PROP - TP 2 - 00001000 [RT_LINEAR_MISMATCH] - Address 0000000000
Apr  3 19:42:27 peyre kernel: [   34.843616] nouveau 0000:01:00.0: gr: TRAP_PROP - TP 2 - e0c: 00000000, e18: 00000000, e1c: 00000020, e20: 00001800, e24: 00220000
Apr  3 19:42:27 peyre kernel: [   34.843623] nouveau 0000:01:00.0: gr: TRAP_PROP - TP 3 - 00001000 [RT_LINEAR_MISMATCH] - Address 0000000000
Apr  3 19:42:27 peyre kernel: [   34.843624] nouveau 0000:01:00.0: gr: TRAP_PROP - TP 3 - e0c: 00000000, e18: 00000000, e1c: 00000030, e20: 00001800, e24: 00220000
Apr  3 19:42:27 peyre kernel: [   34.843626] nouveau 0000:01:00.0: gr: 00200000 [] ch 4 [001f6db000 Xorg[895]] subc 3 class 8297 mthd 1558 data 00000001
Apr  3 19:42:29 peyre rtkit-daemon[1706]: Supervising 4 threads of 2 processes of 1 users.
Apr  3 19:42:29 peyre rtkit-daemon[1706]: message repeated 3 times: [ Supervising 4 threads of 2 processes of 1 users.]
Apr  3 19:42:29 peyre rtkit-daemon[1706]: Successfully made thread 2317 of process 2166 (n/a) owned by '1000' RT at priority 10.
Apr  3 19:42:29 peyre rtkit-daemon[1706]: Supervising 5 threads of 3 processes of 1 users.
Apr  3 19:42:30 peyre systemd-resolved[519]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Apr  3 19:42:30 peyre systemd-resolved[519]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Apr  3 19:42:30 peyre rtkit-daemon[1706]: Supervising 5 threads of 3 processes of 1 users.
Apr  3 19:42:30 peyre rtkit-daemon[1706]: Supervising 5 threads of 3 processes of 1 users.
Apr  3 19:42:36 peyre blueman-mechanism: Exiting
Apr  3 19:42:45 peyre systemd[1]: Starting Stop ureadahead data collection...
Apr  3 19:42:45 peyre systemd[1]: Stopping Read required files in advance...
Apr  3 19:42:45 peyre systemd[1]: Started Stop ureadahead data collection.
Apr  3 19:42:46 peyre systemd[1]: Stopped Read required files in advance.
Apr  3 19:42:50 peyre systemd-resolved[519]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Apr  3 19:42:50 peyre systemd-resolved[519]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Apr  3 19:43:02 peyre systemd[1]: Reloading.
Apr  3 19:43:10 peyre systemd-resolved[519]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Apr  3 19:43:10 peyre systemd-resolved[519]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Apr  3 19:43:11 peyre systemd[1]: Reloading.
Apr  3 19:44:37 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:44:56 peyre kernel: [  183.627071] kauditd_printk_skb: 36 callbacks suppressed
Apr  3 19:44:56 peyre kernel: [  183.627072] audit: type=1400 audit(1585968296.266:47): apparmor="DENIED" operation="capable" profile="/snap/core/8935/usr/lib/snapd/snap-confine" pid=2682 comm="snap-confine" capability=4  capname="fsetid"
Apr  3 19:44:57 peyre kernel: [  185.287541] audit: type=1400 audit(1585968297.926:48): apparmor="DENIED" operation="open" profile="snap.gedit.gedit" name="/proc/2682/mountinfo" pid=2682 comm="gmain" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Apr  3 19:44:57 peyre kernel: [  185.287689] audit: type=1400 audit(1585968297.926:49): apparmor="DENIED" operation="open" profile="snap.gedit.gedit" name="/etc/fstab" pid=2682 comm="gedit" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Apr  3 19:44:57 peyre kernel: [  185.287690] audit: type=1400 audit(1585968297.926:50): apparmor="DENIED" operation="open" profile="snap.gedit.gedit" name="/proc/2682/mountinfo" pid=2682 comm="gedit" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Apr  3 19:44:57 peyre kernel: [  185.287692] audit: type=1400 audit(1585968297.926:51): apparmor="DENIED" operation="open" profile="snap.gedit.gedit" name="/proc/2682/mounts" pid=2682 comm="gedit" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Apr  3 19:44:58 peyre kernel: [  185.466292] audit: type=1400 audit(1585968298.106:52): apparmor="DENIED" operation="open" profile="snap.gedit.gedit" name="/var/log/syslog" pid=2682 comm="pool" requested_mask="r" denied_mask="r" fsuid=1000 ouid=102
Apr  3 19:44:58 peyre kernel: [  185.477211] audit: type=1400 audit(1585968298.118:53): apparmor="DENIED" operation="open" profile="snap.gedit.gedit" name="/var/log/" pid=2682 comm="pool" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Apr  3 19:44:58 peyre kernel: [  185.478447] audit: type=1400 audit(1585968298.118:54): apparmor="DENIED" operation="open" profile="snap.gedit.gedit" name="/proc/2682/mountinfo" pid=2682 comm="gedit" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Apr  3 19:44:58 peyre kernel: [  185.478450] audit: type=1400 audit(1585968298.118:55): apparmor="DENIED" operation="open" profile="snap.gedit.gedit" name="/proc/2682/mounts" pid=2682 comm="gedit" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Apr  3 19:45:17 peyre kernel: [  205.273025] audit: type=1400 audit(1585968317.914:56): apparmor="DENIED" operation="capable" profile="/snap/core/8935/usr/lib/snapd/snap-confine" pid=2755 comm="snap-confine" capability=4  capname="fsetid"
Apr  3 19:45:19 peyre kernel: [  206.636778] audit: type=1400 audit(1585968319.278:57): apparmor="DENIED" operation="open" profile="snap.okteta.okteta" name="/proc/sys/kernel/core_pattern" pid=2755 comm="okteta" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Apr  3 19:45:17 peyre gvfsd-metadata[1732]: message repeated 75 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Apr  3 19:45:21 peyre dbus-daemon[1458]: apparmor="DENIED" operation="dbus_signal"  bus="session" path="/" interface="org.kde.KDirNotify" member="enteredDirectory" mask="send" name="org.freedesktop.DBus" pid=2755 label="snap.okteta.okteta" peer_pid=1722 peer_label="unconfined"
Apr  3 19:45:21 peyre kernel: [  208.429354] audit: type=1400 audit(1585968321.070:58): apparmor="DENIED" operation="open" profile="snap.okteta.okteta" name="/etc/fstab" pid=2755 comm="okteta" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Apr  3 19:45:21 peyre kernel: [  208.429366] audit: type=1400 audit(1585968321.070:59): apparmor="DENIED" operation="open" profile="snap.okteta.okteta" name="/proc/2755/mounts" pid=2755 comm="okteta" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Apr  3 19:45:21 peyre kernel: [  208.429440] audit: type=1400 audit(1585968321.070:60): apparmor="DENIED" operation="open" profile="snap.okteta.okteta" name="/proc/2755/mounts" pid=2755 comm="okteta" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Apr  3 19:45:21 peyre kernel: [  208.437766] audit: type=1107 audit(1585968321.078:61): pid=721 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/UPower" interface="org.freedesktop.DBus.Introspectable" member="Introspect" mask="send" name="org.freedesktop.UPower" pid=2755 label="snap.okteta.okteta" peer_pid=1565 peer_label="unconfined"
Apr  3 19:45:21 peyre kernel: [  208.437766]  exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
Apr  3 19:45:21 peyre kernel: [  208.468252] audit: type=1400 audit(1585968321.106:62): apparmor="DENIED" operation="open" profile="snap.okteta.okteta" name="/etc/xdg/menus/" pid=2755 comm="okteta" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Apr  3 19:45:21 peyre kernel: [  208.468273] audit: type=1400 audit(1585968321.110:63): apparmor="DENIED" operation="open" profile="snap.okteta.okteta" name="/etc/xdg/xdg-xubuntu/menus/" pid=2755 comm="okteta" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Apr  3 19:45:21 peyre kernel: [  208.471020] audit: type=1400 audit(1585968321.110:64): apparmor="DENIED" operation="open" profile="snap.okteta.okteta" name="/var/log/syslog" pid=2755 comm="okteta" requested_mask="r" denied_mask="r" fsuid=1000 ouid=102
Apr  3 19:45:21 peyre kernel: [  208.491258] audit: type=1400 audit(1585968321.130:65): apparmor="DENIED" operation="open" profile="snap.okteta.okteta" name="/proc/sys/kernel/core_pattern" pid=2843 comm="kioslave" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Apr  3 19:45:24 peyre kernel: [  211.607969] kauditd_printk_skb: 9 callbacks suppressed
Apr  3 19:45:24 peyre kernel: [  211.607970] audit: type=1400 audit(1585968324.246:75): apparmor="DENIED" operation="open" profile="snap.okteta.okteta" name="/etc/fstab" pid=2755 comm="okteta" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Apr  3 19:45:21 peyre dbus-daemon[1458]: apparmor="DENIED" operation="dbus_signal"  bus="session" path="/" interface="org.kde.KDirNotify" member="enteredDirectory" mask="send" name="org.freedesktop.DBus" pid=2755 label="snap.okteta.okteta" peer_pid=1722 peer_label="unconfined"
Apr  3 19:45:26 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:45:33 peyre gvfsd-metadata[1732]: message repeated 13 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] AppArmor D-Bus mediation is enabled
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Activating service name='org.xfce.Xfconf' requested by ':1.0' (uid=0 pid=2846 comm="thunar " label="unconfined")
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Successfully activated service 'org.xfce.Xfconf'
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Activating service name='org.freedesktop.thumbnails.Thumbnailer1' requested by ':1.0' (uid=0 pid=2846 comm="thunar " label="unconfined")
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Activating service name='org.gtk.vfs.Daemon' requested by ':1.2' (uid=0 pid=2861 comm="/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd " label="unconfined")
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Successfully activated service 'org.gtk.vfs.Daemon'
Apr  3 19:45:33 peyre org.freedesktop.thumbnails.Thumbnailer1[2851]: Registered thumbailer atril-thumbnailer -s %s %u %o
Apr  3 19:45:33 peyre org.freedesktop.thumbnails.Thumbnailer1[2851]: Registered thumbailer gnome-thumbnail-font --size %s %u %o
Apr  3 19:45:33 peyre org.freedesktop.thumbnails.Thumbnailer1[2851]: Registered thumbailer /usr/bin/gdk-pixbuf-thumbnailer -s %s %u %o
Apr  3 19:45:33 peyre org.freedesktop.thumbnails.Thumbnailer1[2851]: Registered thumbailer /usr/bin/gdk-pixbuf-thumbnailer -s %s %u %o
Apr  3 19:45:33 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:45:33 peyre kernel: [  221.134151] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv84_xuc00f failed with error -2
Apr  3 19:45:33 peyre kernel: [  221.134155] nouveau 0000:01:00.0: vp: unable to load firmware nouveau/nv84_xuc00f
Apr  3 19:45:33 peyre kernel: [  221.134156] nouveau 0000:01:00.0: vp: init failed, -2
Apr  3 19:45:33 peyre kernel: [  221.134180] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv84_xuc103 failed with error -2
Apr  3 19:45:33 peyre kernel: [  221.134182] nouveau 0000:01:00.0: bsp: unable to load firmware nouveau/nv84_xuc103
Apr  3 19:45:33 peyre kernel: [  221.134183] nouveau 0000:01:00.0: bsp: init failed, -2
Apr  3 19:45:33 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Activating service name='org.gtk.vfs.UDisks2VolumeMonitor' requested by ':1.2' (uid=0 pid=2861 comm="/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd " label="unconfined")
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Successfully activated service 'org.gtk.vfs.UDisks2VolumeMonitor'
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Activating service name='org.gtk.vfs.MTPVolumeMonitor' requested by ':1.2' (uid=0 pid=2861 comm="/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd " label="unconfined")
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Successfully activated service 'org.gtk.vfs.MTPVolumeMonitor'
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Activating service name='org.gtk.vfs.GPhoto2VolumeMonitor' requested by ':1.2' (uid=0 pid=2861 comm="/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd " label="unconfined")
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Successfully activated service 'org.gtk.vfs.GPhoto2VolumeMonitor'
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Activating service name='org.gtk.vfs.GoaVolumeMonitor' requested by ':1.2' (uid=0 pid=2861 comm="/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd " label="unconfined")
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Successfully activated service 'org.gtk.vfs.GoaVolumeMonitor'
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Activating service name='org.gtk.vfs.AfcVolumeMonitor' requested by ':1.2' (uid=0 pid=2861 comm="/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd " label="unconfined")
Apr  3 19:45:33 peyre org.gtk.vfs.AfcVolumeMonitor[2851]: Volume monitor alive
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Successfully activated service 'org.gtk.vfs.AfcVolumeMonitor'
Apr  3 19:45:33 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Successfully activated service 'org.freedesktop.thumbnails.Thumbnailer1'
Apr  3 19:45:35 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:45:35 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:45:47 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Activating service name='ca.desrt.dconf' requested by ':1.11' (uid=0 pid=2936 comm="mousepad /var/log/syslog " label="unconfined")
Apr  3 19:45:47 peyre dbus-daemon[2851]: [session uid=0 pid=2849] Successfully activated service 'ca.desrt.dconf'
Apr  3 19:46:19 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:46:53 peyre kernel: [  300.997956] audit: type=1400 audit(1585968413.636:76): apparmor="DENIED" operation="exec" profile="snap.okteta.okteta" name="/usr/bin/localedef" pid=3050 comm="kf5-locale-gen" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Apr  3 19:46:54 peyre kernel: [  301.695200] audit: type=1400 audit(1585968414.332:77): apparmor="DENIED" operation="capable" profile="snap.okteta.okteta" pid=2980 comm="okteta" capability=2  capname="dac_read_search"
Apr  3 19:46:54 peyre kernel: [  301.695213] audit: type=1400 audit(1585968414.332:78): apparmor="DENIED" operation="capable" profile="snap.okteta.okteta" pid=2980 comm="okteta" capability=1  capname="dac_override"
Apr  3 19:46:53 peyre gvfsd-metadata[1732]: message repeated 17 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Apr  3 19:46:57 peyre anacron[713]: Job `cron.daily' started
Apr  3 19:46:57 peyre anacron[3059]: Updated timestamp for job `cron.daily' to 2020-04-03
Apr  3 19:46:57 peyre cracklib: no dictionary update necessary.
Apr  3 19:46:57 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:46:57 peyre gvfsd-metadata[1732]: message repeated 37 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Apr  3 19:46:57 peyre systemd[1]: Stopping Make remote CUPS printers available locally...
Apr  3 19:46:57 peyre systemd[1]: Stopped Make remote CUPS printers available locally.
Apr  3 19:46:57 peyre systemd[1]: Stopping CUPS Scheduler...
Apr  3 19:46:57 peyre systemd[1]: Stopped CUPS Scheduler.
Apr  3 19:46:57 peyre systemd[1]: Closed CUPS Scheduler.
Apr  3 19:46:57 peyre systemd[1]: Stopping CUPS Scheduler.
Apr  3 19:46:57 peyre systemd[1]: Listening on CUPS Scheduler.
Apr  3 19:46:57 peyre gvfsd-metadata[1732]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Apr  3 19:46:57 peyre gvfsd-metadata[1732]: message repeated 11 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Apr  3 19:46:57 peyre systemd[1]: Stopped CUPS Scheduler.
Apr  3 19:46:57 peyre systemd[1]: Stopping CUPS Scheduler.
Apr  3 19:46:57 peyre systemd[1]: Started CUPS Scheduler.
Apr  3 19:46:57 peyre systemd[1]: Started CUPS Scheduler.
Apr  3 19:46:57 peyre systemd[1]: Started Make remote CUPS printers available locally.
Apr  3 19:46:57 peyre colord[822]: failed to get session [pid 3353]: No data available

```

(That's all that shows in Terminal, anyway.)

---

### Post by peyre on 2020-04-03
Well, I was just writing up here that after submitting that the system locked up again, when . . . it did it a third time.

This is ridiculous!  If you can't count on Linux to stay up longer than ten minutes, what's the point of using it?  It's not like it's an old installation, or that I'm using some customized kernel or anything; this is the LTS.  ](*,)](*,)](*,)

---

### Post by peyre on 2020-04-03
FOUR. TIMES. NOW.  It goes down before it completes playing a single MP3.
](*,)
](*,)
](*,)
](*,)
I have changed out EVERYTHING in my computer except the hard drives.  I get that one of them might be the problem, but the S.M.A.R.T. data all looks good and I'd have to jump through quite a few hoops to test it.  I *coult* maybe borrow hard drives from work, clonezilla everything over to them, and see what happens, but that's kind of a big deal and with an intermittent issue like this you just never know if you isolated the problem or the Lockup Genie just hasn't decided to pay a visit yet.  It seems to strike just after I post on here that it seems fixed.

---

### Post by peyre on 2020-04-03
Ok, five times now.  I posted the above, then opened Thunar and it locked up.  Oddly, this time, whenever I clicked the mouse, it actually hung for half a second or a second, then I could move it around again.  It didn't *respond* to those clicks, just froze briefly when I did them.  Don't know that it means anything; it's just something I hadn't seen yet.

---

### Post by peyre on 2020-04-04
Well!  Just hit six times this evening.  Funny, I watch the second half of a movie and the lockup happens just when I open Thunar...which brings to mind that Thunar often seems to be involved when the C (crash) hits the fan.  'Course that doesn't tell us which drive 'cause I'm often looking at stuff on the data drive.  All i can say is, I'm glad there's been a bit of time (and a few homebrews) since the last crash, or I'd be searching for SOME KIND of more intense frustration in my emoticons.

---

### Post by ajgreeny on 2020-04-04
I can see that this is very frustrating for you but I can assure you that it is not typical of Linux or Xubuntu in any way at all.

I run the same version on my desktop and laptop computers, the laptop has an uptime of over 5 days and the desktop an uptime of over 17 days, both of them with no logouts or new sessions.

I would still suspect a hardware problem but I am completely baffled about what it might be that's doing it.  Sorry!

---

### Post by peyre on 2020-04-04
Well thanks Greeny.  I do know this isn't typical; I've been running xubuntu since 8.10 and I've never had this trouble before.  Maybe I'll have to try changing the drives - I just wish I knew which one's causing the trouble.  Of course this waited for the weekend to happen, when I'm not in the office to borrow drives to work with.

---

### Post by peyre on 2020-04-07
Ok, so last night I transferred my system to a similar-size SSD and fired it up, and . . . it logged me out within the hour.  I shut down in disgust and went to the living room to watch TV with the wife.

Today I transferred my data to another mechanical drive and I'm trying again.  It made it through the remainder of the evening (about an hour and a half) and has stayed up, at least until I got up this morning, backing up my data to an external drive.  So far so good (but I've been here before...).

Edit:  I've ordered a replacement data drive.  We'll see how this goes in the meantime...

---

### Post by peyre on 2020-04-10
So, after running for several days straight (backing up my system to a portable drive takes **so** much longer than to an external HD!), it logged me off again sometime last night.  I have literally changed everything in this computer--even the drives and the video card--and it's still doing this, though it doesn't seem to be crashing any more.  And random logoffs seem more likely to be a software issue than crashes (I think).  Any ideas?  If not, I'll start a new thread specifically about the logoffs.

---

### Post by peyre on 2020-04-11
AND, it just locked up again.  I don't know what to do.  I've changed ALL THE HARDWARE - I transferred my OS and data to different physical disks, I changed the video card, and the computer is a different physical machine than the one I was first experiencing this on.  ](*,)

---

### Post by ajgreeny on 2020-04-11
So now everything seems to point to a software problem and rather than keep trying to find something else to blame I think I would just reinstall the operating system in case that is where the difficulties lie.

You appear to have changed all hardware items, almost one by one, but that has provided no solution for you, so what is left?  The OS software I suggest, which may not be the answer you hoped for, but at the moment I can't see any other pathway for you.

---

### Post by peyre on 2020-04-11
UGH...a reinstall from scratch is no big deal on my laptop, but my desktop is a whole order of magnitude harder.  Also I *think* I tried that once already, but at this point I can't say that for certain; my memory of the early parts of this is kind of foggy.  But, that may be all there is left to try.  Maybe I'll see if I can limp along until 20.10 comes out and then do a fresh install of that.

---

### Post by ajgreeny on 2020-04-11
Why 20.10? That is not going to be the next LTS version; that will be 20.04 in about 2 weeks time, April 23rd.

---

### Post by peyre on 2020-04-12
D'ohh, sorry, I meant 20.04.

---

### Post by lvm on 2020-04-12
Ah, nouveau again. Don't use it, install proper nvidia drivers.

---

### Post by peyre on 2020-04-14
Oh hey, there's an idea.  I've switched over to the proprietary driver; we'll see if that clears this up.

---

### Post by peyre on 2020-04-27
Wow... selecting the proprietary NVidia driver seems to have done the trick.  I haven't had a lockup or spontaneous logoff since I did that.  I've been real hesitant to say so because every time I've said "Hey, that last thing seems to have done the trick", I immediately start having trouble again.  But I think we have it this time.  Thanks so much lvm!

---

