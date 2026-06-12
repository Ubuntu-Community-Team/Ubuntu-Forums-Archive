---
title: "No boot to desktop- what went wrong?"
date: 2018-03-05
forum: General Help
---

### Post by tnthomas on 2018-03-05
I recently put a Samsumg 960 EVO M.2 drive in my Dell Inspiron 15 7567 laptop, wanted some of that fast boot goodness. ;)      Installed 16.04(Mate) without incident.    

All was good until yesterday.   Turned on laptop, got to login screen, logged in but would never progress beyond the Ubuntu 'splashscreen.'

I booted to a live session, grabbed my data out of /home and reinstalled.

Just for future reference, what went wrong?     What could I do to repair, rather than doing a re-install?

---

### Post by oldfred on 2018-03-06
By re-installing we lost whatever issue you may have had.
You may have been able to run Boot-Repair's summary report or other specific commands to see configuration and if something was not correct.

We do like to fix things even if it takes days, weeks and sometimes a reinstall is quicker. :)

I do like to have data separate from operating system. If a newer user then a separate /home as that does mount and sets ownership & permissions as part of install. If a bit more advanced and understand a bit of fstab, mounts, ownership & permissions or want to learn a separate /mnt/data partition should be a consideration. I use the data partition as I have more than one install, but want same data, but not necessarily same settings from /home in all my installs.

This may not show much now, but I run it or bootinfoscript which is the first part of it and can be run from my rsync backup just to have details of my configuration.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tnthomas on 2018-03-06
> **oldfred said:**
> By re-installing we lost whatever issue you may have had.
You may have been able to run Boot-Repair's summary report or other specific commands to see configuration and if something was not correct.

We do like to fix things even if it takes days, weeks and sometimes a reinstall is quicker. :)

I do like to have data separate from operating system. If a newer user then a separate /home as that does mount and sets ownership & permissions as part of install. If a bit more advanced and understand a bit of fstab, mounts, ownership & permissions or want to learn a separate /mnt/data partition should be a consideration. I use the data partition as I have more than one install, but want same data, but not necessarily same settings from /home in all my installs.

This may not show much now, but I run it or bootinfoscript which is the first part of it and can be run from my rsync backup just to have details of my configuration.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)


[SIZE=3]Thanks for your reply.     So, what could I have done at the log-in screen, besides rebooting or logging in?[/SIZE]






[SIZE=3]
Once I did log in, all I had was a screen like the one below:

[/SIZE]






[SIZE=3]
I just would like to know how to fix my system, rather than doing a re-install.[/SIZE]

---

### Post by oldfred on 2018-03-06
Please attach screen shots, not post in line.
Easy to attach with paper clip icon in Forum's Advanced Editor.

Did you try booting with grub menu's advanced options and recovery mode?
If you do not get menu, you have to use shift if a BIOS boot system or escape key if UEFI boot system.
Are you getting any warning currently in /etc/var/log various log files or using log file viewer (maybe system log now)?

If that does not work then:
You probably need to use live installer to run Boot-Repair.
And also mount system and check log files for errors or warnings.

---

### Post by tnthomas on 2018-03-06
> **oldfred said:**
> Please attach screen shots, not post in line.
Easy to attach with paper clip icon in Forum's Advanced Editor.

Did you try booting with grub menu's advanced options and recovery mode?
If you do not get menu, you have to use shift if a BIOS boot system or escape key if UEFI boot system.
Are you getting any warning currently in /etc/var/log various log files or using log file viewer (maybe system log now)?

If that does not work then:
You probably need to use live installer to run Boot-Repair.
And also mount system and check log files for errors or warnings.

I edited my post, dumped the inline images and attached instead.

I'm not getting a grub menu, system just goes to the log-in screen.  I didn't notice, since Ubuntu is the only OS on the laptop.  If I had been getting to a grub menu, I would have had options.

Looking at apport.log in the log file viewer indicates:

