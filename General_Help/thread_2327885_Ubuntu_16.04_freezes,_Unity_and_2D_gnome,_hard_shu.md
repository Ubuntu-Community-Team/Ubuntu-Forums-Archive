---
title: "Ubuntu 16.04 freezes, Unity and 2D gnome, hard shutdown required"
date: 2016-06-15
forum: General Help
---

### Post by kolibri on 2016-06-15
After a clean install of 16.04 after a HDD failure, system is randomly freezing on me, requiring hard shutdowns multiple times per day.

Clean install of 16.04 and boot onto 32GB SSD.  Home and data partition on new HDD.  New 16 GB ram added to existing 16GB ram in place of 4GB pair.  Dell XPS desktop.
[COLOR=#000000]Holding down the shift key during startup does not produce a grub menu to do Memtest.[/COLOR]

[COLOR=#000000]Dell  diagnostics indicate that all hardware is working, specifically no memory problems.
[/COLOR]Memtest from the command line, with multiple passes over 15 hours finds no memory problems.
Memtest from the liveCD over 2 passes finds no memory problems, so I don't think this is a memory issue.

[COLOR=#000000]32 GB memory, and 12GB swap on a HDD partition. Freeze occurs with swap on and swap off.[/COLOR]

[COLOR=#000000]System freezes either before (10% of the time ) login, or after login.
[/COLOR]

[COLOR=#000000]After login:[/COLOR]
[COLOR=#000000]System freezes in Unity.[/COLOR]
[COLOR=#000000]System freezes in Gnome flashback 2D.[/COLOR]
[COLOR=#000000]Entire system freezes, Atl-PrtScn REISUB does not work, short power button press does not work, hard shutdown required.[/COLOR]

[COLOR=#000000]Before login (only about 10% of the freezes):[/COLOR]
[COLOR=#000000]REISUB works sometimes, other times not. Short power button press sometimes brings up shutdown dialog, but does not respond to mouse or keyboard input to finish dialog, and hard shutdown is required.[/COLOR]

[COLOR=#000000]After login, system problem detected dialog opens about 50% of the time, with a unity settings daemon error.[/COLOR]


[COLOR=#000000]Any suggestions for how to trouble shoot this issue?  This is not only making me worried about creating issues for my new hardware, it's complicating my attempts to pull the last bit of data off the failing hard drive (and slighly corrupted back up as well). [/COLOR]

[COLOR=#000000]Thanks!

edit to add latest:
REISUB initially wouldn't work.
After 
A) adding [/COLOR]**ppa:ci-train-ppa-service/landing-008**[COLOR=#333333][FONT=Ubuntu] 
B) turning swap back on  (32 GB RAM, 12 GB swap on HDD)
C) installing linux-crashdump

The system is now alternating between freezing and crashing.  When it crashes, it automatically restarts in about 
20 seconds (coincidentally, the time it takes for me to try the SysReq key combinations- so i thought I was rebooting it, but if I wait and do nothing, it reboots), and is still occasionally freezing without restarting- but accepting SysReq key input. 
I've been able to  [/FONT][/COLOR][COLOR=#000000] Alt+SysReq [/COLOR][COLOR=#333333][FONT=Ubuntu]REISUB out of the frozen system (exit to console doesn't work however, nor does [/FONT][/COLOR][COLOR=#000000] Alt+SysReq+F.  or K[/COLOR][COLOR=#333333][FONT=Ubuntu]), and I can hear the hard drive accessing during the freeze (which it wasn't doing before), as a result, I now have a syslog covering the time between the frozen input and the shutdown. 

Relevant syslog entry seems to indicate a hard lockup of one CPU to be implicated in the freeze.

Post Mortem:
I think, after all, I had two independent bugs going on.  
I re-installed 14.04  and the display freeze with REISUB access continued, traced that to the Nouveau driver and NVIIDIA video card bug freezing the display.  Switched to the NVIDIA proprietary/tested driver and resolved that.
I independently checked each USB device (mouse, etc) each memory module connection.  No hardware issues or memory failures.  
I think the total system freeze was specific to 16.04 since the hardware is working fine in 14.04, but couldn't diagnose it, I'm going to stick with 14.04 for now until I get some high priority work out of the way.

[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-06-15
I am not sure this will work in your case but I have been tinkering around with this method since the Development cycle of Xenial
There is a less radical way than rebooting the whole system. **If SysReq key works, **you can kill processes one-by-one using Alt+SysReq+F. Kernel will kill the mostly <expensive> process each time. If you want to kill all processes for one console, you can issue Alt+SysReq+K.

NOTE: You should explicitly enable these key combinations. Ubuntu ships with sysrq default setting 176 (128+32+16), which allows to run only SUB part of REISUB combination. You can change it to 1 or, which is potentially less harmful, 244. To do this:
```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```

and switch 176 to 244; then

```
echo 244 | sudo tee /proc/sys/kernel/sysrq
```
It will immediately work! You can test this by pressing<**Alt+SysReq+F**>. For me, it killed active browser tab, then all extensions. And if you will continue, you can reach X Server restart.

If you're forced to do this, do it slowly. Let a few seconds pass in between each keypress so that the commands you're invoking have a chance to finish before you go to the next one. 
My bit to try and help. And Also Tips from Askubuntu.
Regards

---

### Post by kolibri on 2016-06-15
Thanks runrickus,

I've tried that, and on freezes after login, no keyboard input works at all, not even those key combinations.

the unity-settings-daemon error message that pops up after rebooting reports a "crash" unity-settings-daemon crashed with SIGSEGV in up-exported_daemon_get_lid_is_closed()

---

### Post by QDR06VV9 on 2016-06-15
I was afraid of that... But yes if X is locking up fully, or even the kernel is hung, you can't do much with a keyboard shortcut. 
Thanks for trying it though!:)
Kind Regards

---

### Post by QDR06VV9 on 2016-06-15
One other thought here what version of ubuntu-ui-toolkit are you using
```
apt-cache policy ubuntu-ui-toolkit
```

---

### Post by kolibri on 2016-06-16
> **runrickus said:**
> One other thought here what version of ubuntu-ui-toolkit are you using
```
apt-cache policy ubuntu-ui-toolkit
```

I'm not.... it's not installed, and since I'm not doing development, should it be installed?  Was this meant for someone else?

---

### Post by kolibri on 2016-06-16
I've edited the original posts with the results from memtest, run while logged in from the terminal, and from the live CD, which didn't pick up any memory errors, so I don't think it's a memory problem.  Ironically, the last freeze happened when I exited the terminal-run memtest.

---

### Post by vanadium on 2016-06-16
Keep an eye on kernel messages. On a brand new laptop, I had systematic freezes on random moments. Kernel logs revealed hardware errors now and then:
```

mce: [Hardware Error]: Machine check events logged

```
The Dell diagnostics tool did not reveal errors. Yet the issue was resolved after replacing the motherbord, pointing to faulty hardware as the cause.

---

### Post by kolibri on 2016-06-16
I don't really know how to read a syslog or kernel log, but they don't seem to have any errors that might be associated with the freezes.  The kernel log has mostly network errors and USB errors- which are probably when I try to mount one of my old corrupted hard drives.

fwts gives me errors, but the vast majority of them say that the kernel doesn't use the data associated with the error.  I'm not sure why the checksum line says uefi, I'm pretty sure I'm using the legacy boot.  

```
est           |Pass |Fail |Abort|Warn |Skip |Info |
---------------+-----+-----+-----+-----+-----+-----+
acpiinfo       |     |     |     |     |     |    3|
acpitables     |   17|     |     |     |     |     |
apicedge       |     |    4|     |     |     |     |
apicinstance   |    1|     |     |     |     |     |
asf            |    6|     |     |     |     |     |
aspm           |    3|     |     |    8|     |     |
aspt           |     |     |     |     |    1|     |
autobrightness |     |     |     |     |     |     |
bert           |     |     |     |     |    1|     |
bgrt           |     |     |     |     |    1|     |
bios32         |     |     |     |     |     |     |
bios_info      |     |     |     |     |     |    1|
boot           |     |     |     |     |    1|     |
checksum       |   19|     |     |     |     |     |ubuntu 16.04 uefi
cpep           |     |     |     |     |    1|     |
cpufreq        |    3|    2|     |    8|    2|     |
crs            |    1|     |     |     |     |     |
csm            |     |     |     |     |     |    1|
csrt           |     |     |     |     |    1|     |
cstates        |   15|     |     |     |     |     |
dbg2           |     |     |     |     |    1|     |
dbgp           |     |     |     |     |    1|     |
dmar           |    2|     |     |     |     |     |
dmicheck       |   54|   16|     |     |    1|     |
ebda           |    1|     |     |     |     |     |
ecdt           |     |     |     |     |    1|     |
erst           |     |     |     |     |    1|     |
facs           |    1|     |     |     |     |     |
fadt           |   27|    5|     |    3|    2|    1|
fan            |   13|    1|     |     |     |     |
fpdt           |    1|     |     |     |     |     |
gtdt           |     |     |     |     |    1|     |
hda_audio      |    2|     |     |     |     |     |
hest           |     |     |     |     |    1|     |
hpet           |    5|     |     |     |     |     |
iort           |     |     |     |     |    1|     |
klog           |    1|     |     |     |     |     |
lpit           |     |     |     |     |    1|     |
madt           |   45|     |     |     |     |     |
maxfreq        |    1|     |     |     |     |     |
maxreadreq     |    1|     |     |     |     |     |
mcfg           |    2|     |     |     |     |     |
mchi           |     |     |     |     |    1|     |
method         |  550|    1|     |     |  144|     |
microcode      |     |     |     |     |    1|     |
mpcheck        |    9|     |     |     |     |     |
msdm           |    1|     |     |     |     |     |
msr            |  113|     |     |     |     |     |
mtrr           |    2|     |     |     |    1|     |
nx             |    3|     |     |     |     |     |
oops           |    2|     |     |     |     |     |
osilinux       |     |     |     |    1|     |     |
pcc            |     |     |     |     |     |    1|
pciirq         |    4|     |     |     |     |     |
pnp            |    2|     |     |     |     |     |
rsdp           |    8|    1|     |     |     |     |
rsdt           |    1|     |     |     |     |     |
sbst           |     |     |     |     |    1|     |
securebootcert |     |     |     |     |    1|     |
slic           |    1|     |     |     |     |     |
slit           |     |     |     |     |    1|     |
spcr           |     |     |     |     |    1|     |
spmi           |     |     |     |     |    1|     |
srat           |     |     |     |     |    1|     |
stao           |     |     |     |     |    1|     |
syntaxcheck    |     |   39|     |     |     |     |
tcpa           |     |     |    1|     |     |     |
tpm2           |     |     |    1|     |     |     |
uefi           |     |     |     |     |    1|     |
uefibootpath   |     |     |    1|     |     |     |
version        |     |     |     |     |     |    4|
virt           |    1|     |     |     |     |     |
waet           |     |     |     |     |    1|     |
wakealarm      |    6|     |     |     |     |     |
wdat           |     |     |     |     |    1|     |
wmi            |     |     |     |     |     |     |
xenv           |     |     |    1|     |     |     |
xsdt           |    1|     |     |     |     |     |
---------------+-----+-----+-----+-----+-----+-----+
Total:         |  925|   69|    4|   20|  176|   11|
---------------+-----+-----+-----+-----+-----+-----+
```

---

### Post by QDR06VV9 on 2016-06-16
This was a bug reported about the time 14.10 came to be: [https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1380278](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1380278)
And there were reports that adding this PPA had some success but I do not know for sure that this will also benefit you...but if you want to try it see this:[https://launchpad.net/~ci-train-ppa-service/+archive/ubuntu/landing-008](https://launchpad.net/~ci-train-ppa-service/+archive/ubuntu/landing-008)
And if you do add this PPA would you be as kind to keep us updated on this.
Thanks!:)

---

### Post by kolibri on 2016-06-16
> **runrickus said:**
> This was a bug reported about the time 14.10 came to be: [https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1380278](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1380278)
And there were reports that adding this PPA had some success but I do not know for sure that this will also benefit you...but if you want to try it see this:[https://launchpad.net/~ci-train-ppa-service/+archive/ubuntu/landing-008](https://launchpad.net/~ci-train-ppa-service/+archive/ubuntu/landing-008)
And if you do add this PPA would you be as kind to keep us updated on this.
Thanks!:)

I'll try this and let you know.

---

### Post by kolibri on 2016-06-16
> **runrickus said:**
> This was a bug reported about the time 14.10 came to be: [https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1380278](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1380278)
And there were reports that adding this PPA had some success but I do not know for sure that this will also benefit you...but if you want to try it see this:[https://launchpad.net/~ci-train-ppa-service/+archive/ubuntu/landing-008](https://launchpad.net/~ci-train-ppa-service/+archive/ubuntu/landing-008)
And if you do add this PPA would you be as kind to keep us updated on this.
Thanks!:)

Nope, still freezing all.

---

### Post by QDR06VV9 on 2016-06-16
Crap that's too bad:(...But thanks for testing it out.
Now if you want to remove that PPA and all that came with it you can do as follows
```
sudo apt-get install ppa-purge
```
Then remove that PPA by
```
sudo ppa-purge ppa:ci-train-ppa-service/landing-008
```
Followed by
```
sudo apt update
```
And 
```
sudo apt full-upgrade
```
That will return your system to the state it was before adding the PPA 
Thanks Again for trying.
Kind Regards

---

### Post by kolibri on 2016-06-16
> **runrickus said:**
> Crap that's too bad:(...But thanks for testing it out.
Now if you want to remove that PPA and all that came with it you can do as follows
```
sudo apt-get install ppa-purge
```
Then remove that PPA by
```
sudo ppa-purge ppa:ci-train-ppa-service/landing-008
```
Followed by
```
sudo apt update
```
And 
```
sudo apt full-upgrade
```
That will return your system to the state it was before adding the PPA 
Thanks Again for trying.
Kind Regards

I"ll leave it for now and see if it stops the Unity system error message from popping up even if it doesn't stop the freezes.

I've seen forum posts about Dell XPS systems freezing in windows, and suggestions for changing performance settings in bios, however, in my version of bios I don't have the settings recommended.  How do I update the bios through Ubuntu in Legacy boot mode?  I've found instructions for adding the update to the EFI folder in /boot, but in Legacy boot mode I don't have that option.  I could reinstall in UEFI mode I suppose.  I don't want to roll back to a previous version of Ubuntu because I just updated my dual boot laptop to 16.04 and that's usually the complicated install.

Alternatively, are there anythings in the log files I should be looking for?  So far I haven't seen any commonalities in the log files for individual freezes.

---

### Post by Jason_Hunter on 2016-06-16
How long does it take to freeze?

Have you tried running a serial terminal to catch kernel messages at time of crash?

---

### Post by kolibri on 2016-06-17
> **Jason_Hunter said:**
> How long does it take to freeze?

Have you tried running a serial terminal to catch kernel messages at time of crash?

Freezing is random - rarely before logging in, after login anywhere from 10 minutes to 2 hours or more, and the processes I have running when it crashes seem to be random as well.

I don't think I have the necessary hardware for a serial terminal (or the time right now to devote to setting up a network console)
-------------------------------------------------------------------------------------------------------------

I was trying to get the kernel to dump messages to swap when it crashed again, however....

I've managed to get the freeze behavior to change , after doing:

A) adding **ppa:ci-train-ppa-service/landing-008 **and updating
B) turning swap on
C) in 'other drivers', saying "do not use the device" instead of the processor microcode firmware for Intel CPUs
D) installing linux-crashdump

I can now get the keyboard input recognized (and the hard drive access noise continues,) for the past two freezes, but only for  **SysReq key**  I can't use the keyboard to exit to console.  After restart, I can now see Syslog entries from following the freeze, the relevant log item seems to be a hard lockup for CPU 2


 
Jun 17 12:17:01 Tach CRON[4705]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)Jun 17 12:17:01 Tach org.gnome.evolution.dataserver.Sources5[1575]: ** (evolution-source-registry:1901): WARNING **: secret_service_search_sync: must specify at least one attribute to matchJun 17 **12:29:05 Tach kernel: [ 4293.260016] NMI watchdog: Watchdog detected hard LOCKUP on cpu 2**Jun 17 12:29:05 Tach kernel: [ 4293.260018] Modules linked in: nls_iso8859_1 rfcomm bnep ath3k btusb btrtl btbcm btintel input_leds bluetooth snd_hda_codec_hdmi intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel snd_hda_codec_realtek snd_hda_codec_generic arc4 kvm dcdbas snd_hda_intel ath9k irqbypass crct10dif_pclmul snd_hda_codec ath9k_common snd_hda_core ath9k_hw crc32_pclmul snd_hwdep snd_pcm ath aesni_intel mac80211 aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmidi snd_seq serio_raw cfg80211 snd_seq_device snd_timer snd mei_me soundcore mei shpchp lpc_ich soc_button_array mac_hid sunrpc parport_pc ppdev lp parport autofs4 uas usb_storage hid_generic usbhid hid nouveau mxm_wmi wmi i2c_algo_bit ttm drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops ahci psmouse drm libahci r8169 mii video fjesJun 17 12:29:05 Tach kernel: [ 4293.260049] CPU: 2 PID: 0 Comm: swapper/2 Not tainted 4.4.0-24-generic #43-UbuntuJun 17 12:29:05 Tach kernel: [ 4293.260050] Hardware name: Dell Inc. XPS 8700/0KWVT8, BIOS A03 08/02/2013Jun 17 12:29:05 Tachy kernel: [ 4293.260051] task: ffff88080af41b80 ti: ffff88080af50000 task.ti: ffff88080af50000Jun 17 12:29:05 Tachy kernel: [ 4293.260052] RIP: 0010:[<ffffffff816bcd21>]  [<ffffffff816bcd21>] cpuidle_enter_state+0x111/0x2b0Jun 17 12:29:05 Tachy kernel: [ 4293.260056] RSP: 0018:ffff88080af53e70  EFLAGS: 00000246

and it goes on until (and after) restart.

[COLOR=#333333][FONT=Ubuntu]The system is now alternating between freezing and crashing.  When it crashes, it automatically restarts in about [/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]20 seconds (coincidentally, the time it takes for me to try the SysReq key combinations- so i thought I was rebooting it, but if I wait and do nothing, it reboots), and is still occasionally freezing without restarting- but accepting SysReq key input. [/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-06-17
Out of curiosity what kernel are you running?
Or even... have you tried running a different kernel?

---

### Post by kolibri on 2016-06-17
> **runrickus said:**
> Out of curiosity what kernel are you running?
Or even... have you tried running a different kernel?

4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

I have:
ii  linux-image-4.4.0-21-generic                  4.4.0-21.37                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-24-generic                  4.4.0-24.43                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic            4.4.0-21.37                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-24-generic            4.4.0-24.43                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.4.0.24.25                                         amd64        Generic Linux kernel image



I can't get into grub when I startup (with the shift key), (legacy boot), so I've been trying to get grub back so that I try other kernels.

---

### Post by QDR06VV9 on 2016-06-17
Just wondering if you have tried Boot Repair to fix Grub?
Download here: [https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)

---

### Post by vanadium on 2016-06-17
Follow kernel messages with "dmesg -w". Check for hardware errors. I told you I had the same symptoms and they have replaced the motherbord. Dell XPS 13 9350 with Ubuntu 14.04. I could not even get through the initial setup. Then I wiped Ubuntu and installed 16.04 instead. Much better, but would still freeze within 15 minutes to an hour. If it is faulty hardware, there is nothing you can do yourself.

---

### Post by kolibri on 2016-06-17
So, got grub back, tried both the.4.0-24 and 4.4.0-21 kernels, the 21 kernel just took me back to the complete freeze setting.
syslog from latest freeze - clock froze at 22:47.
```
Jun 17 22:46:49 Tachylite systemd[1]: Starting Cleanup of Temporary Directories...Jun 17 22:46:49 Tachylite systemd-tmpfiles[8547]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Jun 17 22:46:49 Tachylite systemd[1]: Started Cleanup of Temporary Directories.
Jun 17 22:46:50 Tachylite gnome-session[2075]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Jun 17 22:48:58 Tachylite rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="818" x-info="http://www.rsyslog.com"] start
Jun 17 22:48:58 Tachylite rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ]
Jun 17 22:48:58 Tachylite rsyslogd: rsyslogd's groupid changed to 108 
Jun 17 22:48:58 Tachylite rsyslogd: rsyslogd's userid changed to 104
Jun 17 22:48:58 Tachylite systemd-modules-load[288]: Inserted module 'lp'
Jun 17 22:48:58 Tachylite systemd-modules-load[288]: Inserted module 'ppdev'
Jun 17 22:48:58 Tachylite systemd-modules-load[288]: Inserted module 'parport_pc'
Jun 17 22:48:58 Tachylite systemd[1]: Mounting FUSE Control File System...
Jun 17 22:48:58 Tachylite systemd[1]: Starting Apply Kernel Variables...
Jun 17 22:48:58 Tachylite systemd[1]: Starting Create Static Device Nodes in /dev...
Jun 17 22:48:58 Tachylite systemd[1]: Mounted FUSE Control File System.
Jun 17 22:48:58 Tachylite systemd[1]: Started Apply Kernel Variables.
Jun 17 22:48:58 Tachylite systemd[1]: Started Create Static Device Nodes in /dev.
Jun 17 22:48:58 Tachylite systemd[1]: Starting udev Kernel Device Manager...
Jun 17 22:48:58 Tachylite systemd[1]: Started udev Kernel Device Manager.
Jun 17 22:48:58 Tachylite rsyslogd-2039: Could not open output pipe '/dev/xconsole':: No such file or directory [v8.16.0 try http://www.rsyslog.com/e/2039 ]
Jun 17 22:48:58 Tachylite systemd[1]: Starting Remount Root and Kernel File Systems...
Jun 17 22:48:58 Tachylite systemd[1]: Started Remount Root and Kernel File Systems.
Jun 17 22:48:58 Tachylite ureadahead[291]: ureadahead:/var/spool/cups/tmp/cups-dbus-notifier-lockfile: No such file or directory
Jun 17 22:48:58 Tachylite systemd[1]: Reached target Local File Systems (Pre).
Jun 17 22:48:58 Tachylite systemd[1]: Starting udev Coldplug all Devices...
Jun 17 22:48:58 Tachylite systemd[1]: Starting Load/Save Random Seed...
Jun 17 22:48:58 Tachylite rsyslogd-2007: action 'action 10' suspended, next retry is Fri Jun 17 22:49:28 2016 [v8.16.0 try http://www.rsyslog.com/e/2007 ]
```

I'm not sure where the shutdown commands start.

I'm giving up on 16.04 though, I have to go back to real work.  I'll do a clean install of 14, and if the issue goes away, I'll know it was the Ubuntu upgrade and not something that happened during the hardware upgrade.
Thanks for all the replies and suggestions.

---

### Post by kolibri on 2016-06-20
[COLOR=#333333][FONT=Ubuntu]Post Mortem:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I think, after all, I had two independent bugs going on.  [/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I re-installed 14.04  and the display freeze with REISUB access continued, traced that to the Nouveau driver and NVIIDIA video card bug freezing the display.  Switched to the NVIDIA proprietary/tested driver and resolved that behavior.  The total system freeze in 16.04 had occurred with any of the NVIDIA drivers as well as the Nouveau driver, and in 2D gnome as well, so I think that was a different bug.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
With the NVIDIA driver active I independently checked each USB device (mouse, etc), and each memory module solo.  No hardware issues or memory failures or freezes.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I think the total system freeze was specific to 16.04 since the hardware is working fine in 14.04, but couldn't diagnose it, I'm going to stick with 14.04 for now until I get some high priority work out of the way.[/FONT][/COLOR]

---

### Post by mfox on 2016-07-13
I am in much the same boat with random freezes in 16.04. Also using Nvidia driver, but got freezes with Nouveau. I didn't have them before 16.04. So my question is whether reverting to 14.04 solved your problem?

---

