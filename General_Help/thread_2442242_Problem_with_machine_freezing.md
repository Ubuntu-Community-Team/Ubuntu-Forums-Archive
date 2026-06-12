---
title: "Problem with machine freezing"
date: 2020-05-01
forum: General Help
---

### Post by georgesgiralt on 2020-05-01
Hello,
I've a very annoying problem and I don't know if it is software or hardware related.
When I do a high (but not huge) disk activity, the mouse (or track pad) freeze and if I'm tapping on the keyboard, either letters do not show or are multiply output liiike tisss (for like this).
The behavior is easily reproduced : take a huge file (Ubuntu iso image for instance, copy it into another file, say test then cat the iso file >> test and try to move the cursor while working. Movement will become erratic and stop for some time until the cat is done.

The machine is a Dell G3 (3579) with 8Gb memory. The disks are either (I tested 3) a Seagate FireCuda 2TB, A Seagate Barracuda 2TB, and a Seagate LaptopThin 320 GB, 7200 RPM. All three experience the problem.
Distribution is Ubuntu 19.10 with all updates applied. Current as of today. The system is installed with LVM using 2 PV, one is the hard disk, the other one an NVME 256GB (holding /, /usr, /var logical volumes the HDD holding /boot, /tmp, /var/log, /var/tmp, /home and swap lvs) 
The machine has an Nvidia GP107M [GeForce GTX 1050 Mobile] card
The processor is a Intel(R) Core(TM) i5-8300H CPU @ 2.30GHz 
And I tried the Ubuntu session on Xorg, on Wayland and Flashback sessions also without luck.

I have also checked that on an old Lenovo Laptop (I7 4210 ), 16GB memory, Nvidia GT740 mobile card, M.2 256Gb sata and HDD, with same Ubuntu version, with same LVM layout (NVME located LV being replaced by M.2 SSD) the problem only arose when I do 3 or 5 of the above redirected cat simultaneously...  And I tried all 3 HDD mentioned above. Software is exactly same as I pvmove the NVME lvs to the hdd, install the hdd into the Lenovo, pvmove the said lv to the M.2 card and then do the test.

Google is not my friend. I did not find anything relevant nor bug nor explanation.
So any help I can get will be HIGHLY appreciated because I suffer this situation since quite a long time and I've devoted a lot of time trying to solve it.
Thank you for reading me !

---

### Post by CelticWarrior on 2020-05-01
You aren't using Nvidia drivers and those are considerably more important the newer the graphics card is.
This is likely the reason for the differences experienced between those computers.

---

### Post by georgesgiralt on 2020-05-01
Thank you for your quick response !
Actually I am. I use nvidia-driver-390 which was the one the Ubuntu installer proposed to me at install time (and which is just updated now ...).
I've thought about that and tried to switch to the 440 version using the "aditional driver" app but to no avail. The app always shows the 390 version as used. 
Stay safe !

---

### Post by dino99 on 2020-05-01
After a freeze, glance at journalctl output to know what is going on; then you can act.

---

### Post by georgesgiralt on 2020-05-01
Hello,
I've just tested the nvidia-driver-440 and a restart. Nothing changes.
Dino99, I always run glances when doing my tests.
Here are the messages Glances posted during the cat operation
```
2020-05-01 16:54:40 (0:00:42) - CRITICAL on CPU_IOWAIT (Min:16.8 Mean:43.4 Max:71.4): software-proper, update-notifier, firefox
Package id 0                     60C   2020-05-01 16:54:19 (0:00:12) - CRITICAL on CPU_IOWAIT (Min:13.4 Mean:21.1 Max:28.0): megasync, cat, gnome-shell
Core 0                           44C   2020-05-01 16:53:55 (0:00:15) - CRITICAL on CPU_IOWAIT (Min:13.3 Mean:20.0 Max:26.7): cat, gnome-shell, glances
Core 1                           43C   2020-05-01 16:52:58 (0:00:27) - CRITICAL on CPU_IOWAIT (Min:16.3 Mean:23.7 Max:33.0): deja-dup-monitor, gsd-housekeeping, megasync
2020-05-01 16:57:08 CEST         60C   2020-05-01 16:52:18 (0:00:34) - CRITICAL on CPU_IOWAIT (Min:15.4 Mean:37.7 Max:55.5): gnome-software, glances, packagekitd

```
The problem shows when Iowait is above 35~40 %.
Here is the journalctl output (full but cut around the timestamp Glances reports). I send all output because I do not know what to search for and I'm not too keen at journalctl forensics....
```

mai 01 16:52:19 hostname dbus-daemon[1090]: [system] Activating via systemd: service name='org.freedesktop.bolt' unit='bolt.service' requested by ':1.617' (uid=0 pid=2825 comm="/usr/lib/fwupd/fwupd " label
mai 01 16:52:19 hostname systemd[1]: Starting Thunderbolt system service...
mai 01 16:52:19 hostname boltd[2839]: bolt 0.8 starting up.
mai 01 16:52:19 hostname boltd[2839]: store: located at: /var/lib/boltd
mai 01 16:52:19 hostname boltd[2839]: config: loading user config
mai 01 16:52:19 hostname boltd[2839]: bouncer: initializing polkit
mai 01 16:52:19 hostname boltd[2839]: udev: initializing udev
mai 01 16:52:19 hostname boltd[2839]: store: loading domains
mai 01 16:52:19 hostname boltd[2839]: store: loading devices
mai 01 16:52:19 hostname boltd[2839]: power: state located at: /run/boltd/power
mai 01 16:52:19 hostname boltd[2839]: power: force power support: yes
mai 01 16:52:19 hostname boltd[2839]: power: setting force_power to ON
mai 01 16:52:19 hostname boltd[2839]: power: could not force power: write error: Aucun périphérique de ce type
mai 01 16:52:19 hostname boltd[2839]: udev: enumerating devices
mai 01 16:52:19 hostname dbus-daemon[1090]: [system] Successfully activated service 'org.freedesktop.bolt'
mai 01 16:52:19 hostname systemd[1]: Started Thunderbolt system service.
mai 01 16:52:19 hostname kernel: ACPI BIOS Error (bug): AE_AML_PACKAGE_LIMIT, Index (0x0000000FF) is beyond end of object (length 0x11) (20190703/exoparg2-393)
mai 01 16:52:19 hostname kernel: No Local Variables are initialized for Method [GINF]
mai 01 16:52:19 hostname kernel: Initialized Arguments for Method [GINF]:  (2 arguments defined for method invocation)
mai 01 16:52:19 hostname kernel:   Arg0:   00000000e4ef5a4a <Obj>           Integer 00000000000000FF
mai 01 16:52:19 hostname kernel:   Arg1:   000000003e72179d <Obj>           Integer 0000000000000000
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.GINF due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.GADR due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.SGOV due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.CGWR due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.TBFP due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.WMTF.WMTF due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:19 hostname boltd[2839]: power: setting force_power to ON
mai 01 16:52:19 hostname kernel: ACPI BIOS Error (bug): AE_AML_PACKAGE_LIMIT, Index (0x0000000FF) is beyond end of object (length 0x11) (20190703/exoparg2-393)
mai 01 16:52:19 hostname kernel: No Local Variables are initialized for Method [GINF]
mai 01 16:52:19 hostname kernel: Initialized Arguments for Method [GINF]:  (2 arguments defined for method invocation)
mai 01 16:52:19 hostname kernel:   Arg0:   000000003e72179d <Obj>           Integer 00000000000000FF
mai 01 16:52:19 hostname kernel:   Arg1:   0000000089897a23 <Obj>           Integer 0000000000000000
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.GINF due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.GADR due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.SGOV due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.CGWR due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.TBFP due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:19 hostname kernel: ACPI Error: Aborting method \_SB.WMTF.WMTF due to previous error (AE_AML_PACKAGE_LIMIT) (20190703/psparse-529)
mai 01 16:52:20 hostname gnome-shell[2109]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.105/org/ayatana/NotificationItem/software_update_available
mai 01 16:52:20 hostname gnome-shell[2109]: [AppIndicatorSupport-FATAL] unable to update overlay icon
mai 01 16:52:20 hostname gnome-shell[2109]: [AppIndicatorSupport-FATAL] unable to update overlay icon
mai 01 16:52:25 hostname gnome-shell[2109]: [AppIndicatorSupport-DEBUG] Registering StatusNotifierItem :1.114/StatusNotifierItem
mai 01 16:52:25 hostname gnome-shell[2109]: [AppIndicatorSupport-FATAL] unable to update overlay icon
mai 01 16:52:25 hostname gnome-shell[2109]: [AppIndicatorSupport-FATAL] unable to update overlay icon
mai 01 16:52:25 hostname gnome-shell[2109]: [AppIndicatorSupport-FATAL] unable to update overlay icon
mai 01 16:52:32 hostname dbus-daemon[1090]: [system] Successfully activated service 'org.freedesktop.fwupd'
mai 01 16:52:32 hostname systemd[1]: Started Firmware update daemon.
mai 01 16:52:32 hostname gnome-software[2786]: not handling error failed for action get-updates-historical: failed to build result for 03281da317dccd2b18de2bd1cc70a782df40ed7e
mai 01 16:52:32 hostname PackageKit[1476]: uid 1000 is trying to obtain org.freedesktop.packagekit.system-sources-refresh auth (only_trusted:0)
mai 01 16:52:32 hostname PackageKit[1476]: uid 1000 obtained auth for org.freedesktop.packagekit.system-sources-refresh
mai 01 16:52:33 hostname systemd-resolved[1046]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
mai 01 16:52:33 hostname systemd-resolved[1046]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
mai 01 16:52:33 hostname systemd-resolved[1046]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
mai 01 16:52:33 hostname systemd-resolved[1046]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
mai 01 16:52:33 hostname systemd-resolved[1046]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
mai 01 16:52:33 hostname systemd-resolved[1046]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
mai 01 16:52:34 hostname PackageKit[1476]: refresh-cache transaction /2556_dddaaecc from uid 1000 finished with success after 1824ms
mai 01 16:52:35 hostname gnome-software[2786]: hiding category audio-video featured applications: found only 0 to show, need at least 9
mai 01 16:52:35 hostname gnome-software[2786]: g_variant_get_double: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_DOUBLE)' failed
mai 01 16:52:37 hostname PackageKit[1476]: resolve transaction /2557_bdacabbe from uid 1000 finished with success after 1333ms
mai 01 16:52:37 hostname gnome-software[2786]: Only 1 apps for recent list, hiding
mai 01 16:52:37 hostname PackageKit[1476]: resolve transaction /2558_abbbaacc from uid 1000 finished with success after 555ms
mai 01 16:52:37 hostname PackageKit[1476]: resolve transaction /2559_ebcabeed from uid 1000 finished with success after 390ms
mai 01 16:52:37 hostname gnome-software[2786]: hiding category graphics featured applications: found only 1 to show, need at least 9
mai 01 16:52:38 hostname PackageKit[1476]: resolve transaction /2560_eeccbedc from uid 1000 finished with success after 398ms
mai 01 16:52:38 hostname gnome-software[2786]: Only 8 apps for popular list, hiding
mai 01 16:52:38 hostname PackageKit[1476]: resolve transaction /2561_aeacabaa from uid 1000 finished with success after 304ms
mai 01 16:52:39 hostname PackageKit[1476]: search-file transaction /2562_dbbbbbcb from uid 1000 finished with success after 807ms
mai 01 16:52:39 hostname PackageKit[1476]: search-file transaction /2563_aacbcabb from uid 1000 finished with success after 358ms
mai 01 16:52:40 hostname PackageKit[1476]: search-file transaction /2564_beacbbbb from uid 1000 finished with success after 353ms
mai 01 16:52:40 hostname PackageKit[1476]: search-file transaction /2565_caddcbda from uid 1000 finished with success after 349ms
mai 01 16:52:40 hostname gnome-software[2786]: Failed to find one package for arduino-arduinoide.desktop, /usr/share/applications/arduino-arduinoide.desktop, [0]
mai 01 16:52:40 hostname PackageKit[1476]: search-file transaction /2566_ddccbebb from uid 1000 finished with success after 336ms
mai 01 16:52:41 hostname PackageKit[1476]: search-file transaction /2567_accaaadc from uid 1000 finished with success after 335ms
mai 01 16:52:41 hostname PackageKit[1476]: search-file transaction /2568_dbcbdaec from uid 1000 finished with success after 361ms
mai 01 16:52:42 hostname PackageKit[1476]: search-file transaction /2569_ceacbbec from uid 1000 finished with success after 375ms
mai 01 16:52:42 hostname PackageKit[1476]: search-file transaction /2570_dcdbadec from uid 1000 finished with success after 363ms
mai 01 16:52:42 hostname PackageKit[1476]: search-file transaction /2571_cbededbb from uid 1000 finished with success after 335ms
mai 01 16:52:43 hostname PackageKit[1476]: search-file transaction /2572_aaacabcc from uid 1000 finished with success after 371ms
mai 01 16:52:43 hostname PackageKit[1476]: search-file transaction /2573_aaaedddd from uid 1000 finished with success after 335ms
mai 01 16:52:43 hostname PackageKit[1476]: search-file transaction /2574_bdaacacb from uid 1000 finished with success after 345ms
mai 01 16:52:44 hostname PackageKit[1476]: search-file transaction /2575_aeccceec from uid 1000 finished with success after 340ms
mai 01 16:52:44 hostname PackageKit[1476]: search-file transaction /2576_dbdcadad from uid 1000 finished with success after 334ms
mai 01 16:52:44 hostname PackageKit[1476]: search-file transaction /2577_baadcbde from uid 1000 finished with success after 331ms
mai 01 16:52:45 hostname PackageKit[1476]: search-file transaction /2578_abdacbaa from uid 1000 finished with success after 343ms
mai 01 16:52:45 hostname PackageKit[1476]: search-file transaction /2579_aabecbdc from uid 1000 finished with success after 430ms
mai 01 16:52:46 hostname PackageKit[1476]: search-file transaction /2580_dccedaac from uid 1000 finished with success after 345ms
mai 01 16:52:46 hostname PackageKit[1476]: get-details transaction /2581_bdcdddcc from uid 1000 finished with success after 264ms
mai 01 16:52:46 hostname gnome-software[2786]: ignoring non-installed app GsApp: [0x7ff9bc0d5060]
                                               kind:                desktop
                                               state:               available
                                               quirk:               provenance
                                               id:                  virtualbox.desktop
                                               unique-id:           system/package/ubuntu-eoan-multiverse/desktop/virtualbox.desktop/*
                                               scope:               system
                                               bundle-kind:         package
                                               kudos:               has-keywords
                                               kudo-percentage:     5
                                               name:                VirtualBox
                                               pixbuf:              0x7ff9d416aea0
                                               icon-kind:           cached
                                               icon-pixbuf:         0x7ff9d416aea0
                                               icon-name:           virtualbox-qt_virtualbox.png
                                               icon-prefix:         /var/lib/app-info/icons/ubuntu-eoan-multiverse
                                               version:             6.0.14-dfsg-1
                                               summary:             Run several virtual systems on a single host computer
                                               description:         VirtualBox est une solution libre de virtualisation x86 qui permet d'utiliser de nombreux systèmes d'exploitation, comme Windows, DOS, BS
                                               
                                               Ce paquet fournit l'interface utilisateur basée sur Qt pour VirtualBox.
                                               source-00:           virtualbox-qt
                                               source-id-00:        virtualbox-qt;6.0.14-dfsg-1;amd64;ubuntu-eoan-multiverse
                                               url{homepage}:       https://www.virtualbox.org
                                               license:             unknown
                                               license-is-free:     no
                                               management-plugin:   packagekit
                                               origin:              ubuntu-eoan-multiverse
                                               origin-appstream:    ubuntu-eoan-multiverse
                                               rating:              62
                                               review-rating:       [0:0]
                                               review-rating:       [1:69]
                                               review-rating:       [2:11]
                                               review-rating:       [3:13]
                                               review-rating:       [4:14]
                                               review-rating:       [5:74]
                                               reviews:             0
                                               provides:            0
                                               install-date:        1
                                               size-installed:      unknowable
                                               size-download:       3,5*MB
                                               category:            Emulator
                                               category:            System
                                               category:            Utility
                                               keyword:             virtualization
                                               {appstream::source-file}: /usr/share/applications/virtualbox.desktop
                                               {GnomeSoftware::Creator}: appstream
mai 01 16:52:46 hostname gnome-software[2786]: ignoring non-installed app GsApp: [0x7ff9bc0eac30]
                                               kind:                desktop
                                               state:               available
                                               quirk:               provenance
                                               id:                  nemo.desktop
                                               unique-id:           system/package/ubuntu-eoan-universe/desktop/nemo.desktop/*
                                               scope:               system
                                               bundle-kind:         package
                                               kudos:               has-keywords|hi-dpi-icon
                                               kudo-percentage:     25
                                               name:                Fichiers
                                               pixbuf:              0x7ff9d4260580
                                               icon-kind:           stock
                                               icon-name:           org.gnome.Nautilus
                                               icon-prefix:         /var/lib/app-info/icons/ubuntu-eoan-universe
                                               icon-kind:           cached
                                               icon-name:           budgie-desktop-common_org.gnome.Nautilus.png
                                               icon-prefix:         /var/lib/app-info/icons/ubuntu-eoan-universe
                                               icon-kind:           remote
                                               version:             0.12.4
                                               summary:             Accéder aux fichiers et les organiser
                                               description:         While this common budgie-desktop package can be installed manually, it is recommended that the binary packages budgie-desktop-minimal or 
                                               
                                               This package provides common:   ubuntu and budgie-desktop gsettings overrides   make QT apps look like GTK+ apps   default icon-theme for GTK+ applications   
                                               source-00:           budgie-desktop-common
                                               source-01:           nemo
                                               source-id-00:        budgie-desktop-common;0.12.4;all;ubuntu-eoan-universe
                                               source-id-01:        nemo;4.0.6-1;amd64;installed:ubuntu-eoan-universe
                                               url{homepage}:       https://github.com/UbuntuBudgie
                                               license:             LicenseRef-free=https://www.ubuntu.com/about/about-ubuntu/licensing
                                               license-is-free:     yes
                                               management-plugin:   packagekit
                                               origin:              ubuntu-eoan-universe
                                               origin-appstream:    ubuntu-eoan-universe
                                               rating:              86
                                               review-rating:       [0:0]
                                               review-rating:       [1:2]
                                               review-rating:       [2:2]
                                               review-rating:       [3:1]
                                               review-rating:       [4:2]
                                               review-rating:       [5:24]
                                               reviews:             0
                                               provides:            0
                                               install-date:        1
                                               size-installed:      unknowable
                                               size-download:       4,8*MB
                                               category:            Utility
                                               category:            Core
                                               keyword:             folders
                                               keyword:             filesystem
                                               keyword:             explorer
                                               {appstream::source-file}: /usr/share/applications/nemo.desktop
                                               {GnomeSoftware::Creator}: appstream
mai 01 16:53:17 hostname systemd[2028]: Reached target GNOME Session is stable (running for >2 minutes).
mai 01 16:54:37 hostname zeitgeist-datah[2655]: zeitgeist-datahub.vala:210: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, man
mai 01 16:54:37 hostname systemd[2028]: Started Application launched by gnome-shell.
mai 01 16:54:40 hostname rtkit-daemon[1383]: Supervising 3 threads of 1 processes of 1 users.
mai 01 16:54:40 hostname rtkit-daemon[1383]: Supervising 3 threads of 1 processes of 1 users.
mai 01 16:54:40 hostname rtkit-daemon[1383]: Supervising 3 threads of 1 processes of 1 users.

```
Thak you VERY MUCH for your help !

---

### Post by georgesgiralt on 2020-05-02
update :
As you said it could be induced by a graphic card driver, I decided to try something. I disabled the Nvidia card (as there is no way to do this into BIOS on the Dell, as opposed to the Lenovo BIOS), I used prime-select to switch to Intel graphic card and restarted the machine.Problem is worse I think. 
So is this clearing the graphic driver ? 
Have a nice day !

---

### Post by dino99 on 2020-05-02
What catched up my attention:   > ACPI BIOS Error (bug): AE_AML_PACKAGE_LIMIT, Index (0x0000000FF) is beyond end of object

This is serious enough to drop all the possible other trouble reasons. Have to dig and solve that first.
It is time to glance at other hardware/chipset warning/error prior to the above acpi error. Be sure that everything is well identified.
If you do not use the latest Dell's bios for you hardware, then upgrade first, and glance again at journalctl after a reboot. Maybe the Dell forum is the good place to talk/share/find a solution.

At least booting with 'noacpi' can be a temporary solution to avoid such freeze. As you says freezing happen with high hdd load (only ?), then you can also test that hdd(s) health (specialy be sure to get >10% space free on it).

---

### Post by georgesgiralt on 2020-05-02
Oh boy,
This machine came from Dell with Ubuntu 16.04LTS installed. IT had a lot of ACPI messages in the logs.
When I re-installed it with 19.10, I did hope to solve most if not all of them. 
I, of course, used the same boot kernel parameters Dell used. And still there are problems left. I once tried without any ACPI options in the Kernel boot line... You should have seen it ! Horrific.
I tried to search the Dell community for thoughts and solutions... Better get Windows. 
This machine is the first Dell computer I've bought, and, given the present situation and Dell support, will be the last one. 
I4ll give a try at the "no acpi" option. But I fear this may solve one thing and break loose everything else....  
I have the latest Dell BIOS installed. Everytime there is one new, I hope it will solve some of my ACPI issues. So far, not so good...

I also have the original Dell software somewhere. I'll try this on to see if they have a different kernel than the stock one... 

For the record, here is what I use nowadays :
```

GRUB_CMDLINE_LINUX_DEFAULT="acpi=strict"
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux-Dell-Video alx.enable_wol=1 mem_sleep_default=deep"

```

And here are the Nvidia packets that I got after installing the 440 version ! 
```

georges:~$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-440:amd64                      440.59-0ubuntu0.19.10.2                    amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-440                          440.59-0ubuntu0.19.10.2                    all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:amd64                   390.132-0ubuntu0.19.10.1                   amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                    390.132-0ubuntu0.19.10.1                   i386         NVIDIA libcompute package
rc  libnvidia-compute-435:amd64                   435.21-0ubuntu2                            amd64        NVIDIA libcompute package
ii  libnvidia-compute-440:amd64                   440.59-0ubuntu0.19.10.2                    amd64        NVIDIA libcompute package
ii  libnvidia-compute-440:i386                    440.59-0ubuntu0.19.10.2                    i386         NVIDIA libcompute package
ii  libnvidia-decode-440:amd64                    440.59-0ubuntu0.19.10.2                    amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-440:i386                     440.59-0ubuntu0.19.10.2                    i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-440:amd64                    440.59-0ubuntu0.19.10.2                    amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-440:i386                     440.59-0ubuntu0.19.10.2                    i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-440:amd64                      440.59-0ubuntu0.19.10.2                    amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-440:i386                       440.59-0ubuntu0.19.10.2                    i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-440:amd64                        440.59-0ubuntu0.19.10.2                    amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-440:i386                         440.59-0ubuntu0.19.10.2                    i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-440:amd64                      440.59-0ubuntu0.19.10.2                    amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-440:i386                       440.59-0ubuntu0.19.10.2                    i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  nvidia-compute-utils-390                      390.132-0ubuntu0.19.10.1                   amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-435                      435.21-0ubuntu2                            amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-440                      440.59-0ubuntu0.19.10.2                    amd64        NVIDIA compute utilities
rc  nvidia-dkms-390                               390.132-0ubuntu0.19.10.1                   amd64        NVIDIA DKMS package
rc  nvidia-dkms-435                               435.21-0ubuntu2                            amd64        NVIDIA DKMS package
ii  nvidia-dkms-440                               440.59-0ubuntu0.19.10.2                    amd64        NVIDIA DKMS package
ii  nvidia-driver-440                             440.59-0ubuntu0.19.10.2                    amd64        NVIDIA driver metapackage
rc  nvidia-kernel-common-390                      390.132-0ubuntu0.19.10.1                   amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-435                      435.21-0ubuntu2                            amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-440                      440.59-0ubuntu0.19.10.2                    amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-440                      440.59-0ubuntu0.19.10.2                    amd64        NVIDIA kernel source package
ii  nvidia-prime                                  0.8.13                                     all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                               440.44-0ubuntu0.19.10.1                    amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-440                              440.59-0ubuntu0.19.10.2                    amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                       0.18                                       all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-440                 440.59-0ubuntu0.19.10.2                    amd64        NVIDIA binary Xorg driver
georges:~$ 

```

---

### Post by georgesgiralt on 2020-05-02
New investigations :
I've moved all LV from NVME card to the hard drive. Then I've installed the Dell original nvme card in it's slot and booted the machine into the original Ubuntu.
Errors pertaining to ACPI functions. But I checked and found that the kernel I had booted into was not the OEM original. So I rebooted the machine with the 4.13 OEM dell delivered. 
Much much less ACPI errors and warning. I tried my experiment to cat  a huge file and append it to an already big file and, guess what, no freeze ! (I did the copy on the hard disk to be sure to have the same access speed and as close as possible machine behavior).
So Mr Dell did something on its 4.13 kernel. I've checked that I've got the original restore partition available but if there is a custom kernel config file, no kernel sources. Nor in /usr/src ...
I'm very rusty as to the kernel build and analysis so I need your help here, please !
Here is the Kernel command line on the Dell's 16.04LTS :
```

Command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-1021-oem.efi.signed root=UUID=477456a6-fe49-47fe-b30c-ba780cef7428 ro acpi_osi=Linux-Dell-Video acpi_osi=Linux-Dell-Video alx.enable_wol=1 mem_sleep_default=deep acpi_osi=Linux-Dell-Video alx.enable_wol=1 mem_sleep_default=deep quiet splash vt.handoff=7

```
Please help me, I'm way over my head here !
HAve a nice day !

---

### Post by dino99 on 2020-05-02
Sorry for all these troubles, but i have never used a Dell, but seen many times related threads  :(
 [https://duckduckgo.com/?q=ubuntu+dell+kernel+driver+freeze&t=canonical&ia=web](https://duckduckgo.com/?q=ubuntu+dell+kernel+driver+freeze&t=canonical&ia=web)
[https://duckduckgo.com/?q=ubuntu+dell+g3+freeze&t=canonical&ia=web](https://duckduckgo.com/?q=ubuntu+dell+g3+freeze&t=canonical&ia=web)

[https://www.dell.com/support/home/fr/fr/frbsdt1/product-support/product/g-series-15-3579-laptop/drivers](https://www.dell.com/support/home/fr/fr/frbsdt1/product-support/product/g-series-15-3579-laptop/drivers)

Genuinely the kernel is patched/upgraded with the help of Dell technical staff, so recent versions should be better; except for too old hardware where some chip are no more supported (should not be case on your machine, but who knows).

Many ways to investigate: 
- boot settings: are you using the (all/good) required ones ?
- bios settings: are they well set to deal with chipsets/cards on mobo ?
- ram/swap/free hdd space: is there enough room for wide/huge load ?
- nvidia driver used: maybe test/find the one running the less trouble.

When you get a freeze, or better when you suspect getting one, open first the system Monitor Processes addon to see which one is saturating %cpu.
Maybe you will find where is the hardware bottleneck ; need to test many cases sadly ;)

---

### Post by georgesgiralt on 2020-05-02
Hello Dino99,
You wrote :
"Genuinely the kernel is patched/upgraded with the help of Dell technical staff, so recent versions should be better; except for too old hardware where some chip are no more supported (should not be case on your machine, but who knows)."

Well, the most recent kernel does not hold the change they made into the 4.13 one... 
I've seen that the 16.04 Dell version with a more recent kernel (vanilla one) does not have the problem. So could it be a module they use ? (there are a lot of loaded module with names containing "acpi"...) Add to this I still have the Dell recovery partition where there are a lot of things (3.0 GB...) so doing some forensic analysis could give me an answer... But I need some leads or clues as to what to search .

Last but not least, do you think that if I upgrade from 16.04 Dell version to, says 20.04, I could retain the Dell changes (obviously not those in the OEM kernel, but...) ? 

I have searched too much for troubleshooting this issue that I can't think straight, so your help will be invaluable !

P.S. : The Dell support page only offer the BIOS update when I select my serial number and a Linux OS.... So no help to get from them, I suppose....

---

### Post by dino99 on 2020-05-02
About the Seageate 320 Gb: could it be the slowest device installed ?  Maybe exclude it from lvm, and use it for storage or else.
The other hdds are very good ones. How they are used ?  There are many custom partitions install choices: is the system need to pick them across all these hdds ?

Try a new install of 20.04 on free space (manual install, ext4, default installer choices (no custom /var/ /tmp/ ...). Note that nowadays there is a swap file, not a partition, nor a /home partition: better to set a Data partition which is filed via syncing or cron. Do tests and see if you get freeze with that config.

---

### Post by georgesgiralt on 2020-05-02
Oh, I did not made myself clear !
I tried 3 different disks, as cited. But one at a time, as I can't put more than one in the laptop... 
So I've a 2TB Seagate disk in the machine. I hook another disk using USB adapter on the laptop, create the various needed partition on it, and copy the non Linux partitions, and pvmove the Linux parts. 
Once done, I do fstab edit on the external drive, adjust the initramfs and grub on the external disk and swap the external disk, putting it inside the machine. I then reboot and test for the freeze using my copy/cat commands. As there is the NVME disk in the VG, I "only" have to move the home, varlog, vartmp, ... LVs in the "new" disk. 
And I repeated this 3 times (including the test on the Lenovo laptop)... Time consuming and worthless.... given the results.
The 320 GB disk, running at 7200 RPM is very good at access time and responsiveness. Better than the 2TB one... A pity they do not make 2TB disks in 7200 RPM ...

Oh, and by the way, the Dell provided Ubuntu 16.04 LTS uses the Nvidia driver version 390. And it works flawlessly as far as I can tell in the Dell OS.... I can't tell if they have made some change to it or not. 
Now, I'll return the "plain" Seagate 2TB 5400 RPM to the Lenovo Laptop where it belongs, and restore on it the Windows partitions stored on a very old 200 GB disk, the linux partitions being stored on a 500 GB drive and a couple of USB sticks... I miss the data center storage I used at work ;-) it would have made my life easier ;-) 
Stay safe and have a nice bright day !

---

### Post by dino99 on 2020-05-02
Happy weekend 

As most say, devil is hidden into the details :P
Take time to find culprits via 'journalctl -b', pay attention at errors (red lines) then warnings.

But first have a break to avoid headhaches

---

### Post by georgesgiralt on 2020-05-02
I'll sleep on it. Maybe I will have a clue as to what to search for to reproduce/apply the Dell's mods to a recent 5.x kernel... 
Or try to update the 16.04 Dell version to 19.04, then to 20.04 and see if it still works. 
If it does, Bob's your uncle, if not.... 
For now I've got a bootable USB stick with Dell original software on it to make the disk as if it just left the factory.. 
Time to go to sleep.

---

### Post by georgesgiralt on 2020-05-04
So, here am I again.
I spend yesterday and a part of today restoring the Dell software, using it to test and upgrading it. And do it again because the upgrade didn't went well... And do it again.... Time consuming, to say the least, but in these lockdown period, time is not the essence ;-)
So, Dell gave a 16.04 LTS version, tweaked with an oem kernel some DKMS modules (Wifi, Bluetooth and Ethernet chip for the obvious.) and some fancy things like a G3 wallpaper or Dell restore app... And maybe something else, who knows ? 
I kept the original SSD as delivered by Dell to have a reference and had to clean up the 256Gb SSD I use instead. Pvmove is my friend... 
I restored the Dell software (which cleaned up the MOK Microsoft keys, BTW... ) and had a quite identical 16.04LTS with oem tweaks. To be on the safe side (belt and suspenders type) I had removed the 2TB disk holding Ubuntu 19.10, Windows 10 and more importantly my files...  
Then, I put back the disk into the machine, and did my copy, and cat test to see how the computer behaves. Perfect. As expected. 16.04 has 4.13 oem kernel. (Maybe I can get the source, I did not check)
Then I upgraded to 18.04LTS (Dell had disabled this ...) And then turned on again the Dell software repositories  upgraded the Ubuntu and put the disk back in and tested the copy/cat file. Perfect. This was done with a 4.13-0-1080oem kernel. Still perfect. 
Then I wanted to go up to 19.10... And everything went south.
First, I did the upgrade in the graphical environment. Something went wrong and the upgrade frooze, in an unrecoverable way. So I started right again from the beginning. Thanks that the SSD is fast... Same problem. So I started again and this time made a backup (dump) of the 18.04 version, then did the upgrade in a console. The upgrade finished "flawlessly"  but upon reboot, impossible to get the graphical session, even if the gdm shows... 
The kernel did not get past the 4.13.0-1080oem version and it seems it is not enough for 19.10 to work. I'm too tired to analyze or troubleshoot but, something is amiss here. 
Add to this, I now have to clean up the MOK table, and that the latest upgrade, done with the hard disk installed messed up badly with the EFI entries, Grub settings on the HDD and I'm fed up. 
Now, I run the 19.10 version on the hdd and LVM. The ssd has 19.10 and seems not to be working (but I have to triple check again) ..
So I'm left with :
1) restore the SSD to 18.04 oem and make it work. Then copy it over the LVM HDD to make it back to 18.04 (and loose all the configuration and installed software) and return the SSD as a fast PV ...
2) Try to find a suitable 19.10 capable kernel with the Dell oem tweaks... And test it.... 
3) sell the Dell G3 and revert to the nice Lenovo, old but good.... 
4) Go fishing .....
Well this last one is not possible right now... 

I'll be happy to hear from all of you and get some advice... 
Have a nice day and stay safe !

---

### Post by georgesgiralt on 2020-05-05
Update : Nothing related to kernel version in my problem.
The Xorg nouveau driver had kicked in instead of the Nvidia based one and wreck havoc. Once modprobe.blacklist=nouveau was added to the Kernel boot parameters, everything was fine.
So I could test for presence of my problem. 
As I suspected (due to the kernel version being used), everything is fine ! And performance is very good.
The Nvidia driver was broken (hence the Nouveau use) and I had to install it again. 
Now, I'm left with putting this into the LVM 19.10 version I prefer to use and to clean up the mess on the UEFI key table... And that will keep me busy for some time...

Lesson learned : Sometimes, a newer kernel does not solve problems.. But sometimes an older one could....

---