```
ERROR: apport (pid 12190) Sun Mar  4 23:05:27 2018: called for pid 1404, signal 11, core limit 0ERROR: apport (pid 12190) Sun Mar  4 23:05:27 2018: executable: /usr/bin/mate-panel (command line "mate-panel")
ERROR: apport (pid 12190) Sun Mar  4 23:05:27 2018: gdbus call error: Error connecting: Could not connect: Connection refused


ERROR: apport (pid 12190) Sun Mar  4 23:05:27 2018: debug: session gdbus call: 
ERROR: apport (pid 12190) Sun Mar  4 23:05:34 2018: wrote report /var/crash/_usr_bin_mate-panel.1000.crash
```

Not sure what that means.   I'll keep looking at the other logs.

---

### Post by oldfred on 2018-03-06
If only Ubuntu installed you do not get grub menu by default as it only has one system to boot.
If UEFI you must press Escape key between UEFI screen & grub menu to get grub menu. But if fast boot is on, you may not have time to press any key.
If BIOS you press & hold shift key from BIOS until grub menu appears.
If grub sees abnormal shutdown (REISUB preferred), then it usually shows grub menu as parameter not reset on shutdown.

Looked up apport.
It is the error reporting tool.
So some issue on Mate panel?

---

### Post by tnthomas on 2018-03-06
> **oldfred said:**
> 
If UEFI you must press Escape key between UEFI screen & grub menu to get grub menu. But if fast boot is on, you may not have time to press any key.

Now that is something I'll keep in mind.   This laptop boots up so screamin' fast with the 960 EVO.  \\:D/


> **oldfred said:**
> So some issue on Mate panel?

Well that apport.log snippet is from the  current install, but I'm not experiencing any *wonky* behavior with the laptop, ATM.    The screen that appeared_ after_ logging in might be

the result of the display having an error, and being waaay oversized, for the laptop screen.

---

### Post by tnthomas on 2018-03-06
Well, just  booted the laptop, and upon entering the desktop got a crash message(see [image]("https://i.imgur.com/cNZLXzs.png")).

Got quite a list from _usr_bin_mate-panel.1000.crash, in /var/crash:


