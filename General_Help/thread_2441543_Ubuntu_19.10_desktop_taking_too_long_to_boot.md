---
title: "Ubuntu 19.10 desktop taking too long to boot"
date: 2020-04-24
forum: General Help
---

### Post by tech291083 on 2020-04-24
Dear friends,

Hope you are doing fine. I am happy that I was able to install Ubuntu 19.10 64 bit Desktop onto a brand new 500 GB hard drive without any glitch whatsoever, but after having updated and installing a few packages manually I am facing a weird issue now. Whenever I try to boot Ubuntu I just see a black screen and nothing else, while the PC is running properly and not shutting itself down or restarting at random, for no apparent reason. Ubuntu does not boot even if I wait for an hour. Can you please guide me as to what might have gone wrong? How can I get into rescue mode, if any?Thanks 

I have posted a small video showing what the actual problem is. Thanks

[https://imgur.com/a/mU5ksq2](https://imgur.com/a/mU5ksq2)

---

### Post by kc1di on 2020-04-24
A couple thing come to mind.  One would be your Video Card If it is Nvidia you'll need to add an entry in the boot line in grub 
"nomodset"  you can see how to do that [here: ]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu")
secondly If it were me I would download and install the latest version 20.04  Because 19.10 will be end of live in July 2020. 20.04 will be supported for 5 years. 
Good Luck.

---

### Post by ActionParsnip on 2020-04-24
If you run:

```

dmesg > ~/Desktop/dmesg.txt; gedit ~/Desktop/dmesg.txt

```

Look down the left hand side for large gaps in time. It will help show where the issue is....

---

### Post by tech291083 on 2020-04-24
> **kc1di said:**
> One would be your Video Card If it is Nvidia you'll need to add an entry in the boot line in grub 
"nomodset" you can see how to do that here: 



I am not using a dedicated video card or graphics card. My motherboard is a simple one, a link to which is given below.


[https://www.gigabyte.com/in/Motherboard/GA-H61M-S-rev-10#ov](https://www.gigabyte.com/in/Motherboard/GA-H61M-S-rev-10#ov)



> 
secondly If it were me I would download and install the latest version 20.04 Because 19.10 will be end of live in July 2020. 20.04 will be supported for 5 years. 



Sure, I will do so soon.

---

### Post by tech291083 on 2020-04-24
> **ActionParsnip said:**
> If you run:

```

dmesg > ~/Desktop/dmesg.txt; gedit ~/Desktop/dmesg.txt

```

Look down the left hand side for large gaps in time. It will help show where the issue is....

Thanks, I will post these files here when I am finally able to boot properly.

---

### Post by kc1di on 2020-04-24
If you can get to a terminal (command line) enter this command and post the out back here. ```
systemd-analyze blame
```

---

### Post by CelticWarrior on 2020-04-24
You're using an embedded GPU in the CPU. The motherboard itself has no iGPU so it would have been useful the information about the processor, the motherboard is irrelevant in this case. But also although possible a CPU failure is extremely unlikely and it shows video output in the beginning so...

You can ignore for now the suggestion about 'nomodeset' which isn't applicable.
You may try to press ESC while the Ubuntu logo is visible or even in the black screen to check if there are error messages.
If nothing shows up try CTRL+ALT+F3 which hopefully will give a functional TTY (command line) where further troubleshooting can be tried.

Meanwhile...
What exactly have you "manually installed"? Something to do with desktop environments?

---

### Post by tech291083 on 2020-04-24
> 
You can ignore for now the suggestion about 'nomodeset' which isn't applicable.

OK, that is exactly what I was thinking initially, but you have now confirmed it.


> 
If nothing shows up try CTRL+ALT+F3 which hopefully will give a functional TTY (command line) where further troubleshooting can be tried.



Yes, I will try this.


> 
What exactly have you "manually installed"? Something to do with desktop environments?



Correct. I installed cinnamon and mate desktop environments manually just to try them out. Actually I was following a techmint.com article titled "20 Things To Do After Installing Ubuntu 19.10 &#8216;Eoan Ermine" and item 18 was "18. Try Different Desktop Environments".

[https://www.tecmint.com/things-to-do-after-installing-ubuntu/](https://www.tecmint.com/things-to-do-after-installing-ubuntu/)

I have this habit of taking screen-shots whenever I am installing something for the very 1st time and I would like you to visit the following link, which has them listed and only point to the very fact that I installed cinnamon and mate desktop environments manually just to try them out.

[https://imgur.com/a/fcZkCFM](https://imgur.com/a/fcZkCFM)

I try many Linux distros and Ubuntu is one of my favorites. Everything I learn about Ubuntu or any other Linux distro comes from the internet or YouTube. I like to try things out on my own 1st and if things go wrong, I seek help here. 

Thanks a lot.

---

### Post by CelticWarrior on 2020-04-24
Installing other DEs from the respective meta-packages available in the official repositories as you did, apparently, is thought to be safe. That said, I suspect there was a problem with the display manager somewhere during that process.

You may try in the TTY - really, it can't hurt - to reconfigure the default one in vanilla Ubuntu 20.04:
```
sudo dpkg-reconfigure gdm3
```
Use directional keys to select again 'gdm3', then TAB to highlight OK and finally ENTER. Use this as a reference: [https://www.linuxuprising.com/2018/12/how-to-change-default-display-manager.html](https://www.linuxuprising.com/2018/12/how-to-change-default-display-manager.html)

---

### Post by tech291083 on 2020-04-25
> **CelticWarrior said:**
> 
If nothing shows up try CTRL+ALT+F3 which hopefully will give a functional TTY (command line) where further troubleshooting can be tried.



Yes, I somehow tried CTRL+ALT+F3 which gave me a functional TTY, thanks. I then inserted an pen drive and then ran 3 commands and redirected their outputs to 3 separate text files and then copied these text files to the pen drive itself, so that fellow members of this forum can have a look and further guide me, thanks.

All I did to copy these text files to the pen drive was to follow the below steps..

Make a directory in the /media folder named "usbpendrive" and then mounted the pen drive onto this directory by running the command "mount /dev/sdb /media/usbpendrive" an then I ran the command "cd /media/usbpendrive" and then "ls" and finally "cp errorfiles.txt /media/usbpendrive" and "umount /media/usbpendrive". But I had to wait for 30 minutes or more just to be able to unmount the pen drive safely, but I did not allow me to do so and kept saying "target is busy", so I finally got fed up and just pulled out my pen drive manually, but the text files were copied properly. Did I follow the right process? Thanks

[https://imgur.com/a/prAmAtl](https://imgur.com/a/prAmAtl)

---

### Post by tech291083 on 2020-04-25
> **kc1di said:**
> 
If you can get to a terminal (command line) enter this command and post the out back here. ```
systemd-analyze blame
```


Below it is, please help, thanks.

```

systemd-analyze blame
         46.199s postgresql@11-main.service 
         38.476s mysql.service
         26.301s udisks2.service
         21.367s networkd-dispatcher.service
         11.966s nmbd.service
         11.932s accounts-daemon.service
         10.672s NetworkManager-wait-online.service
         10.428s apache2.service
          8.113s dev-sda2.device
          7.825s NetworkManager.service
          7.697s bind9.service
          7.649s grub-common.service
          7.419s spice-vdagent.service
          7.279s grub-initrd-fallback.service
          7.202s rsyslog.service
          7.142s wpa_supplicant.service
          7.136s systemd-logind.service
          7.021s pppd-dns.service
          6.968s rtirq.service
          6.908s avahi-daemon.service
          5.082s dev-loop0.device
          5.071s dev-loop6.device
          5.055s dev-loop10.device
          5.055s dev-loop7.device
          4.970s dev-loop12.device
          4.897s dev-loop2.device
          4.795s dev-loop13.device
          4.776s dev-loop8.device
          4.703s dev-loop11.device
          4.678s dev-loop9.device
          4.588s dev-loop4.device
          4.087s ssh.service
          3.319s dev-loop1.device
          2.365s smbd.service
          2.292s apparmor.service
          2.198s postfix@-.service
          2.019s user@1000.service
          1.675s winbind.service
          1.519s systemd-resolved.service
          1.490s polkit.service
          1.476s dev-loop5.device
          1.470s dev-loop3.device
          1.400s systemd-journal-flush.service
          1.340s systemd-udevd.service
           886ms systemd-modules-load.service
           866ms systemd-tmpfiles-setup-dev.service
           824ms keyboard-setup.service
           770ms snap-gnome\x2dcharacters-317.mount
           769ms snap-core-8935.mount
           767ms systemd-tmpfiles-setup.service
           756ms snap-gtk\x2dcommon\x2dthemes-1502.mount
           713ms snap-gnome\x2dlogs-81.mount
           690ms snap-gnome\x2dcharacters-495.mount
           675ms systemd-sysusers.service
           662ms snap-gnome\x2dlogs-93.mount
           620ms systemd-udev-trigger.service
           619ms systemd-sysctl.service
           531ms snap-gnome\x2d3\x2d28\x2d1804-71.mount
           524ms systemd-timesyncd.service
           515ms systemd-journald.service
           469ms swapfile.swap
           418ms switcheroo-control.service
           381ms snap-gnome\x2d3\x2d28\x2d1804-116.mount
           362ms apport.service
           358ms sysstat.service
           334ms systemd-user-sessions.service
           261ms snap-gnome\x2dcalculator-501.mount
           255ms setvtrgb.service
           229ms kmod-static-nodes.service
           221ms systemd-remount-fs.service
           195ms dev-mqueue.mount
           177ms snap-gnome\x2dcalculator-704.mount
           173ms systemd-fsck@dev-disk-by\x2duuid-1B1B\x2dBF00.service
           170ms ufw.service
           169ms console-setup.service
           151ms snap-core-7917.mount
           142ms snap-core18-1705.mount
           141ms plymouth-read-write.service
           140ms boot-efi.mount
           132ms systemd-update-utmp.service
           130ms snap-core18-1223.mount
           110ms plymouth-quit.service
           109ms plymouth-quit-wait.service
            98ms rtkit-daemon.service
            98ms systemd-random-seed.service
            95ms snap-gtk\x2dcommon\x2dthemes-1506.mount
            92ms motd-news.service
            89ms sys-kernel-debug.mount
            76ms phpsessionclean.service
            70ms plymouth-start.service
            63ms hddtemp.service
            61ms user-runtime-dir@1000.service
            55ms systemd-tmpfiles-clean.service
            19ms postgresql.service
            11ms systemd-update-utmp-runlevel.service
            11ms gdm3.service
             5ms dev-hugepages.mount
             4ms lightdm.service
             4ms cron-php-root-0.service
             3ms cron-sysstat-root-0.service
             3ms sys-kernel-config.mount
             3ms sys-fs-fuse-connections.mount

```

---

### Post by tech291083 on 2020-04-25
> **ActionParsnip said:**
> If you run:

```

dmesg > ~/Desktop/dmesg.txt; gedit ~/Desktop/dmesg.txt

```

Look down the left hand side for large gaps in time. It will help show where the issue is....

Below are the contents of the var/log/dmesg file.
As you know the actual output is too long, so I am only posting the last few lines here. Thanks.

```

[    1.478124] kernel: usb 1-1.2: Product: USB Optical Mouse
[    1.478125] kernel: usb 1-1.2: Manufacturer: Logitech
[    1.513250] kernel: usb 2-1.5: New USB device found, idVendor=04d9, idProduct=1702, bcdDevice= 4.06
[    1.513252] kernel: usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.513253] kernel: usb 2-1.5: Product: USB Keyboard
[    1.513253] kernel: usb 2-1.5: Manufacturer:  
[    1.577240] kernel: ata2.00: failed to resume link (SControl 30)
[    1.893254] kernel: ata1.01: failed to resume link (SControl 0)
[    2.053310] kernel: ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[    2.053320] kernel: ata1.01: SATA link down (SStatus 0 SControl 0)
[    2.056069] kernel: ata1.00: HPA detected: current 976771055, native 976773168
[    2.056072] kernel: ata1.00: ATA-8: ST3500414CS, CA12, max UDMA/133
[    2.056073] kernel: ata1.00: 976771055 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.061097] kernel: ata1.00: configured for UDMA/133
[    2.061299] kernel: scsi 0:0:0:0: Direct-Access     ATA      ST3500414CS      CA12 PQ: 0 ANSI: 5
[    2.061646] kernel: sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.061761] kernel: sd 0:0:0:0: [sda] 976771055 512-byte logical blocks: (500 GB/466 GiB)
[    2.061802] kernel: sd 0:0:0:0: [sda] Write Protect is off
[    2.061803] kernel: sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.061891] kernel: sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.107648] kernel:  sda: sda1 sda2
[    2.108058] kernel: sd 0:0:0:0: [sda] Attached SCSI disk
[    2.617239] kernel: ata2.01: failed to resume link (SControl 0)
[    2.627961] kernel: ata2.00: SATA link down (SStatus 4 SControl 30)
[    2.627973] kernel: ata2.01: SATA link down (SStatus 0 SControl 0)
[    2.629128] kernel: scsi 3:0:0:0: CD-ROM            ASUS     DRW-24D5MT       2.00 PQ: 0 ANSI: 5
[    2.688421] kernel: sr 3:0:0:0: [sr0] scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.688424] kernel: cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.688651] kernel: sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.688700] kernel: sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.689732] kernel: Freeing unused decrypted memory: 2040K
[    2.690066] kernel: Freeing unused kernel image memory: 2676K
[    2.690109] kernel: Write protecting the kernel read-only data: 22528k
[    2.690464] kernel: Freeing unused kernel image memory: 2008K
[    2.690682] kernel: Freeing unused kernel image memory: 1420K
[    2.699172] kernel: x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    2.699173] kernel: x86/mm: Checking user space page tables
[    2.707580] kernel: x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    2.707582] kernel: Run /init as init process
[    2.797507] kernel: ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20190703/utaddress-204)
[    2.797514] kernel: ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.797517] kernel: ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20190703/utaddress-204)
[    2.797522] kernel: ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.797523] kernel: ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20190703/utaddress-204)
[    2.797527] kernel: ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.797528] kernel: ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000051F (\LED) (20190703/utaddress-204)
[    2.797532] kernel: ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20190703/utaddress-204)
[    2.797536] kernel: ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.797536] kernel: lpc_ich: Resource conflict(s) found affecting gpio_ich
[    2.799394] kernel: hidraw: raw HID events driver (C) Jiri Kosina
[    2.808145] kernel: i801_smbus 0000:00:1f.3: enabling device (0001 -> 0003)
[    2.808354] kernel: i801_smbus 0000:00:1f.3: SMBus using PCI interrupt
[    2.821157] kernel: libphy: r8169: probed
[    2.821364] kernel: r8169 0000:02:00.0 eth0: RTL8168g/8111g, e0:d5:5e:08:9c:1d, XID 4c0, IRQ 26
[    2.821366] kernel: r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.829203] kernel: usbcore: registered new interface driver usbhid
[    2.829204] kernel: usbhid: USB HID core driver
[    2.834160] kernel: cryptd: max_cpu_qlen set to 1000
[    2.837935] kernel: input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:046D:C077.0001/input/input2
[    2.839020] kernel: r8169 0000:02:00.0 enp2s0: renamed from eth0
[    2.839706] kernel: hid-generic 0003:046D:C077.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.0-1.2/input0
[    2.839880] kernel: input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/0003:04D9:1702.0002/input/input3
[    2.874292] kernel: checking generic (e0000000 300000) vs hw (e0000000 10000000)
[    2.874293] kernel: fb0: switching to inteldrmfb from EFI VGA
[    2.874367] kernel: Console: switching to colour dummy device 80x25
[    2.874407] kernel: i915 0000:00:02.0: vgaarb: deactivate vga console
[    2.874927] kernel: [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.874927] kernel: [drm] Driver supports precise vblank timestamp query.
[    2.875789] kernel: i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.882549] kernel: [drm] Initialized i915 1.6.0 20190619 for 0000:00:02.0 on minor 0
[    2.883097] kernel: ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.883269] kernel: input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    2.897448] kernel: hid-generic 0003:04D9:1702.0002: input,hidraw1: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.0-1.5/input0
[    2.897595] kernel: input:   USB Keyboard System Control as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/0003:04D9:1702.0003/input/input5
[    2.922058] kernel: fbcon: i915drmfb (fb0) is primary device
[    2.957361] kernel: input:   USB Keyboard Consumer Control as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/0003:04D9:1702.0003/input/input6
[    2.957494] kernel: hid-generic 0003:04D9:1702.0003: input,hidraw2: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.0-1.5/input1
[    3.020380] kernel: Console: switching to colour frame buffer device 240x67
[    3.040393] kernel: i915 0000:00:02.0: fb0: i915drmfb frame buffer device
[    3.387238] kernel: EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    4.879037] systemd[1]: Inserted module 'autofs4'
[    5.055394] systemd[1]: systemd 242 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD +IDN2 -IDN +PCRE2 default-hierarchy=hybrid)
[    5.073340] systemd[1]: Detected architecture x86-64.
[    5.081050] systemd[1]: Set hostname to <james-To-be-filled-by-O-E-M>.
[    5.106111] systemd[1]: Failed to bump fs.file-max, ignoring: Invalid argument
[    9.001421] systemd[1]: /lib/systemd/system/dbus.socket:4: ListenStream= references a path below legacy directory /var/run/, updating /var/run/dbus/system_bus_socket &#8594; /run/dbus/system_bus_socket; please update the unit file accordingly.
[    9.077332] systemd[1]: /lib/systemd/system/winbind.service:8: PIDFile= references a path below legacy directory /var/run/, updating /var/run/samba/winbindd.pid &#8594; /run/samba/winbindd.pid; please update the unit file accordingly.
[    9.318881] systemd[1]: /lib/systemd/system/smbd.service:9: PIDFile= references a path below legacy directory /var/run/, updating /var/run/samba/smbd.pid &#8594; /run/samba/smbd.pid; please update the unit file accordingly.
[    9.404726] systemd[1]: /lib/systemd/system/nmbd.service:9: PIDFile= references a path below legacy directory /var/run/, updating /var/run/samba/nmbd.pid &#8594; /run/samba/nmbd.pid; please update the unit file accordingly.
[    9.478052] systemd[1]: /lib/systemd/system/dovecot.service:9: PIDFile= references a path below legacy directory /var/run/, updating /var/run/dovecot/master.pid &#8594; /run/dovecot/master.pid; please update the unit file accordingly.
[    9.595310] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    9.918401] kernel: EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   10.092413] systemd[1]: Condition check resulted in Rebuild Hardware Database being skipped.
[   10.093276] systemd[1]: Starting Create System Users...
[   10.094020] systemd[1]: Starting Load/Save Random Seed...
[   10.192139] systemd[1]: Started Load/Save Random Seed.
[   10.216835] systemd[1]: Started Journal Service.
[   10.242900] kernel: lp: driver loaded but no devices found
[   10.278506] kernel: ppdev: user-space parallel port driver
[   10.389223] kernel: Adding 2097148k swap on /swapfile.  Priority:-2 extents:6 across:2260988k FS
[   15.139219] kernel: kvm: disabled by bios
[   15.178290] kernel: kvm: disabled by bios
[   15.226335] kernel: kvm: disabled by bios
[   15.274478] kernel: kvm: disabled by bios
[   19.326637] kernel: audit: type=1400 audit(1587742330.059:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=544 comm="apparmor_parser"
[   19.344359] kernel: audit: type=1400 audit(1587742330.075:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=545 comm="apparmor_parser"
[   19.344363] kernel: audit: type=1400 audit(1587742330.075:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=545 comm="apparmor_parser"
[   19.344366] kernel: audit: type=1400 audit(1587742330.075:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=545 comm="apparmor_parser"
[   19.357425] kernel: audit: type=1400 audit(1587742330.091:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=551 comm="apparmor_parser"
[   19.371877] kernel: audit: type=1400 audit(1587742330.103:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=548 comm="apparmor_parser"
[   19.371881] kernel: audit: type=1400 audit(1587742330.103:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=548 comm="apparmor_parser"
[   19.371884] kernel: audit: type=1400 audit(1587742330.103:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd//third_party" pid=548 comm="apparmor_parser"
[   19.372214] kernel: audit: type=1400 audit(1587742330.103:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=550 comm="apparmor_parser"
[   19.372218] kernel: audit: type=1400 audit(1587742330.103:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=550 comm="apparmor_parser"
[   26.982178] kernel: intel_pstate: Turbo disabled by BIOS or unavailable on processor

```

---

### Post by tech291083 on 2020-04-25
[COLOR=#000000]Below are the contents of the var/log/dpkg file. I am not sure whether this is of any help or not, but I am still posting it here. Since[/COLOR][COLOR=#000000] the actual output is too long, so I am only posting the last few lines here. Thanks.

```

[/COLOR]2020-04-24 21:07:59 status half-installed systemd-cron:amd64 1.5.14-2
2020-04-24 21:07:59 status unpacked systemd-cron:amd64 1.5.14-2
2020-04-24 21:08:00 install systemd-journal-remote:amd64 <none> 242-7ubuntu3.7
2020-04-24 21:08:00 status half-installed systemd-journal-remote:amd64 242-7ubuntu3.7
2020-04-24 21:08:00 status unpacked systemd-journal-remote:amd64 242-7ubuntu3.7
2020-04-24 21:08:00 install systemd-tests:amd64 <none> 242-7ubuntu3.7
2020-04-24 21:08:00 status half-installed systemd-tests:amd64 242-7ubuntu3.7
2020-04-24 21:08:02 status unpacked systemd-tests:amd64 242-7ubuntu3.7
2020-04-24 21:08:02 install libnss-mymachines:amd64 <none> 242-7ubuntu3.7
2020-04-24 21:08:02 status half-installed libnss-mymachines:amd64 242-7ubuntu3.7
2020-04-24 21:08:02 status unpacked libnss-mymachines:amd64 242-7ubuntu3.7
2020-04-24 21:08:03 startup packages configure
2020-04-24 21:08:03 configure libdw1:amd64 0.176-1.1 <none>
2020-04-24 21:08:03 status unpacked libdw1:amd64 0.176-1.1
2020-04-24 21:08:03 status half-configured libdw1:amd64 0.176-1.1
2020-04-24 21:08:03 status installed libdw1:amd64 0.176-1.1
2020-04-24 21:08:03 configure systemd-coredump:amd64 242-7ubuntu3.7 <none>
2020-04-24 21:08:03 status unpacked systemd-coredump:amd64 242-7ubuntu3.7
2020-04-24 21:08:03 status half-configured systemd-coredump:amd64 242-7ubuntu3.7
2020-04-24 21:08:04 status installed systemd-coredump:amd64 242-7ubuntu3.7
2020-04-24 21:08:05 configure btrfs-progs:amd64 5.2.1-1ubuntu1 <none>
2020-04-24 21:08:05 status unpacked btrfs-progs:amd64 5.2.1-1ubuntu1
2020-04-24 21:08:05 status half-configured btrfs-progs:amd64 5.2.1-1ubuntu1
2020-04-24 21:08:05 status installed btrfs-progs:amd64 5.2.1-1ubuntu1
2020-04-24 21:08:05 configure systemd-cron:amd64 1.5.14-2 <none>
2020-04-24 21:08:05 status unpacked systemd-cron:amd64 1.5.14-2
2020-04-24 21:08:05 status half-configured systemd-cron:amd64 1.5.14-2
2020-04-24 21:08:08 status installed systemd-cron:amd64 1.5.14-2
2020-04-24 21:08:08 configure libmicrohttpd12:amd64 0.9.66-1 <none>
2020-04-24 21:08:08 status unpacked libmicrohttpd12:amd64 0.9.66-1
2020-04-24 21:08:08 status half-configured libmicrohttpd12:amd64 0.9.66-1
2020-04-24 21:08:08 status installed libmicrohttpd12:amd64 0.9.66-1
2020-04-24 21:08:09 configure systemd-bootchart:amd64 233-2 <none>
2020-04-24 21:08:09 status unpacked systemd-bootchart:amd64 233-2
2020-04-24 21:08:09 status half-configured systemd-bootchart:amd64 233-2
2020-04-24 21:08:10 status installed systemd-bootchart:amd64 233-2
2020-04-24 21:08:11 configure systemd-tests:amd64 242-7ubuntu3.7 <none>
2020-04-24 21:08:11 status unpacked systemd-tests:amd64 242-7ubuntu3.7
2020-04-24 21:08:11 status half-configured systemd-tests:amd64 242-7ubuntu3.7
2020-04-24 21:08:11 status installed systemd-tests:amd64 242-7ubuntu3.7
2020-04-24 21:08:11 configure systemd-container:amd64 242-7ubuntu3.7 <none>
2020-04-24 21:08:11 status unpacked systemd-container:amd64 242-7ubuntu3.7
2020-04-24 21:08:11 status half-configured systemd-container:amd64 242-7ubuntu3.7
2020-04-24 21:08:13 status installed systemd-container:amd64 242-7ubuntu3.7
2020-04-24 21:08:13 configure systemd-journal-remote:amd64 242-7ubuntu3.7 <none>
2020-04-24 21:08:13 status unpacked systemd-journal-remote:amd64 242-7ubuntu3.7
2020-04-24 21:08:13 status half-configured systemd-journal-remote:amd64 242-7ubuntu3.7
2020-04-24 21:08:14 status installed systemd-journal-remote:amd64 242-7ubuntu3.7
2020-04-24 21:08:14 configure libnss-mymachines:amd64 242-7ubuntu3.7 <none>
2020-04-24 21:08:14 status unpacked libnss-mymachines:amd64 242-7ubuntu3.7
2020-04-24 21:08:14 status half-configured libnss-mymachines:amd64 242-7ubuntu3.7
2020-04-24 21:08:15 status installed libnss-mymachines:amd64 242-7ubuntu3.7
2020-04-24 21:08:15 trigproc libc-bin:amd64 2.30-0ubuntu2.1 <none>
2020-04-24 21:08:15 status half-configured libc-bin:amd64 2.30-0ubuntu2.1
2020-04-24 21:08:15 status installed libc-bin:amd64 2.30-0ubuntu2.1
2020-04-24 21:08:15 trigproc man-db:amd64 2.8.7-3 <none>
2020-04-24 21:08:15 status half-configured man-db:amd64 2.8.7-3
2020-04-24 21:08:21 status installed man-db:amd64 2.8.7-3
2020-04-24 21:08:21 trigproc dbus:amd64 1.12.14-1ubuntu2 <none>
2020-04-24 21:08:21 status half-configured dbus:amd64 1.12.14-1ubuntu2
2020-04-24 21:08:21 status installed dbus:amd64 1.12.14-1ubuntu2[COLOR=#000000]
[/COLOR]
```

---

### Post by HermanAB on 2020-04-25
Howdy,

Some general tips:
1. Linux is very stable, to the point that most problems are due to upgrades and updates.
2. If you install the LTS version, then you don't need to upgrade so often.
3. Look at it this way: If it works now, then after an upgrade it will be the same or worse - it won't be better - less security issues maybe - but not really any better.
4. After installing and making sure it works, enable the Secure Shell OpenSSH Server.  That way, if your video settings go south, you can log in over the network from another computer to fix it.
5. If you make /home a separate disk partition, then you can upgrade in place without formatting /home where all your data is, which can save a lot of time if you don't have to retrieve your data from backup.
6. As soon as things are working, spend some time on making a backup system that works, but only backup your data, not the whole system, since you can always install the latest system - you don't need to keep an old and outdated copy of Linux.

---

### Post by tech291083 on 2020-04-25
> **CelticWarrior said:**
> Installing other DEs from the respective meta-packages available in the official repositories as you did, apparently, is thought to be safe. That said, I suspect there was a problem with the display manager somewhere during that process.

You may try in the TTY - really, it can't hurt - to reconfigure the default one in vanilla Ubuntu 20.04:
```
sudo dpkg-reconfigure gdm3
```
Use directional keys to select again 'gdm3', then TAB to highlight OK and finally ENTER. Use this as a reference: [https://www.linuxuprising.com/2018/12/how-to-change-default-display-manager.html](https://www.linuxuprising.com/2018/12/how-to-change-default-display-manager.html)

Sure, I will give it a ago, thanks.

---

### Post by tech291083 on 2020-04-25
> **CelticWarrior said:**
> 
If nothing shows up try CTRL+ALT+F3 which hopefully will give a functional TTY (command line) where further troubleshooting can be tried.



Here is a bunch of photos showing what the current situation is, boot menu is there but Ubuntu won't boot but I am able to CTRL+ALT+F3 and get functional TTY (command line), thanks.

[https://imgur.com/a/vasOYBf](https://imgur.com/a/vasOYBf)

---

### Post by CelticWarrior on 2020-04-25
> **tech291083 said:**
> Here is a bunch of photos showing what the current situation is, boot menu is there but Ubuntu won't boot but I am able to CTRL+ALT+F3 and get functional TTY (command line), thanks.

[https://imgur.com/a/vasOYBf](https://imgur.com/a/vasOYBf)

All I can see in these photos is you doing a lot of things you probably shouldn't and nothing of what was suggested.

---

### Post by tech291083 on 2020-04-26
> **HermanAB said:**
> 


1. Linux is very stable, to the point that most problems are due to upgrades and updates.



Hi!


Yes, I agree as I have used Ubuntu as a hobby for over a decade, although intermittently.




> 
2. If you install the LTS version, then you don't need to upgrade so often.



You make a lot of sense, I am just waiting for a solution to my current problem with 19.10 and I promise you that I will download and install the latest LTS edition ASAP.


> 
3. Look at it this way: If it works now, then after an upgrade it will be the same or worse - it won't be better - less security issues maybe - but not really any better.



Correct.


> 
4. After installing and making sure it works, enable the Secure Shell OpenSSH Server. That way, if your video settings go south, you can log in over the network from another computer to fix it.



I do appreciated your suggestion, but I have never used Secure Shell OpenSSH Server.


> 
5. If you make /home a separate disk partition, then you can upgrade in place without formatting /home where all your data is, which can save a lot of time if you don't have to retrieve your data from backup.



For that matter, I will have to manually create various partitions, which I have never done in my life. But worth a try nevertheless.


> 


6. As soon as things are working, spend some time on making a backup system that works, but only backup your data, not the whole system, since you can always install the latest system - you don't need to keep an old and outdated copy of Linux.

 
OK, sure.


Many thanks for the above suggestions.

---

### Post by tech291083 on 2020-04-26
> **CelticWarrior said:**
> All I can see in these photos is you doing a lot of things you probably shouldn't and nothing of what was suggested.

Hi,

Yes, you are right I did a few things which were not suggested, but please believe me I was only trying to find a workaround, sorry if you have been inconvenienced. Thanks a lot.

---

### Post by tech291083 on 2020-04-26
> **CelticWarrior said:**
> 
You may try in the TTY - really, it can't hurt - to reconfigure the default one in vanilla Ubuntu 20.04:
```
sudo dpkg-reconfigure gdm3
```



Hi!


I was able to get to a TTY and I did try what you had suggested, but I got an error "gdm3 is broken or not fully installed". Please do guide me further if possible. You have given me a lot of hope of a possible workaround so far and I truly appreciate your guidance. Thanks.

[https://imgur.com/a/gTGTLCu](https://imgur.com/a/gTGTLCu)

---

### Post by CelticWarrior on 2020-04-26
> **tech291083 said:**
> Hi!


 "gdm3 is broken or not fully installed"

[https://imgur.com/a/gTGTLCu](https://imgur.com/a/gTGTLCu)

The system is not in a good place... This may correct it:
```
sudo apt install --reinstall gdm3
```

If successful - the reinstallation - maybe it's all it needs but you can then try reconfiguring it again with the previous command.

---

### Post by tech291083 on 2020-06-08
Friends,


Sorry to reply so late, but I have downloaded and installed the latest Ubuntu Desktop 20.04 LTS 64 bit and I am proud to say that I have somehow managed to install the following 4 different desktop environments and I am able to boot into any of these 4 desktop environments without any issues whatsoever. I have posted some screenshots just let you know my system looks now. Many thanks for your help.

Login screen..

[https://imgur.com/a/WXE7yKf](https://imgur.com/a/WXE7yKf)

Cinnamon desktop environment


[https://imgur.com/a/f7SawWz](https://imgur.com/a/f7SawWz)



GNOME Classic desktop environment


[https://imgur.com/a/4jw54gw](https://imgur.com/a/4jw54gw)


MATE desktop environment


[https://imgur.com/a/nxOikNa](https://imgur.com/a/nxOikNa)



Ubuntu on Wayland desktop environment


[https://imgur.com/a/37SkgQJ](https://imgur.com/a/37SkgQJ)

---