```
R 0:906e9 TIME 1520390930 SOCKET 0 APIC 0 microcode 84
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: mce: [Hardware Error]: CPU 0: Machine Check: 0 Bank 9: ee2000000040110a
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: mce: [Hardware Error]: TSC 0 ADDR fef1ff00 MISC 3880010086 
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: mce: [Hardware Error]: PROCESSOR 0:906e9 TIME 1520390930 SOCKET 0 APIC 0 microcode 84
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel:  #2 #3
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: PCCT header not found.
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: i8042: Warning: Keylock active
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: wmi_bus wmi_bus-PNP0C14:02: WQBC data block query control method not found
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: MXM: GUID detected in BIOS
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: ACPI Warning: \_SB.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170531/nsarguments-95)
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: ACPI Warning: \_SB.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170531/nsarguments-95)
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: ACPI Warning: \_SB.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20170531/nsarguments-95)
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: i915 0000:00:02.0: Direct firmware load for i915/kbl_dmc_ver1_01.bin failed with error -2
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: nouveau 0000:01:00.0: Direct firmware load for nvidia/gp107/gr/sw_nonctx.bin failed with error -2
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: nouveau 0000:01:00.0: gr: failed to load gr/sw_nonctx
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: nouveau 0000:01:00.0: gr ctor failed, -2
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: nouveau: probe of 0000:01:00.0 failed with error -2
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: [drm:lspcon_init [i915]] *ERROR* Failed to probe lspcon
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: [drm:intel_ddi_init [i915]] *ERROR* LSPCON init failed on port B
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed40080 f80
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-29.ucode failed with error -2
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-28.ucode failed with error -2
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-27.ucode failed with error -2
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-26.ucode failed with error -2
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-25.ucode failed with error -2
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-24.ucode failed with error -2
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-23.ucode failed with error -2
 Mar 06 18:48:52 Inspiron-15-7000-Gaming kernel: i2c_hid i2c-DLL077C:00: i2c-DLL077C:00 supply vdd not found, using dummy regulator
 Mar 06 18:48:53 Inspiron-15-7000-Gaming systemd-tmpfiles[567]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
 Mar 06 18:48:53 Inspiron-15-7000-Gaming kernel: uvcvideo 1-12:1.0: Entity type for entity Extension 4 was not initialized!
 Mar 06 18:48:53 Inspiron-15-7000-Gaming kernel: uvcvideo 1-12:1.0: Entity type for entity Extension 3 was not initialized!
 Mar 06 18:48:53 Inspiron-15-7000-Gaming kernel: uvcvideo 1-12:1.0: Entity type for entity Processing 2 was not initialized!
 Mar 06 18:48:53 Inspiron-15-7000-Gaming kernel: uvcvideo 1-12:1.0: Entity type for entity Camera 1 was not initialized!
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: Failed to obtain handles for "Service Changed" characteristic
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: Not enough free handles to register service
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: Error adding Link Loss service
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: Not enough free handles to register service
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: Not enough free handles to register service
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: Not enough free handles to register service
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: Current Time Service could not be registered
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: gatt-time-server: Input/output error (5)
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: Not enough free handles to register service
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: Not enough free handles to register service
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: Sap driver initialization failed.
 Mar 06 18:48:54 Inspiron-15-7000-Gaming bluetoothd[780]: sap-server: Operation not permitted (1)
 Mar 06 18:48:54 Inspiron-15-7000-Gaming NetworkManager[778]: <warn>  [1520390934.5389] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
 Mar 06 18:48:54 Inspiron-15-7000-Gaming NetworkManager[778]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
 Mar 06 18:48:54 Inspiron-15-7000-Gaming NetworkManager[778]: <warn>  [1520390934.7074] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
 Mar 06 18:48:54 Inspiron-15-7000-Gaming wpa_supplicant[957]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
 Mar 06 18:48:54 Inspiron-15-7000-Gaming wpa_supplicant[957]: dbus: Failed to construct signal
 Mar 06 18:48:54 Inspiron-15-7000-Gaming wpa_supplicant[957]: Could not read interface p2p-dev-wlp3s0 flags: No such device
 Mar 06 18:48:55 Inspiron-15-7000-Gaming lightdm[968]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
 Mar 06 18:48:55 Inspiron-15-7000-Gaming lightdm[968]: PAM adding faulty module: pam_kwallet.so
 Mar 06 18:48:55 Inspiron-15-7000-Gaming lightdm[968]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
 Mar 06 18:48:55 Inspiron-15-7000-Gaming lightdm[968]: PAM adding faulty module: pam_kwallet5.so
 Mar 06 18:48:55 Inspiron-15-7000-Gaming lightdm[1026]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
 Mar 06 18:48:55 Inspiron-15-7000-Gaming lightdm[1026]: PAM adding faulty module: pam_kwallet.so
 Mar 06 18:48:55 Inspiron-15-7000-Gaming lightdm[1026]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
 Mar 06 18:48:55 Inspiron-15-7000-Gaming lightdm[1026]: PAM adding faulty module: pam_kwallet5.so
 Mar 06 18:49:00 Inspiron-15-7000-Gaming ntpd[1060]: error resolving pool 0.ubuntu.pool.ntp.org: Temporary failure in name resolution (-3)
 Mar 06 18:49:01 Inspiron-15-7000-Gaming ntpd[1060]: error resolving pool 1.ubuntu.pool.ntp.org: Temporary failure in name resolution (-3)
 Mar 06 18:49:02 Inspiron-15-7000-Gaming ntpd[1060]: error resolving pool 2.ubuntu.pool.ntp.org: Temporary failure in name resolution (-3)
 Mar 06 18:49:03 Inspiron-15-7000-Gaming ntpd[1060]: error resolving pool 3.ubuntu.pool.ntp.org: Temporary failure in name resolution (-3)
 Mar 06 18:49:04 Inspiron-15-7000-Gaming ntpd[1060]: error resolving pool ntp.ubuntu.com: Temporary failure in name resolution (-3)
 Mar 06 18:49:21 Inspiron-15-7000-Gaming org.gtk.vfs.Daemon[985]: A connection to the bus can't be made
 Mar 06 18:49:21 Inspiron-15-7000-Gaming org.a11y.Bus[1305]: Activating service name='org.a11y.atspi.Registry'
 Mar 06 18:49:21 Inspiron-15-7000-Gaming org.a11y.Bus[1305]: ** (process:1373): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
 Mar 06 18:49:21 Inspiron-15-7000-Gaming org.a11y.Bus[1305]: Successfully activated service 'org.a11y.atspi.Registry'
 Mar 06 18:49:21 Inspiron-15-7000-Gaming mate-session[1168]: WARNING: Unable to find provider '' of required component 'dock'
 Mar 06 18:49:22 Inspiron-15-7000-Gaming dnsmasq[1438]: warning: no upstream servers configured
 Mar 06 18:49:22 Inspiron-15-7000-Gaming pulseaudio[1596]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
 Mar 06 18:49:22 Inspiron-15-7000-Gaming pulseaudio[1712]: [pulseaudio] pid.c: Daemon already running.
 Mar 06 18:49:23 Inspiron-15-7000-Gaming kernel: show_signal_msg: 5 callbacks suppressed
 Mar 06 18:49:23 Inspiron-15-7000-Gaming org.blueman.Mechanism[747]: Failed to connect to Mir: Failed to connect to server socket: No such file or directory
 Mar 06 18:49:23 Inspiron-15-7000-Gaming org.blueman.Mechanism[747]: Unable to init server: Could not connect: Connection refused
 Mar 06 18:49:23 Inspiron-15-7000-Gaming org.blueman.Mechanism[747]: Failed to connect to Mir: Failed to connect to server socket: No such file or directory
 Mar 06 18:49:23 Inspiron-15-7000-Gaming org.blueman.Mechanism[747]: Unable to init server: Could not connect: Connection refused
 Mar 06 18:49:23 Inspiron-15-7000-Gaming org.blueman.Mechanism[747]: (blueman-mechanism:1810): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
 Mar 06 18:49:26 Inspiron-15-7000-Gaming org.gtk.vfs.Daemon[1305]: ** (gvfsd:1377): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
 Mar 06 18:49:26 Inspiron-15-7000-Gaming org.gtk.vfs.Daemon[1305]: ** (process:1801): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Package: mate-panel 1.12.2-1
PackageArchitecture: amd64
ProcCpuinfoMinimal:
 processor    : 3
 vendor_id    : GenuineIntel
 cpu family    : 6
 model        : 158
 model name    : Intel(R) Core(TM) i5-7300HQ CPU @ 2.50GHz
 stepping    : 9
 microcode    : 0x84
 cpu MHz        : 2500.000
 cache size    : 6144 KB
 physical id    : 0
 siblings    : 4
 core id        : 3
 cpu cores    : 4
 apicid        : 6
 initial apicid    : 6
 fpu        : yes
 fpu_exception    : yes
 cpuid level    : 22
 wp        : yes
 flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti retpoline intel_pt rsb_ctxsw spec_ctrl tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp
 bugs        : cpu_meltdown spectre_v1 spectre_v2
 bogomips    : 4992.00
 clflush size    : 64
 cache_alignment    : 64
 address sizes    : 39 bits physical, 48 bits virtual
 power management:
ProcVersionSignature: Ubuntu 4.13.0-36.40~16.04.1-generic 4.13.13
Registers:
 rax            0x0    0
 rbx            0x420660    4327008
 rcx            0x4    4
 rdx            0x1564980    22432128
 rsi            0x169bc80    23706752
 rdi            0xffffd510e9000002    -47206371426302
 rbp            0x169bc80    0x169bc80
 rsp            0x7fff712c66a0    0x7fff712c66a0
 r8             0x1517d50    22117712
 r9             0x1    1
 r10            0x3f0    1008
 r11            0x4    4
 r12            0x169bc80    23706752
 r13            0x420660    4327008
 r14            0x0    0
 r15            0x12    18
 rip            0x7ffa45cc6b6c    0x7ffa45cc6b6c <g_slist_remove_all+44>
 eflags         0x10282    [ SF IF RF ]
 cs             0x33    51
 ss             0x2b    43
 ds             0x0    0
 es             0x0    0
 fs             0x0    0
 gs             0x0    0
SegvAnalysis:
 Segfault happened at: 0x7ffa45cc6b6c <g_slist_remove_all+44>:    cmp    %rbp,(%rdi)
 PC (0x7ffa45cc6b6c) ok
 source "%rbp" ok
 destination "(%rdi)" (0xffffd510e9000002) not located in a known VMA region (needed writable region)!
SegvReason: writing unknown VMA
SourcePackage: mate-panel
Stacktrace:
 #0  0x00007ffa45cc6b6c in g_slist_remove_all () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #1  0x00007ffa47545802 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #2  0x00007ffa45c98340 in g_hash_table_foreach () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x00007ffa47547d7b in gtk_rc_reset_styles () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #4  0x00007ffa475677ed in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #5  0x00007ffa45f7ffa5 in g_closure_invoke () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #6  0x00007ffa45f91afc in ?? () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #7  0x00007ffa45f9ad5c in g_signal_emit_valist () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #8  0x00007ffa45f9b08f in g_signal_emit () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #9  0x00007ffa45f844d4 in ?? () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #10 0x00007ffa45f86961 in g_object_notify () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #11 0x00007ffa4756b615 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #12 0x00007ffa474ff705 in gtk_main_do_event () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #13 0x00007ffa47173c8c in ?? () from /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0
 No symbol table info available.
 #14 0x00007ffa45ca9197 in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #15 0x00007ffa45ca93f0 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #16 0x00007ffa45ca9712 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #17 0x00007ffa474fe697 in gtk_main () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #18 0x00000000004224cc in main ()
 No symbol table info available.
StacktraceAddressSignature: /usr/bin/mate-panel:11:/lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.2+67b6c:/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.30+177802:/lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.2+39340:/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.30+179d7b:/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.30+1997ed:/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.2+ffa5:/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.2+21afc:/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.2+2ad5c:/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.2+2b08f:/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.2+144d4:/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.2+16961:/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.30+19d615:/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0.2400.30+131705:/usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0.2400.30+5ac8c:/lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.2+4a197
StacktraceTop:
 g_slist_remove_all () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 ?? () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 g_hash_table_foreach () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 gtk_rc_reset_styles () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 ?? () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
Tags:  xenial
ThreadStacktrace:
 .
 Thread 6 (Thread 0x7ffa361d0700 (LWP 1741)):
 #0  0x00007ffa44f2b499 in syscall () from /lib/x86_64-linux-gnu/libc.so.6
 No symbol table info available.
 #1  0x00007ffa45cedcfa in g_cond_wait_until () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #2  0x00007ffa45c7d999 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x00007ffa45cd0526 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #4  0x00007ffa45ccfbb5 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #5  0x00007ffa451fb6ba in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 No symbol table info available.
 #6  0x00007ffa44f313dd in clone () from /lib/x86_64-linux-gnu/libc.so.6
 No symbol table info available.
 .
 Thread 5 (Thread 0x7ffa369d1700 (LWP 1601)):
 #0  0x00007ffa44f2b499 in syscall () from /lib/x86_64-linux-gnu/libc.so.6
 No symbol table info available.
 #1  0x00007ffa45cedcfa in g_cond_wait_until () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #2  0x00007ffa45c7d999 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x00007ffa45cd0526 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #4  0x00007ffa45ccfbb5 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #5  0x00007ffa451fb6ba in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 No symbol table info available.
 #6  0x00007ffa44f313dd in clone () from /lib/x86_64-linux-gnu/libc.so.6
 No symbol table info available.
 .
 Thread 4 (Thread 0x7ffa373d8700 (LWP 1591)):
 #0  0x00007ffa44f2570d in poll () from /lib/x86_64-linux-gnu/libc.so.6
 No symbol table info available.
 #1  0x00007ffa45ca938c in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #2  0x00007ffa45ca949c in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x00007ffa37dfa28d in ?? () from /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
 No symbol table info available.
 #4  0x00007ffa45ccfbb5 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #5  0x00007ffa451fb6ba in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 No symbol table info available.
 #6  0x00007ffa44f313dd in clone () from /lib/x86_64-linux-gnu/libc.so.6
 No symbol table info available.
 .
 Thread 3 (Thread 0x7ffa3cbc6700 (LWP 1590)):
 #0  0x00007ffa44f2570d in poll () from /lib/x86_64-linux-gnu/libc.so.6
 No symbol table info available.
 #1  0x00007ffa45ca938c in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #2  0x00007ffa45ca9712 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x00007ffa462a79d6 in ?? () from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
 No symbol table info available.
 #4  0x00007ffa45ccfbb5 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #5  0x00007ffa451fb6ba in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 No symbol table info available.
 #6  0x00007ffa44f313dd in clone () from /lib/x86_64-linux-gnu/libc.so.6
 No symbol table info available.
 .
 Thread 2 (Thread 0x7ffa3d3c7700 (LWP 1589)):
 #0  0x00007ffa44f2570d in poll () from /lib/x86_64-linux-gnu/libc.so.6
 No symbol table info available.
 #1  0x00007ffa45ca938c in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #2  0x00007ffa45ca949c in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x00007ffa45ca94d9 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #4  0x00007ffa45ccfbb5 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #5  0x00007ffa451fb6ba in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 No symbol table info available.
 #6  0x00007ffa44f313dd in clone () from /lib/x86_64-linux-gnu/libc.so.6
 No symbol table info available.
 .
 Thread 1 (Thread 0x7ffa48a1ba40 (LWP 1412)):
 #0  0x00007ffa45cc6b6c in g_slist_remove_all () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #1  0x00007ffa47545802 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #2  0x00007ffa45c98340 in g_hash_table_foreach () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #3  0x00007ffa47547d7b in gtk_rc_reset_styles () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #4  0x00007ffa475677ed in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #5  0x00007ffa45f7ffa5 in g_closure_invoke () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #6  0x00007ffa45f91afc in ?? () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #7  0x00007ffa45f9ad5c in g_signal_emit_valist () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #8  0x00007ffa45f9b08f in g_signal_emit () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #9  0x00007ffa45f844d4 in ?? () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #10 0x00007ffa45f86961 in g_object_notify () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #11 0x00007ffa4756b615 in ?? () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #12 0x00007ffa474ff705 in gtk_main_do_event () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #13 0x00007ffa47173c8c in ?? () from /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0
 No symbol table info available.
 #14 0x00007ffa45ca9197 in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #15 0x00007ffa45ca93f0 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #16 0x00007ffa45ca9712 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #17 0x00007ffa474fe697 in gtk_main () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
 No symbol table info available.
 #18 0x00000000004224cc in main ()
 No symbol table info available.
Title: mate-panel crashed with SIGSEGV in g_slist_remove_all()
UnreportableReason:
 You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:
 
 apt, apt-utils, bsdutils, dpkg, gcc-5-base, libapparmor1, libapt-inst2.0, libapt-pkg5.0, libaudit-common, libaudit1, libblkid1, libc6, libcryptsetup4, libcups2, libdb5.3, libdrm-amdgpu1, libdrm-intel1, libdrm-nouveau2, libdrm-radeon1, libdrm2, libegl1-mesa, libfdisk1, libgbm1, libgd3, libgdk-pixbuf2.0-0, libgdk-pixbuf2.0-common, libgl1-mesa-dri, libgl1-mesa-glx, libglapi-mesa, libgnutls30, libgraphite2-3, libgtk2.0-0, libgtk2.0-bin, libgtk2.0-common, libicu55, libidn11, libjavascriptcoregtk-4.0-18, libllvm4.0, libmirclient9, libmircommon7, libmircore1, libmirprotobuf3, libmount1, libpam-systemd, libpython-stdlib, libpython2.7-minimal, libpython2.7-stdlib, libseccomp2, libsmartcols1, libsoup-gnome2.4-1, libsoup2.4-1, libssl1.0.0, libstdc++6, libsystemd0, libtasn1-6, libudev1, libuuid1, libvorbis0a, libvorbisenc2, libvorbisfile3, libwavpack1, libwayland-client0, libwayland-cursor0, libwayland-egl1-mesa, libwayland-server0, libwebkit2gtk-4.0-37, libxcursor1, libxml2, mount, multiarch-support, perl-base, python, python-minimal, python2.7, python2.7-minimal, sensible-utils, systemd, ubuntu-mono, udev, util-linux, uuid-runtime
UpgradeStatus: No upgrade log present (probably fresh install)
XsessionErrors:
 mate-session[1168]: WARNING: Unable to find provider '' of required component 'dock'
 (mate-panel:1412): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
 (blueman-applet:1676): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates: assertion 'window->update_and_descendants_freeze_count > 0' failed
 (nm-applet:1623): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates: assertion 'window->update_and_descendants_freeze_count > 0' failed
 
_MarkForUpload: True
root@Inspiron-15-7000-Gaming:/var/crash# 
 
```


Hardware problems, or driver issues?    I updated the BIOS to the latest version, before the original Ubuntu install.

---

### Post by oldfred on 2018-03-06
I see nouveau, do you have nVidia card/chip? What model?
And have you installed nVidia driver from repository?
Or if very new chip, added ppa and installed?

       17.10 defaults to wayland where nvidia's driver don't work 
   [https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959](https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959) by 1fallen
> EDIT: This seems to work for my card here, instead of using "nomodeset" I am using this "nogpumanager"
And I have to watch carefully any changes made to "/etc/X11/xorg.conf" 
   nVidia Must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by tnthomas on 2018-03-07
Yes, a GTX 1050. I had not changed the video driver, from what was provided during the initial install.   A couple months back i had installed an nVidia Linux driver (v384) using the Additional Drivers feature.  That resulted in a black screen with a blinking cursor,  so we didn't try that again.

---

### Post by oldfred on 2018-03-07
I might then try the purge to totally remove 384 and add the ppa to get the newest nVidia drivers.
Then add whichever is newest.
I believe the 1050 is very new, newer than some with higher numbers and needed driver updated from nVidia.

---

### Post by tnthomas on 2018-03-07
I shall use the information you provided, and install the latest nVidia driver this weekend. :thanks:

   I don't game, but I do participate in [Folding@Home]("https://en.wikipedia.org/wiki/Folding@home").  The gtx1050 in the laptop is currently the only video card in any of my machines that have a significant number of CUDA cores, which f@h needs to run on.  Because of heating concerns, I would only run f@h on a laptop for shorter periods of time.   Certainly not when the weather gets warm.

---

### Post by hrsetrdr on 2018-05-14
> **tnthomas said:**
> I shall use the information you provided, and install the latest nVidia driver this weekend. :thanks:


This is actually me, until I recovered my original account([this post]("https://ubuntuforums.org/showthread.php?t=2386869")), and the laptop is the same.  After the last 16.04 re-install I went along while 

everything was going good, and didn't bother installing the nVidia drivers.  But, once again the desktop never fully deployed after log-in(see posts 1&3) so I reinstalled Ubuntu, this time I went ahead and installed the 

384  nVidia drivers.  I want to be able to fix the system when it breaks, even though a reinstall can be so much easier & quicker.

---

### Post by oldfred on 2018-05-14
Do you also have the latest UEFI from Dell?

The Intel issues called Meltdown and Spectre have required both UEFI/BIOS updates and kernel updates.
Also not just Intel chip systems as some of issues apply to AMD, IBM mainframes and Raspberry Pi.

---

### Post by hrsetrdr on 2018-05-14
Yes, I updated with  the BIOS version dated 12 Apr 2018.    In order to use the BIOS update which is a Windows executable, I used the Del Dell Digital Delivery Application to download and create installation media for the original Dell Windows 10.  I put it on the original hybrid drive, used it to install the firmware update then removed & archived the drive.    Then I was free to install the Samsung 960 EVO and put some Linux goodness on it.  ;)

---

### Post by oldfred on 2018-05-14
Can you then boot recovery mode? To command line/terminal? And its menu of repairs.

---

### Post by hrsetrdr on 2018-05-14
> **oldfred said:**
> Can you then boot recovery mode? To command line/terminal? And its menu of repairs.

I just used the Recovery Menu:

[ATTACH=CONFIG]279690[/ATTACH]


I did not explore the terminal menu of repairs...probably should have.

---

### Post by oldfred on 2018-05-14
If it did boot, then it seems to still need nomodeset.
The recovery mode has nomodeset as a boot parameter. But once nVidia driver is installed (and working), you should not need nomodeset.

---

### Post by hrsetrdr on 2018-05-14
Well the nVidia 384 driver is now installed, will be interested in seeing no more display problems.  I finally got my head wrapped around the "nomodeset" boot option, there's a ray of hope if the display goes south again.

I never ever had this problem before. Is it a "Dell" problem, or "nVidia" problem due to the high end nature of the card, rather than being just a 'display' adaptor?

---

### Post by hrsetrdr on 2018-05-14
I've seen several "blank screen" threads regarding the 18.04 installation, laptops I think.   So, would using "nomodeset"  be the remedy for that?

---

### Post by oldfred on 2018-05-14
I seem to be seeing a variety of  video settings that seem to help.
It used to be only AMD & nVidia needed nomodeset. The it was just nVidia newer cards. My older card did not need it then. But now it does again.
And then AMD seemed to just work, but now not always?
And even Intel may need settings depending on chip and system.

---

### Post by hrsetrdr on 2018-05-14
I'm looking to understand more about nomodeset, I found an[ article]("https://ask.fedoraproject.org/en/question/46846/what-does-nomodeset-do/")

> The nomodeset boot parameter disables KMS (Kernel Mode Setting), have a look at this for more info: [http://www.x.org/wiki/ModeSetting/](http://www.x.org/wiki/ModeSetting/)

Nowadays, most open source graphics drivers in Linux require KMS and can't work without it; so for example if you have an intel graphics card and disable KMS the system will automatically fallback to the VESA driver, which is not as powerful/feature-full.

nomodeset is added to the boot parameters if you boot the installation media with the "basic graphics mode" boot entry; consequently nomodeset is added to the kernel command line in the installed system.

To remove nomodeset altogether you'll have to remove it from /boot/grub2/grub.cfg (if you have a UEFI system then it's /boot/efi/EFI/fedora/grub.cfg). And to ensure any subsequent runs of grub2-mkconfig don't add nomodeset back to grub.cfg you'll also need to edit /etc/default/grub (specifically the GRUB_CMDLINE_LINUX line).


So if nomodeset is added to the boot parameter then the system will use the vesa driver, which will prevent the display problems mentioned? 



Update:  a couple posts back I had installed the nVidia 384 display driver, though the System>Preferences>Hardware>Additional Drivers menu .   Well, I just noticed that it in fact did not install, and that the Nouveau driver is running.

Will having the VESA or the proprietary nVidia driver prevent the display issues?


I re-installed the nVidia 384 display driver and will reboot in just a second.  If my laptop display goes wonky, I'll be posting back here from my Android tablet.  ;)

---

### Post by oldfred on 2018-05-15
I know there are always issues of installing a different nVidia driver. You have to purge first to make sure there are no conflicts.
But not sure if just reinstalling creates any issues or not.

       #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 


 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices

---

