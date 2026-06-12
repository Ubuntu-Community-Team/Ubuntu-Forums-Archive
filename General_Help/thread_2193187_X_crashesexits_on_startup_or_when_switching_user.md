---
title: "X crashes/exits on startup or when switching user"
date: 2013-12-11
forum: General Help
---

### Post by kofa on 2013-12-11
Hello,

I think it started after my Sauce upgrade: upon startup, or when switching users (my wife and I use the same box, running separate sessions on VT7 and 8). The greeter is not displayed. I've tried gathering logs. These are from attempting to log on for my user 'kofa', initiated from my wife's ('juca') session.

I use an NVIDIA G86 GeForce 8500 GT with nouveau; when the problems started (I was using nouveau at the time), I suspected a driver issue, and tried the binary nvidia drivers, but the problem stayed and I returned to nouveau.
I've also tried replacing lightdm with gdm, the same thing happens.

I'd be grateful for your help, this is very annoying. A restart (by my wife, who won't go killing/restarting processes) usually helps; killing all lightdm instances with killall, then service lightdm start also works.

Logs attached for easier grepping.

Thanks,
Kofa

Details below.

After the crash, at least colord and lightdm are stuck; ps -aux output follows:
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  27200  2268 ?        Ss   17:26   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    17:26   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    17:26   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   17:26   0:00 [kworker/0:0H]
root         7  0.0  0.0      0     0 ?        S    17:26   0:00 [migration/0]
root         8  0.0  0.0      0     0 ?        S    17:26   0:00 [rcu_bh]
root         9  0.0  0.0      0     0 ?        S    17:26   0:00 [rcuob/0]
root        10  0.0  0.0      0     0 ?        S    17:26   0:00 [rcuob/1]
root        11  0.0  0.0      0     0 ?        S    17:26   0:00 [rcuob/2]
root        12  0.0  0.0      0     0 ?        S    17:26   0:00 [rcuob/3]
root        13  0.0  0.0      0     0 ?        S    17:26   0:02 [rcu_sched]
root        14  0.0  0.0      0     0 ?        S    17:26   0:01 [rcuos/0]
root        15  0.0  0.0      0     0 ?        S    17:26   0:01 [rcuos/1]
root        16  0.0  0.0      0     0 ?        S    17:26   0:00 [rcuos/2]
root        17  0.0  0.0      0     0 ?        S    17:26   0:00 [rcuos/3]
root        18  0.0  0.0      0     0 ?        S    17:26   0:00 [watchdog/0]
root        19  0.0  0.0      0     0 ?        S    17:26   0:00 [watchdog/1]
root        20  0.0  0.0      0     0 ?        S    17:26   0:00 [migration/1]
root        21  0.0  0.0      0     0 ?        S    17:26   0:00 [ksoftirqd/1]
root        23  0.0  0.0      0     0 ?        S<   17:26   0:00 [kworker/1:0H]
root        24  0.0  0.0      0     0 ?        S<   17:26   0:00 [khelper]
root        25  0.0  0.0      0     0 ?        S    17:26   0:00 [kdevtmpfs]
root        26  0.0  0.0      0     0 ?        S<   17:26   0:00 [netns]
root        27  0.0  0.0      0     0 ?        S<   17:26   0:00 [writeback]
root        28  0.0  0.0      0     0 ?        S<   17:26   0:00 [kintegrityd]
root        29  0.0  0.0      0     0 ?        S<   17:26   0:00 [bioset]
root        30  0.0  0.0      0     0 ?        S<   17:26   0:00 [kworker/u9:0]
root        31  0.0  0.0      0     0 ?        S<   17:26   0:00 [kblockd]
root        32  0.0  0.0      0     0 ?        S<   17:26   0:00 [ata_sff]
root        33  0.0  0.0      0     0 ?        S    17:26   0:00 [khubd]
root        34  0.0  0.0      0     0 ?        S<   17:26   0:00 [md]
root        35  0.0  0.0      0     0 ?        S<   17:26   0:00 [devfreq_wq]
root        38  0.0  0.0      0     0 ?        S    17:26   0:00 [khungtaskd]
root        39  0.0  0.0      0     0 ?        S    17:26   0:08 [kswapd0]
root        40  0.0  0.0      0     0 ?        SN   17:26   0:00 [ksmd]
root        41  0.0  0.0      0     0 ?        SN   17:26   0:00 [khugepaged]
root        42  0.0  0.0      0     0 ?        S    17:26   0:00 [fsnotify_mark]
root        43  0.0  0.0      0     0 ?        S    17:26   0:00 [ecryptfs-kthrea]
root        44  0.0  0.0      0     0 ?        S<   17:26   0:00 [crypto]
root        56  0.0  0.0      0     0 ?        S<   17:26   0:00 [kthrotld]
root        77  0.0  0.0      0     0 ?        S<   17:26   0:00 [deferwq]
root        78  0.0  0.0      0     0 ?        S<   17:26   0:00 [charger_manager]
root        79  0.0  0.0      0     0 ?        S    17:26   0:05 [kworker/1:2]
root       122  0.0  0.0      0     0 ?        S    17:26   0:00 [scsi_eh_0]
root       123  0.0  0.0      0     0 ?        S    17:26   0:00 [scsi_eh_1]
root       126  0.0  0.0      0     0 ?        S    17:26   0:00 [scsi_eh_2]
root       127  0.0  0.0      0     0 ?        S    17:26   0:00 [scsi_eh_3]
root       128  0.0  0.0      0     0 ?        S    17:26   0:00 [scsi_eh_4]
root       129  0.0  0.0      0     0 ?        S    17:26   0:00 [scsi_eh_5]
root       130  0.0  0.0      0     0 ?        S    17:26   0:00 [scsi_eh_6]
root       131  0.0  0.0      0     0 ?        S    17:26   0:00 [scsi_eh_7]
root       132  0.0  0.0      0     0 ?        S    17:26   0:00 [scsi_eh_8]
root       133  0.0  0.0      0     0 ?        S    17:26   0:00 [scsi_eh_9]
root       141  0.0  0.0      0     0 ?        S<   17:26   0:00 [ttm_swap]
root       142  0.0  0.0      0     0 ?        S    17:26   0:00 [scsi_eh_10]
root       143  0.0  0.0      0     0 ?        S    17:26   0:03 [usb-storage]
root       155  0.0  0.0      0     0 ?        S<   17:26   0:00 [bioset]
root       156  0.0  0.0      0     0 ?        S    17:26   0:00 [md0_raid1]
root       161  0.0  0.0      0     0 ?        S<   17:26   0:00 [bioset]
root       162  0.0  0.0      0     0 ?        S    17:26   0:00 [md1_raid1]
root       167  0.0  0.0      0     0 ?        S<   17:26   0:00 [bioset]
root       168  0.0  0.0      0     0 ?        S    17:26   0:00 [md2_raid1]
root       173  0.0  0.0      0     0 ?        S<   17:26   0:00 [bioset]
root       174  0.0  0.0      0     0 ?        S    17:26   0:00 [md3_raid1]
root       243  0.0  0.0      0     0 ?        S<   17:26   0:00 [kworker/u9:1]
root       249  0.0  0.0      0     0 ?        S    17:26   0:00 [jbd2/sdd1-8]
root       250  0.0  0.0      0     0 ?        S<   17:26   0:00 [ext4-rsv-conver]
root       251  0.0  0.0      0     0 ?        S<   17:26   0:00 [ext4-unrsv-conv]
root       379  0.0  0.0  17320   496 ?        S    17:26   0:00 upstart-udev-bridge --daemon
root       391  0.0  0.0  43424  1796 ?        Ss   17:26   0:00 /lib/systemd/systemd-udevd --daemon
root       459  0.0  0.0      0     0 ?        S<   17:26   0:00 [hd-audio0]
root       468  0.0  0.0      0     0 ?        S<   17:26   0:00 [cfg80211]
root       621  0.0  0.0  15260   596 ?        S    17:26   0:00 upstart-socket-bridge --daemon
root       742  0.0  0.0      0     0 ?        S<   17:26   0:00 [kvm-irqfd-clean]
root       778  0.0  0.0  32316   740 ?        Ss   17:26   0:00 wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
root       887  0.0  0.0      0     0 ?        S    17:26   0:00 [jbd2/sdc5-8]
root       888  0.0  0.0      0     0 ?        S<   17:26   0:00 [ext4-rsv-conver]
root       889  0.0  0.0      0     0 ?        S<   17:26   0:00 [ext4-unrsv-conv]
root       893  0.0  0.0      0     0 ?        S    17:26   0:06 [kworker/0:2]
root       918  0.0  0.0      0     0 ?        S    17:26   0:00 [jbd2/md3-8]
root       919  0.0  0.0      0     0 ?        S<   17:26   0:00 [ext4-rsv-conver]
root       920  0.0  0.0      0     0 ?        S<   17:26   0:00 [ext4-unrsv-conv]
102        949  0.0  0.0  31912  2384 ?        Ss   17:26   0:00 dbus-daemon --system --fork
root      1009  0.0  0.0  19264  1224 ?        Ss   17:26   0:00 /usr/sbin/bluetoothd
root      1012  0.0  0.0  37152  1376 ?        Ss   17:26   0:00 /lib/systemd/systemd-logind
root      1035  0.0  0.0      0     0 ?        S<   17:26   0:00 [krfcommd]
syslog    1045  0.0  0.0 247472  1064 ?        Sl   17:26   0:00 rsyslogd -c5
avahi     1080  0.0  0.0  32360  1136 ?        S    17:26   0:00 avahi-daemon: running [eagle.local]
avahi     1082  0.0  0.0  32228   336 ?        S    17:26   0:00 avahi-daemon: chroot helper
root      1148  0.0  0.0  15536   660 ?        S    17:26   0:00 upstart-file-bridge --daemon
colord    1151  0.0  0.0 292700  4000 ?        Sl   17:26   0:00 /usr/lib/colord/colord
root      1158  0.0  0.0  73072  2424 ?        Ss   17:26   0:00 /usr/sbin/cups-browsed
root      1221  0.0  0.0  83484  2364 ?        Ss   17:27   0:00 /usr/sbin/modem-manager
root      1253  0.0  0.1 268368  4564 ?        Ssl  17:27   0:00 NetworkManager
root      1262  0.0  0.1 272300  4268 ?        Sl   17:27   0:00 /usr/lib/policykit-1/polkitd --no-debug
root      1358  0.0  0.0  21504   608 tty4     Ss+  17:27   0:00 /sbin/getty -8 38400 tty4
root      1370  0.0  0.0  21504   592 tty5     Ss+  17:27   0:00 /sbin/getty -8 38400 tty5
root      1386  0.0  0.0  21504   604 tty2     Ss+  17:27   0:00 /sbin/getty -8 38400 tty2
root      1387  0.0  0.0  21504   596 tty3     Ss+  17:27   0:00 /sbin/getty -8 38400 tty3
root      1392  0.0  0.0  21504   608 tty6     Ss+  17:27   0:00 /sbin/getty -8 38400 tty6
root      1443  0.0  0.0  61092  1504 ?        Ss   17:27   0:00 /usr/sbin/sshd -D
root      1471  0.0  0.0   4376   568 ?        Ss   17:27   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1477  0.0  0.0  25804   832 ?        Ss   17:27   0:00 cron
whoopsie  1479  0.0  0.1 506328  4220 ?        Ssl  17:27   0:00 whoopsie
root      1544  0.0  0.0 275628  3108 ?        SLsl 17:27   0:00 lightdm
root      1638  0.0  0.0  25160  1252 ?        Ss   17:27   0:00 /usr/lib/postfix/master
postfix   1641  0.0  0.0  27384  1276 ?        S    17:27   0:00 qmgr -l -t unix -u
root      1670  0.0  0.0 278504  3044 ?        Sl   17:27   0:00 /usr/lib/accountsservice/accounts-daemon
root      1684  0.0  0.0      0     0 ?        S    17:27   0:00 [kauditd]
root      1737  0.0  0.0 232808  3484 ?        Sl   17:27   0:00 /usr/lib/upower/upowerd
root      1829  0.0  0.0 1047564 3692 ?        Sl   17:27   0:00 /usr/sbin/console-kit-daemon --no-daemon
rtkit     1900  0.0  0.0 168920   952 ?        SNl  17:27   0:00 /usr/lib/rtkit/rtkit-daemon
root      2062  0.0  0.0  24584  1564 ?        S    17:27   0:00 /usr/sbin/smartd --pidfile /var/run/smartd.pid
root      2102  0.0  0.0      0     0 ?        S<   17:27   0:00 [iprt]
root      2148  0.0  0.0  13420   540 ?        Ss   17:27   0:00 /sbin/mdadm --monitor --pid-file /run/mdadm/monitor.pid --daemonise --scan --syslog
root      2208  8.4  9.7 1952592 393828 ?      SNl  17:27  16:20 /usr/bin/java -Dfile.encoding=UTF-8 -Dapp=CrashPlanService -DappBaseName=CrashPlan -Xms20m -Xmx512m -Djava.net.preferIPv4Stack=true -Dsun.ne$
root      2233  0.0  0.0  84440  2284 tty1     Ss   17:27   0:00 /bin/login --
root      2783  0.0  0.1 363288  5200 ?        Sl   17:27   0:05 /usr/lib/udisks2/udisksd --no-debug
root      5125  0.0  0.0 107084  2872 ?        Ss   17:46   0:00 /usr/sbin/winbindd -F
root      5128  0.0  0.0 107084  1648 ?        S    17:46   0:00 /usr/sbin/winbindd -F
root      5673  0.0  0.0  75048  3328 ?        Ss   17:46   0:00 /usr/sbin/cupsd -F
root      5840  0.0  0.0      0     0 ?        S    18:58   0:01 [kworker/u8:0]
postfix   5889  0.0  0.0  27224  1092 ?        S    19:06   0:00 pickup -l -t unix -u -c
root      6014  0.0  0.0      0     0 ?        S    20:05   0:00 [kworker/0:1]
root      6022  0.0  0.0      0     0 ?        S    20:17   0:00 [kworker/1:1]
root      6173  0.0  0.0 100512  2676 ?        S    20:26   0:00 lightdm --session-child 25 32
kofa      6308  0.0  0.1  29092  4660 tty1     S    20:27   0:00 -bash
root      6404  0.0  0.0  76908  2424 tty1     S    20:27   0:00 sudo -i
root      6405  0.0  0.0  28228  3940 tty1     S    20:27   0:00 -bash
root      6530  0.0  0.0      0     0 ?        S    20:32   0:00 [kworker/u8:1]
root      6603  0.0  0.0      0     0 ?        S    20:37   0:00 [kworker/u8:2]
root      6677  0.0  0.0  24124  1372 tty1     R+   20:41   0:00 ps aux

Logs (long...)

/var/log/syslog:
Dec 11 20:26:58 eagle acpid: client connected from 6087[0:0]
Dec 11 20:26:58 eagle acpid: 1 client rule loaded
Dec 11 20:26:59 eagle gnome-session[2524]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Dec 11 20:26:59 eagle colord: device removed: xrandr-Hewlett Packard-HP ZR22w-CN403201HN
Dec 11 20:26:59 eagle colord: Profile removed: icc-015f22a2f2f38fddf3f14faf8fe69984
Dec 11 20:26:59 eagle colord: Profile removed: icc-f7c51cc481618b181a72a34a0c535954

/var/log/Xorg.0.log:
[ 10816.292] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 10816.292] (II) NOUVEAU(0): NVLeaveVT is called.
[ 10817.230] (II) evdev: AT Translated Set 2 keyboard: Close
[ 10817.230] (II) UnloadModule: "evdev"
[ 10817.230] (II) evdev: Logitech USB-PS/2 Optical Mouse: Close
[ 10817.230] (II) UnloadModule: "evdev"
[ 10817.230] (II) evdev: Power Button: Close
[ 10817.231] (II) UnloadModule: "evdev"
[ 10817.231] (II) evdev: Power Button: Close
[ 10817.231] (II) UnloadModule: "evdev"
[ 10817.235] (II) NOUVEAU(0): Closed GPU channel 0
[ 10817.237] (EE) Server terminated successfully (0). Closing log file.

/var/log/Xorg.1.log:
[ 10816.187]
X.Org X Server 1.14.3
Release Date: 2013-09-12
[ 10816.187] X Protocol Version 11, Revision 0
[ 10816.187] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[ 10816.187] Current Operating System: Linux eagle 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64
[ 10816.187] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=3e1c180e-a0de-4678-aef3-1e474e52ff94 ro quiet splash vt.handoff=7
[ 10816.187] Build Date: 15 October 2013  09:23:37AM
[ 10816.187] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support)
[ 10816.187] Current version of pixman: 0.30.2
[ 10816.187]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[ 10816.187] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 10816.187] (==) Log file: "/var/log/Xorg.1.log", Time: Wed Dec 11 20:26:58 2013
[ 10816.189] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 10816.191] (==) No Layout section.  Using the first Screen section.
[ 10816.191] (==) No screen section available. Using defaults.
[ 10816.191] (**) |-->Screen "Default Screen Section" (0)
[ 10816.191] (**) |   |-->Monitor "<default monitor>"
[ 10816.191] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[ 10816.191] (==) Automatically adding devices
[ 10816.191] (==) Automatically enabling devices
[ 10816.191] (==) Automatically adding GPU devices
[ 10816.193] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 10816.193]    Entry deleted from font path.
[ 10816.193] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 10816.193]    Entry deleted from font path.
[ 10816.193] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 10816.193]    Entry deleted from font path.
[ 10816.194] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 10816.194]    Entry deleted from font path.
[ 10816.194] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 10816.194]    Entry deleted from font path.
[ 10816.194] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[ 10816.194] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 10816.194] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 10816.194] (II) Loader magic: 0x7fdc4ce7ad20
[ 10816.194] (II) Module ABI versions:
[ 10816.194]    X.Org ANSI C Emulation: 0.4
[ 10816.194]    X.Org Video Driver: 14.1
[ 10816.194]    X.Org XInput driver : 19.1
[ 10816.194]    X.Org Server Extension : 7.0
[ 10816.194] (II) xfree86: Adding drm device (/dev/dri/card0)
[ 10816.194] setversion 1.4 failed
[ 10816.194] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[ 10816.196] (--) PCI:*(0:1:0:0) 10de:0421:1043:8264 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000c000/128, BIOS @ 0x????????/131072
[ 10816.196] (II) Open ACPI successful (/var/run/acpid.socket)
[ 10816.196] Initializing built-in extension Generic Event Extension
[ 10816.196] Initializing built-in extension SHAPE
[ 10816.196] Initializing built-in extension MIT-SHM
[ 10816.196] Initializing built-in extension XInputExtension
[ 10816.196] Initializing built-in extension XTEST
[ 10816.196] Initializing built-in extension BIG-REQUESTS
[ 10816.196] Initializing built-in extension SYNC
[ 10816.196] Initializing built-in extension XKEYBOARD
[ 10816.197] Initializing built-in extension XC-MISC
[ 10816.197] Initializing built-in extension SECURITY
[ 10816.197] Initializing built-in extension XINERAMA
[ 10816.197] Initializing built-in extension XFIXES
[ 10816.197] Initializing built-in extension RENDER
[ 10816.197] Initializing built-in extension RANDR
[ 10816.197] Initializing built-in extension COMPOSITE
[ 10816.197] Initializing built-in extension DAMAGE
[ 10816.197] Initializing built-in extension MIT-SCREEN-SAVER
[ 10816.197] Initializing built-in extension DOUBLE-BUFFER
[ 10816.197] Initializing built-in extension RECORD
[ 10816.197] Initializing built-in extension DPMS
[ 10816.197] Initializing built-in extension X-Resource
[ 10816.197] Initializing built-in extension XVideo
[ 10816.197] Initializing built-in extension XVideo-MotionCompensation
[ 10816.197] Initializing built-in extension SELinux
[ 10816.197] Initializing built-in extension XFree86-VidModeExtension
[ 10816.196] (--) PCI:*(0:1:0:0) 10de:0421:1043:8264 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000c000/128, BIOS @ 0x????????/131072
[ 10816.196] (II) Open ACPI successful (/var/run/acpid.socket)
[ 10816.196] Initializing built-in extension Generic Event Extension
[ 10816.196] Initializing built-in extension SHAPE
[ 10816.196] Initializing built-in extension MIT-SHM
[ 10816.196] Initializing built-in extension XInputExtension
[ 10816.196] Initializing built-in extension XTEST
[ 10816.196] Initializing built-in extension BIG-REQUESTS
[ 10816.196] Initializing built-in extension SYNC
[ 10816.196] Initializing built-in extension XKEYBOARD
[ 10816.197] Initializing built-in extension XC-MISC
[ 10816.197] Initializing built-in extension SECURITY
[ 10816.197] Initializing built-in extension XINERAMA
[ 10816.197] Initializing built-in extension XFIXES
[ 10816.197] Initializing built-in extension RENDER
[ 10816.197] Initializing built-in extension RANDR
[ 10816.197] Initializing built-in extension COMPOSITE
[ 10816.197] Initializing built-in extension DAMAGE
[ 10816.197] Initializing built-in extension MIT-SCREEN-SAVER
[ 10816.197] Initializing built-in extension DOUBLE-BUFFER
[ 10816.197] Initializing built-in extension RECORD
[ 10816.197] Initializing built-in extension DPMS
[ 10816.197] Initializing built-in extension X-Resource
[ 10816.197] Initializing built-in extension XVideo
[ 10816.197] Initializing built-in extension XVideo-MotionCompensation
[ 10816.197] Initializing built-in extension SELinux
[ 10816.197] Initializing built-in extension XFree86-VidModeExtension
[ 10816.196] (--) PCI:*(0:1:0:0) 10de:0421:1043:8264 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000c000/128, BIOS @ 0x????????/131072
[ 10816.196] (II) Open ACPI successful (/var/run/acpid.socket)
[ 10816.196] Initializing built-in extension Generic Event Extension
[ 10816.196] Initializing built-in extension SHAPE
[ 10816.196] Initializing built-in extension MIT-SHM
[ 10816.196] Initializing built-in extension XInputExtension
[ 10816.196] Initializing built-in extension XTEST
[ 10816.196] Initializing built-in extension BIG-REQUESTS
[ 10816.196] Initializing built-in extension SYNC
[ 10816.196] Initializing built-in extension XKEYBOARD
[ 10816.197] Initializing built-in extension XC-MISC
[ 10816.197] Initializing built-in extension SECURITY
[ 10816.197] Initializing built-in extension XINERAMA
[ 10816.197] Initializing built-in extension XFIXES
[ 10816.197] Initializing built-in extension RENDER
[ 10816.197] Initializing built-in extension RANDR
[ 10816.197] Initializing built-in extension COMPOSITE
[ 10816.197] Initializing built-in extension DAMAGE
[ 10816.197] Initializing built-in extension MIT-SCREEN-SAVER
[ 10816.197] Initializing built-in extension DOUBLE-BUFFER
[ 10816.197] Initializing built-in extension RECORD
[ 10816.197] Initializing built-in extension DPMS
[ 10816.197] Initializing built-in extension X-Resource
[ 10816.197] Initializing built-in extension XVideo
[ 10816.197] Initializing built-in extension XVideo-MotionCompensation
[ 10816.197] Initializing built-in extension SELinux
[ 10816.197] Initializing built-in extension XFree86-VidModeExtension
[ 10816.197] Initializing built-in extension XFree86-DGA
[ 10816.197] Initializing built-in extension XFree86-DRI
[ 10816.197] Initializing built-in extension DRI2
[ 10816.197] (II) LoadModule: "glx"
[ 10816.199] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 10816.201] (II) Module glx: vendor="X.Org Foundation"
[ 10816.202]    compiled for 1.14.3, module version = 1.0.0
[ 10816.202]    ABI class: X.Org Server Extension, version 7.0
[ 10816.202] (==) AIGLX enabled
[ 10816.202] Loading extension GLX
[ 10816.202] (==) Matched nvidia as autoconfigured driver 0
[ 10816.202] (==) Matched nouveau as autoconfigured driver 1
[ 10816.202] (==) Matched vesa as autoconfigured driver 2
[ 10816.202] (==) Matched modesetting as autoconfigured driver 3
[ 10816.202] (==) Matched fbdev as autoconfigured driver 4
[ 10816.202] (==) Assigned the driver to the xf86ConfigLayout
[ 10816.202] (II) LoadModule: "nvidia"
[ 10816.205] (WW) Warning, couldn't open module nvidia
[ 10816.205] (II) UnloadModule: "nvidia"
[ 10816.205] (II) Unloading nvidia
[ 10816.205] (EE) Failed to load module "nvidia" (module does not exist, 0)
[ 10816.205] (II) LoadModule: "nouveau"
[ 10816.205] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[ 10816.206] (II) Module nouveau: vendor="X.Org Foundation"
[ 10816.206]    compiled for 1.14.2.901, module version = 1.0.9
[ 10816.207]    Module class: X.Org Video Driver
[ 10816.207]    ABI class: X.Org Video Driver, version 14.1
[ 10816.207] (II) LoadModule: "vesa"
[ 10816.207] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 10816.207] (II) Module vesa: vendor="X.Org Foundation"
[ 10816.207]    compiled for 1.14.1, module version = 2.3.2
[ 10816.207]    Module class: X.Org Video Driver
[ 10816.207]    ABI class: X.Org Video Driver, version 14.1
[ 10816.207] (II) LoadModule: "modesetting"
[ 10816.208] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 10816.208] (II) Module modesetting: vendor="X.Org Foundation"
[ 10816.208]    compiled for 1.14.1, module version = 0.8.0
[ 10816.208]    Module class: X.Org Video Driver
[ 10816.208]    ABI class: X.Org Video Driver, version 14.1
[ 10816.208] (II) LoadModule: "fbdev"
[ 10816.208] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 10816.209] (II) Module fbdev: vendor="X.Org Foundation"
[ 10816.209]    compiled for 1.14.1, module version = 0.4.3
[ 10816.209]    Module class: X.Org Video Driver
[ 10816.209]    ABI class: X.Org Video Driver, version 14.1
[ 10816.209] (==) Matched nvidia as autoconfigured driver 0
[ 10816.209] (==) Matched nouveau as autoconfigured driver 1
[ 10816.209] (==) Matched vesa as autoconfigured driver 2
[ 10816.209] (==) Matched modesetting as autoconfigured driver 3
[ 10816.209] (==) Matched fbdev as autoconfigured driver 4
[ 10816.209] (==) Assigned the driver to the xf86ConfigLayout
[ 10816.209] (II) LoadModule: "nvidia"
[ 10816.209] (WW) Warning, couldn't open module nvidia
[ 10816.209] (II) UnloadModule: "nvidia"
[ 10816.209] (II) Unloading nvidia
[ 10816.209] (EE) Failed to load module "nvidia" (module does not exist, 0)
[ 10816.209] (II) LoadModule: "nouveau"
[ 10816.210] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[ 10816.210] (II) Module nouveau: vendor="X.Org Foundation"
[ 10816.210]    compiled for 1.14.2.901, module version = 1.0.9
[ 10816.210]    Module class: X.Org Video Driver
[ 10816.210]    ABI class: X.Org Video Driver, version 14.1
[ 10816.210] (II) UnloadModule: "nouveau"
[ 10816.210] (II) Unloading nouveau
[ 10816.210] (II) Failed to load module "nouveau" (already loaded, 0)
[ 10816.210] (II) LoadModule: "vesa"
[ 10816.210] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 10816.210] (II) Module vesa: vendor="X.Org Foundation"
[ 10816.210]    compiled for 1.14.1, module version = 2.3.2
[ 10816.210]    Module class: X.Org Video Driver
[ 10816.210]    ABI class: X.Org Video Driver, version 14.1
[ 10816.210] (II) UnloadModule: "vesa"
[ 10816.210] (II) Unloading vesa
[ 10816.210] (II) Failed to load module "vesa" (already loaded, 0)
[ 10816.210] (II) LoadModule: "modesetting"
[ 10816.210] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 10816.210] (II) Module modesetting: vendor="X.Org Foundation"
[ 10816.210]    compiled for 1.14.1, module version = 0.8.0
[ 10816.210]    Module class: X.Org Video Driver
[ 10816.210]    ABI class: X.Org Video Driver, version 14.1
[ 10816.210] (II) UnloadModule: "modesetting"
[ 10816.210] (II) Unloading modesetting
[ 10816.210] (II) Failed to load module "modesetting" (already loaded, 0)
[ 10816.210] (II) LoadModule: "fbdev"
[ 10816.211] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 10816.211] (II) Module fbdev: vendor="X.Org Foundation"
[ 10816.211]    compiled for 1.14.1, module version = 0.4.3
[ 10816.211]    Module class: X.Org Video Driver
[ 10816.211]    ABI class: X.Org Video Driver, version 14.1
[ 10816.211] (II) UnloadModule: "fbdev"
[ 10816.211] (II) Unloading fbdev
[ 10816.211] (II) Failed to load module "fbdev" (already loaded, 0)
[ 10816.211] (II) NOUVEAU driver Date:   Wed Jul 31 10:51:03 2013 +1000
[ 10816.211] (II) NOUVEAU driver for NVIDIA chipset families :
[ 10816.211]    RIVA TNT        (NV04)
[ 10816.211]    RIVA TNT2       (NV05)
[ 10816.211]    GeForce 256     (NV10)
[ 10816.211]    GeForce 2       (NV11, NV15)
[ 10816.211]    GeForce 4MX     (NV17, NV18)
[ 10816.211]    GeForce 3       (NV20)
[ 10816.211]    GeForce 4Ti     (NV25, NV28)
[ 10816.211]    GeForce FX      (NV3x)
[ 10816.211]    GeForce 6       (NV4x)
[ 10816.211]    GeForce 7       (G7x)
[ 10816.211]    GeForce 8       (G8x)
[ 10816.211]    GeForce GTX 200 (NVA0)
[ 10816.211]    GeForce GTX 400 (NVC0)
[ 10816.211] (II) VESA: driver for VESA chipsets: vesa
[ 10816.211] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[ 10816.211] (II) FBDEV: driver for framebuffer: fbdev
[ 10816.211] (++) using VT number 8

[ 10816.325] (II) [drm] nouveau interface version: 1.1.1
[ 10816.325] (WW) Falling back to old probe method for vesa
[ 10816.325] (WW) Falling back to old probe method for modesetting
[ 10816.325] (WW) Falling back to old probe method for fbdev
[ 10816.325] (II) Loading sub module "fbdevhw"
[ 10816.325] (II) LoadModule: "fbdevhw"
[ 10816.325] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 10816.329] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 10816.329]    compiled for 1.14.3, module version = 0.0.2
[ 10816.329]    ABI class: X.Org Video Driver, version 14.1
[ 10816.329] (II) Loading sub module "dri2"
[ 10816.329] (II) LoadModule: "dri2"
[ 10816.329] (II) Module "dri2" already built-in
[ 10816.329] (--) NOUVEAU(0): Chipset: "NVIDIA NV86"
[ 10816.329] (II) NOUVEAU(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[ 10816.329] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[ 10816.329] (==) NOUVEAU(0): RGB weight 888
[ 10816.329] (==) NOUVEAU(0): Default visual is TrueColor
[ 10816.329] (==) NOUVEAU(0): Using HW cursor
[ 10816.329] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[ 10816.329] (==) NOUVEAU(0): Page flipping enabled
[ 10816.329] (==) NOUVEAU(0): Swap limit set to 2 [Max allowed 2]
[ 10816.369] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[ 10816.392] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[ 10816.420] (II) NOUVEAU(0): EDID for output DVI-I-1
[ 10816.420] (II) NOUVEAU(0): Manufacturer: HWP  Model: 2867  Serial#: 16843009
[ 10816.420] (II) NOUVEAU(0): Year: 2010  Week: 32
[ 10816.420] (II) NOUVEAU(0): EDID Version: 1.3
[ 10816.420] (II) NOUVEAU(0): Digital Display Input
[ 10816.420] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[ 10816.420] (II) NOUVEAU(0): Gamma: 2.20
[ 10816.420] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
[ 10816.420] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[ 10816.420] (II) NOUVEAU(0): Default color space is primary color space
[ 10816.420] (II) NOUVEAU(0): First detailed timing is preferred mode
[ 10816.420] (II) NOUVEAU(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[ 10816.420] (II) NOUVEAU(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[ 10816.420] (II) NOUVEAU(0): Supported established timings:
[ 10816.420] (II) NOUVEAU(0): 720x400@70Hz
[ 10816.420] (II) NOUVEAU(0): 640x480@60Hz
[ 10816.420] (II) NOUVEAU(0): 800x600@60Hz
[ 10816.420] (II) NOUVEAU(0): 1024x768@60Hz
[ 10816.420] (II) NOUVEAU(0): Manufacturer's mask: 0
[ 10816.420] (II) NOUVEAU(0): Supported standard timings:
[ 10816.420] (II) NOUVEAU(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[ 10816.420] (II) NOUVEAU(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[ 10816.420] (II) NOUVEAU(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[ 10816.420] (II) NOUVEAU(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[ 10816.420] (II) NOUVEAU(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[ 10816.420] (II) NOUVEAU(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[ 10816.420] (II) NOUVEAU(0): Supported detailed timing:
[ 10816.420] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  475 x 267 mm
[ 10816.420] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[ 10816.420] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[ 10816.420] (II) NOUVEAU(0): Ranges: V min: 50 V max: 76 Hz, H min: 24 H max: 94 kHz, PixClock max 175 MHz
[ 10816.420] (II) NOUVEAU(0): Monitor name: HP ZR22w
[ 10816.420] (II) NOUVEAU(0): Serial No: CN403201HN
[ 10816.420] (II) NOUVEAU(0): EDID (in hex):
[ 10816.420] (II) NOUVEAU(0):   00ffffffffffff0022f0672801010101
[ 10816.420] (II) NOUVEAU(0):   2014010380301b78eeee95a3544c9926
[ 10816.420] (II) NOUVEAU(0):   0f5054a1080081c0814081809500a940
[ 10816.420] (II) NOUVEAU(0):   b30001010101023a801871382d40582c
[ 10816.420] (II) NOUVEAU(0):   4500db0b1100001e000000fd00324c18
[ 10816.420] (II) NOUVEAU(0):   5e11000a202020202020000000fc0048
[ 10816.420] (II) NOUVEAU(0):   50205a523232770a20202020000000ff
[ 10816.420] (II) NOUVEAU(0):   00434e343033323031484e0a202000ec
[ 10816.420] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[ 10816.420] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 10816.420] (II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[ 10816.420] (II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[ 10816.420] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 10816.420] (II) NOUVEAU(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[ 10816.420] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 10816.420] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[ 10816.420] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 10816.420] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 10816.420] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 10816.420] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 10816.441] (II) NOUVEAU(0): EDID for output VGA-1
[ 10816.441] (II) NOUVEAU(0): Output DVI-I-1 connected
[ 10816.441] (II) NOUVEAU(0): Output VGA-1 disconnected
[ 10816.441] (II) NOUVEAU(0): Using exact sizes for initial modes
[ 10816.441] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 1920x1080
[ 10816.441] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 10816.441] (--) NOUVEAU(0): Virtual size is 1920x1080 (pitch 0)
[ 10816.441] (**) NOUVEAU(0):  Driver mode "1920x1080": 148.5 MHz (scaled from 0.0 MHz), 67.5 kHz, 60.0 Hz
[ 10816.441] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 10816.441] (**) NOUVEAU(0):  Driver mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
[ 10816.441] (II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[ 10816.441] (**) NOUVEAU(0):  Driver mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
[ 10816.441] (II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[ 10816.441] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[ 10816.441] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 10816.441] (**) NOUVEAU(0):  Driver mode "1440x900": 88.8 MHz (scaled from 0.0 MHz), 55.5 kHz, 59.9 Hz
[ 10816.441] (II) NOUVEAU(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[ 10816.441] (**) NOUVEAU(0):  Driver mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
[ 10816.441] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 10816.441] (**) NOUVEAU(0):  Mode "1280x720": 74.4 MHz (scaled from 0.0 MHz), 44.7 kHz, 60.0 Hz
[ 10816.442] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[ 10816.442] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[ 10816.442] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 10816.442] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[ 10816.442] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 10816.442] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[ 10816.442] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 10816.442] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[ 10816.442] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 10816.442] (==) NOUVEAU(0): DPI set to (96, 96)
[ 10816.442] (II) Loading sub module "fb"
[ 10816.442] (II) LoadModule: "fb"
[ 10816.442] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 10816.444] (II) Module fb: vendor="X.Org Foundation"
[ 10816.444]    compiled for 1.14.3, module version = 1.0.0
[ 10816.444]    ABI class: X.Org ANSI C Emulation, version 0.4
[ 10816.444] (II) Loading sub module "exa"
[ 10816.444] (II) LoadModule: "exa"
[ 10816.444] (II) Loading /usr/lib/xorg/modules/libexa.so
[ 10816.444] (II) Module exa: vendor="X.Org Foundation"
[ 10816.444]    compiled for 1.14.3, module version = 2.6.0
[ 10816.444]    ABI class: X.Org Video Driver, version 14.1
[ 10816.444] (II) Loading sub module "shadowfb"
[ 10816.444] (II) LoadModule: "shadowfb"
[ 10816.444] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[ 10816.444] (II) Module shadowfb: vendor="X.Org Foundation"
[ 10816.444]    compiled for 1.14.3, module version = 1.0.0
[ 10816.444]    ABI class: X.Org ANSI C Emulation, version 0.4
[ 10816.444] (II) UnloadModule: "vesa"
[ 10816.444] (II) Unloading vesa
[ 10816.444] (II) UnloadModule: "modesetting"
[ 10816.444] (II) Unloading modesetting
[ 10816.444] (II) UnloadModule: "fbdev"
[ 10816.445] (II) Unloading fbdev
[ 10816.445] (II) UnloadSubModule: "fbdevhw"
[ 10816.445] (II) Unloading fbdevhw
[ 10816.445] (--) Depth 24 pixmap format is 32 bpp
[ 10816.445] (II) NOUVEAU(0): Opened GPU channel 0
[ 10816.449] (II) NOUVEAU(0): [DRI2] Setup complete
[ 10816.449] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[ 10816.449] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[ 10816.449] (II) EXA(0): Driver allocated offscreen pixmaps
[ 10816.449] (II) EXA(0): Driver registered support for the following operations:
[ 10816.449] (II)         Solid
[ 10816.449] (II)         Copy
[ 10816.449] (II)         Composite (RENDER acceleration)
[ 10816.449] (II)         UploadToScreen
[ 10816.449] (II)         DownloadFromScreen
[ 10816.449] (==) NOUVEAU(0): Backing store disabled
[ 10816.449] (==) NOUVEAU(0): Silken mouse enabled
[ 10816.450] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[ 10816.450] (II) NOUVEAU(0): [XvMC] Extension initialized.
[ 10816.450] (==) NOUVEAU(0): DPMS enabled
[ 10816.450] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 10816.450] (--) RandR disabled
[ 10816.456] (II) SELinux: Disabled on system
[ 10816.512] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[ 10816.512] (II) AIGLX: enabled GLX_INTEL_swap_event
[ 10816.512] (II) AIGLX: enabled GLX_ARB_create_context
[ 10816.512] (II) AIGLX: enabled GLX_ARB_create_context_profile
[ 10816.512] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[ 10816.512] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[ 10816.513] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[ 10816.513] (II) AIGLX: Loaded and initialized nouveau
[ 10816.513] (II) GLX: Initialized DRI2 GL provider for screen 0
[ 10816.515] (II) NOUVEAU(0): NVEnterVT is called.
[ 10816.540] (II) NOUVEAU(0): Setting screen physical size to 508 x 285
[ 10816.540] resize called 1920 1080
[ 10816.551] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 10816.555] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 10816.555] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 10816.555] (II) LoadModule: "evdev"
[ 10816.555] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 10816.555] (II) Module evdev: vendor="X.Org Foundation"
[ 10816.556]    compiled for 1.14.1, module version = 2.7.3
[ 10816.556]    Module class: X.Org XInput Driver
[ 10816.556]    ABI class: X.Org XInput driver, version 19.1
[ 10816.556] (II) Using input driver 'evdev' for 'Power Button'
[ 10816.556] (**) Power Button: always reports core events
[ 10816.556] (**) evdev: Power Button: Device: "/dev/input/event1"
[ 10816.556] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 10816.556] (--) evdev: Power Button: Found keys
[ 10816.556] (II) evdev: Power Button: Configuring as keyboard
[ 10816.556] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[ 10816.556] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 10816.556] (**) Option "xkb_rules" "evdev"
[ 10816.556] (**) Option "xkb_model" "pc105"
[ 10816.556] (**) Option "xkb_layout" "hu"
[ 10816.558] (II) XKB: reuse xkmfile /var/lib/xkb/server-544CA222969D37ADB2821D0E82B6A6D6FDEF206B.xkm
[ 10816.559] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 10816.559] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 10816.559] (II) Using input driver 'evdev' for 'Power Button'
[ 10816.559] (**) Power Button: always reports core events
[ 10816.559] (**) evdev: Power Button: Device: "/dev/input/event0"
[ 10816.559] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 10816.559] (--) evdev: Power Button: Found keys
[ 10816.559] (II) evdev: Power Button: Configuring as keyboard
[ 10816.559] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[ 10816.559] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[ 10816.559] (**) Option "xkb_rules" "evdev"
[ 10816.559] (**) Option "xkb_model" "pc105"
[ 10816.559] (**) Option "xkb_layout" "hu"
[ 10816.559] (II) config/udev: Adding drm device (/dev/dri/card0)
[ 10816.559] (II) xfree86: Adding drm device (/dev/dri/card0)
[ 10816.560] setversion 1.4 failed
[ 10816.560] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[ 10816.560] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event3)
[ 10816.560] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[ 10816.560] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[ 10816.560] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[ 10816.560] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event3"
[ 10816.560] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc03e
[ 10816.560] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[ 10816.560] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[ 10816.560] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[ 10816.560] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[ 10816.560] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[ 10816.560] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[ 10816.560] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[ 10816.560] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 10816.560] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[ 10816.560] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 8)
[ 10816.560] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[ 10816.560] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[ 10816.560] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[ 10816.560] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[ 10816.560] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[ 10816.561] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[ 10816.561] (II) No input driver specified, ignoring this device.
[ 10816.561] (II) This device may have been added with another device file.
[ 10816.561] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event10)
[ 10816.561] (II) No input driver specified, ignoring this device.
[ 10816.561] (II) This device may have been added with another device file.
[ 10816.561] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event11)
[ 10816.561] (II) No input driver specified, ignoring this device.
[ 10816.561] (II) This device may have been added with another device file.
[ 10816.562] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[ 10816.562] (II) No input driver specified, ignoring this device.
[ 10816.562] (II) This device may have been added with another device file.
[ 10816.562] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[ 10816.562] (II) No input driver specified, ignoring this device.
[ 10816.562] (II) This device may have been added with another device file.
[ 10816.562] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[ 10816.562] (II) No input driver specified, ignoring this device.
[ 10816.562] (II) This device may have been added with another device file.
[ 10816.563] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[ 10816.563] (II) No input driver specified, ignoring this device.
[ 10816.563] (II) This device may have been added with another device file.
[ 10816.563] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[ 10816.563] (II) No input driver specified, ignoring this device.
[ 10816.563] (II) This device may have been added with another device file.
[ 10816.563] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[ 10816.563] (II) No input driver specified, ignoring this device.
[ 10816.563] (II) This device may have been added with another device file.
[ 10816.564] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[ 10816.564] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[ 10816.564] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[ 10816.564] (**) AT Translated Set 2 keyboard: always reports core events
[ 10816.564] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[ 10816.564] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[ 10816.564] (--) evdev: AT Translated Set 2 keyboard: Found keys
[ 10816.564] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[ 10816.564] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[ 10816.564] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[ 10816.564] (**) Option "xkb_rules" "evdev"
[ 10816.564] (**) Option "xkb_model" "pc105"
[ 10816.564] (**) Option "xkb_layout" "hu"
[ 10817.053] (II) NOUVEAU(0): EDID vendor "HWP", prod id 10343
[ 10817.053] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[ 10817.053] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[ 10817.053] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[ 10817.053] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 10817.053] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 10817.053] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 10817.053] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 10817.053] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 10817.053] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[ 10817.053] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 10817.053] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 10817.053] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[ 10817.053] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[ 10817.053] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[ 10817.312] (II) evdev: AT Translated Set 2 keyboard: Close
[ 10817.312] (II) UnloadModule: "evdev"
[ 10817.312] (II) evdev: Logitech USB-PS/2 Optical Mouse: Close
[ 10817.312] (II) UnloadModule: "evdev"
[ 10817.312] (II) evdev: Power Button: Close
[ 10817.312] (II) UnloadModule: "evdev"
[ 10817.312] (II) evdev: Power Button: Close
[ 10817.312] (II) UnloadModule: "evdev"
[ 10817.314] (II) NOUVEAU(0): NVLeaveVT is called.
[ 10817.314] (II) NOUVEAU(0): Closed GPU channel 0
[ 10817.341] (EE) Server terminated successfully (0). Closing log file.

/var/log/apport.log (I guess this is just my wife's Skype crashing to to X shutting down):
ERROR: apport (pid 6200) Wed Dec 11 20:27:00 2013: called for pid 2761, signal 6, core limit 0
ERROR: apport (pid 6200) Wed Dec 11 20:27:00 2013: executable: /usr/bin/skype (command line "skype")
ERROR: apport (pid 6200) Wed Dec 11 20:27:00 2013: gdbus call error: Error connecting: Could not connect: Connection refused

ERROR: apport (pid 6200) Wed Dec 11 20:27:00 2013: debug: session gdbus call:
ERROR: apport (pid 6200) Wed Dec 11 20:27:00 2013: apport: report /var/crash/_usr_bin_skype.1001.crash already exists and unseen, doing nothing to avoid disk usage DoS

/var/log/auth.log
Dec 11 20:26:58 eagle dbus[949]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.13" (uid=0 pid=1544 comm="lightdm ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.54" (uid=1001 pid=2630 comm="/usr/lib/x86_64-linux-gnu/indicator-session/indica")
Dec 11 20:26:58 eagle lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kofa"
Dec 11 20:26:58 eagle lightdm: pam_unix(lightdm:auth): conversation failed
Dec 11 20:26:58 eagle lightdm: pam_unix(lightdm:auth): auth could not identify password for [kofa]
Dec 11 20:26:58 eagle lightdm: pam_winbind(lightdm:auth): getting password (0x00000388)
Dec 11 20:26:58 eagle lightdm: pam_winbind(lightdm:auth): Could not retrieve user's password
Dec 11 20:26:59 eagle lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Dec 11 20:26:59 eagle lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :1
Dec 11 20:26:59 eagle lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kofa"
Dec 11 20:26:59 eagle lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Dec 11 20:26:59 eagle lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "kofa"
Dec 11 20:26:59 eagle polkitd(authority=local): Unregistered Authentication Agent for unix-session:c2 (system bus name :1.65, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale hu_HU.UTF-8) (disconnected from bus)
Dec 11 20:26:59 eagle lightdm: pam_unix(lightdm:session): session closed for user juca

/var/log/ConsoleKit/history (timestamp is 11 Dec 2013 20:27:17 in my time zone, but I guess this is me logging on to the console, since it's a bit later than the crash, at 20:26:59):
1386790037.391 type=SEAT_SESSION_ADDED : seat-id='Seat1' session-id='Session1' session-type='' session-x11-display='' session-x11-display-device='' session-display-device='/dev/tty1' session-remote-host-name='' session-is-local=TRUE session-unix-user=1000 session-creation-time='2013-12-11T19:27:17.384946Z'
1386790037.391 type=SEAT_ACTIVE_SESSION_CHANGED : seat-id='Seat1' session-id='Session1'

/var/log/lightdm/lightdm.log
[+10795.70s] DEBUG: Seat: Switching to user kofa
[+10795.70s] DEBUG: Seat: Creating user session
[+10795.71s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+10795.71s] DEBUG: Session pid=6086: Started with service 'lightdm', username 'kofa'
[+10795.72s] DEBUG: Session pid=6086: Authentication complete with return value 7: Authentication failure
[+10795.72s] DEBUG: Seat: Switching to greeter to authenticate session
[+10795.72s] DEBUG: Session pid=6086: Sending SIGTERM
[+10795.72s] DEBUG: Seat: Creating greeter session
[+10795.73s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+10795.73s] DEBUG: Seat: Creating display server of type x
[+10795.73s] DEBUG: Seat: Starting local X display
[+10795.73s] DEBUG: Using VT 8
[+10795.73s] DEBUG: DisplayServer x-1: Logging to /var/log/lightdm/x-1.log
[+10795.73s] DEBUG: DisplayServer x-1: Writing X server authority to /var/run/lightdm/root/:1
[+10795.73s] DEBUG: DisplayServer x-1: Launching X Server
[+10795.73s] DEBUG: Launching process 6087: /usr/bin/X -core :1 -auth /var/run/lightdm/root/:1 -nolisten tcp vt8 -novtswitch
[+10795.73s] DEBUG: DisplayServer x-1: Waiting for ready signal from X server :1
[+10795.73s] DEBUG: Session pid=6086: Terminated with signal 15
[+10795.73s] DEBUG: Seat: Session stopped
[+10796.14s] DEBUG: Got signal 10 from process 6087
[+10796.14s] DEBUG: DisplayServer x-1: Got signal from X server :1
[+10796.14s] DEBUG: DisplayServer x-1: Connecting to XServer :1
[+10796.14s] DEBUG: Seat: Display server ready, starting session authentication
[+10796.14s] DEBUG: Session: Setting XDG_VTNR=8
[+10796.14s] DEBUG: Session pid=6093: Started with service 'lightdm-greeter', username 'lightdm'
[+10796.21s] DEBUG: Session pid=6093: Authentication complete with return value 0: Success
[+10796.21s] DEBUG: Seat: Session authenticated, running command
[+10796.21s] DEBUG: Session pid=6093: Setting XDG_VTNR=8
[+10796.21s] DEBUG: Session pid=6093: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+10796.25s] DEBUG: Session pid=6093: Logging to /var/log/lightdm/x-1-greeter.log
[+10796.27s] DEBUG: Activating VT 8
[+10796.27s] DEBUG: Locking login1 session /org/freedesktop/login1/session/c2
[+10796.51s] DEBUG: Session pid=6093: Greeter connected version=1.8.4
[+10796.64s] DEBUG: Session pid=6093: Greeter start authentication for kofa
[+10796.64s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+10796.64s] DEBUG: Session: Setting XDG_VTNR=8
[+10796.64s] DEBUG: Session pid=6173: Started with service 'lightdm', username 'kofa'
[+10796.64s] DEBUG: Session pid=6093: Greeter start authentication for kofa
[+10796.64s] DEBUG: Session pid=6173: Sending SIGTERM
[+10796.64s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+10796.64s] DEBUG: Session: Setting XDG_VTNR=8
[+10796.64s] DEBUG: Session pid=6174: Started with service 'lightdm', username 'kofa'
[+10796.65s] DEBUG: Session pid=6174: Got 1 message(s) from PAM
[+10796.65s] DEBUG: Session pid=6093: Prompt greeter with 1 message(s)
[+10796.67s] DEBUG: Got signal 15 from process 1544
[+10796.67s] DEBUG: Caught Terminated signal, shutting down
[+10796.67s] DEBUG: Stopping display manager
[+10796.67s] DEBUG: Seat: Stopping
[+10796.67s] DEBUG: Seat: Stopping display server
[+10796.67s] DEBUG: Sending signal 15 to process 1570
[+10796.71s] DEBUG: Seat: Stopping display server
[+10796.71s] DEBUG: Sending signal 15 to process 6087
[+10796.71s] DEBUG: Seat: Stopping session
[+10796.71s] DEBUG: Session pid=2332: Sending SIGTERM
[+10796.71s] DEBUG: Seat: Stopping session
[+10796.71s] DEBUG: Session pid=6093: Sending SIGTERM
[+10796.71s] DEBUG: Seat: Stopping session
[+10796.71s] DEBUG: Session pid=6174: Sending SIGTERM
[+10796.71s] DEBUG: Session pid=6174: Terminated with signal 15
[+10796.71s] DEBUG: Session: Failed during authentication
[+10796.71s] DEBUG: Seat: Session stopped
[+10796.74s] DEBUG: Session pid=6173: Got 1 message(s) from PAM
[+10796.76s] DEBUG: Session pid=6093: Exited with return value 0
[+10796.76s] DEBUG: Seat: Session stopped
[+10796.83s] DEBUG: Process 1570 exited with return value 0
[+10796.83s] DEBUG: DisplayServer x-0: X server stopped
[+10796.83s] DEBUG: Releasing VT 7
[+10796.83s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+10796.83s] DEBUG: Seat: Display server stopped
[+10796.90s] DEBUG: Session pid=2332: Exited with return value 0
[+10796.90s] DEBUG: Seat: Session stopped
[+10796.90s] DEBUG: Process 6087 exited with return value 0
[+10796.90s] DEBUG: DisplayServer x-1: X server stopped
[+10796.90s] DEBUG: Releasing VT 8
[+10796.90s] DEBUG: DisplayServer x-1: Removing X server authority /var/run/lightdm/root/:1
[+10796.90s] DEBUG: Seat: Display server stopped
--- now this is probably me killing stuck lightdm from the console
[+11653.53s] DEBUG: Got signal 15 from process 6678
[+11653.53s] DEBUG: Caught Terminated signal, shutting down
[+11653.53s] DEBUG: Session pid=6173: Terminated with signal 15
[+11653.53s] DEBUG: Session: Failed during authentication
[+11653.53s] DEBUG: Seat: Session stopped
[+11653.53s] DEBUG: Seat: Stopped
[+11653.53s] DEBUG: Display manager stopped
[+11653.53s] DEBUG: Stopping daemon
[+11653.53s] DEBUG: Releasing VT 8
[+11653.53s] DEBUG: Exiting with return value 0

/var/log/lightdm/x-0.log
X.Org X Server 1.14.3
Release Date: 2013-09-12
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux eagle 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=3e1c180e-a0de-4678-aef3-1e474e52ff94 ro quiet splash vt.handoff=7
Build Date: 15 October 2013  09:23:37AM
xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.30.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 11 17:27:03 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
resize called 1920 1080
resize called 1920 1080
resize called 1920 1080
(II) AIGLX: Suspending AIGLX clients for VT switch
(EE) Server terminated successfully (0). Closing log file.

/var/log/lightdm/x-1-greeter.log
[+0,00s] DEBUG: unity-greeter.vala:435: Starting unity-greeter 13.10.3 UID=106 LANG=en_US.UTF-8
[+0,00s] DEBUG: unity-greeter.vala:438: Setting cursor
[+0,00s] DEBUG: unity-greeter.vala:452: Loading command line options
[+0,00s] DEBUG: unity-greeter.vala:480: Setting GTK+ settings
[+0,09s] DEBUG: unity-greeter.vala:503: Creating Unity Greeter
[+0,09s] DEBUG: unity-greeter.vala:55: Creating background surface
[+0,09s] DEBUG: Connecting to display manager...
[+0,09s] DEBUG: Wrote 17 bytes to daemon
[+0,09s] DEBUG: Read 8 bytes from daemon
[+0,09s] DEBUG: Read 173 bytes from daemon
[+0,09s] DEBUG: Connected version=1.8.4 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=false select-user=kofa show-remote-login=true
[+0,15s] DEBUG: menubar.vala:332: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0,16s] DEBUG: menubar.vala:364: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0,17s] DEBUG: Loading users from org.freedesktop.Accounts
[+0,17s] DEBUG: Loading user /org/freedesktop/Accounts/User1001
[+0,17s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0,18s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0,18s] DEBUG: Loaded session /org/freedesktop/DisplayManager/Session0 (juca)
[+0,18s] DEBUG: user-list.vala:988: Adding/updating user juca (Juca)
[+0,18s] DEBUG: user-list.vala:988: Adding/updating user kofa (Kofa)
[+0,21s] WARNING: Failed to open sessions directory: Error opening directory '/usr/share/lightdm/sessions': No such file or directory
[+0,21s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0,21s] DEBUG: Loaded session /usr/share/xsessions/kde-plasma.desktop (KDE Plasma Workspace, The desktop made by KDE)
[+0,22s] DEBUG: Loaded session /usr/share/xsessions/gnome-fallback.desktop (GNOME Flashback (No effects), This session logs you into GNOME with the traditional panel)
[+0,22s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0,22s] DEBUG: Loaded session /usr/share/xsessions/gnome-fallback-compiz.desktop (GNOME Flashback, This session logs you into GNOME with the traditional panel)
[+0,22s] WARNING: Failed to open sessions directory: Error opening directory '/usr/share/lightdm/remote-sessions': No such file or directory
[+0,22s] DEBUG: Starting authentication for user kofa...
[+0,22s] DEBUG: Wrote 20 bytes to daemon
[+0,22s] DEBUG: Starting authentication for user kofa...
[+0,22s] DEBUG: Wrote 20 bytes to daemon
[+0,22s] DEBUG: main-window.vala:181: Screen is 1920x1080 pixels
[+0,22s] DEBUG: main-window.vala:187: Monitor 0 is 1920x1080 pixels at 0,0
[+0,22s] DEBUG: unity-greeter.vala:506: Showing greeter
[+0,22s] DEBUG: unity-greeter.vala:194: Showing main window
[+0,23s] DEBUG: background.vala:470: Regenerating backgrounds
[+0,23s] DEBUG: background.vala:68: Making background /usr/share/backgrounds/warty-final-ubuntukylin.jpg at 1920x1080

(gnome-settings-daemon:6166): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


** (nm-applet:6181): WARNING **: Could not open X display

(nm-applet:6181): Gtk-WARNING **: cannot open display: :1

/var/log/lightdm/x-1.log
X.Org X Server 1.14.3
Release Date: 2013-09-12
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux eagle 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=3e1c180e-a0de-4678-aef3-1e474e52ff94 ro quiet splash vt.handoff=7
Build Date: 15 October 2013  09:23:37AM
xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.30.2
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Wed Dec 11 20:26:58 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
setversion 1.4 failed
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
resize called 1920 1080
setversion 1.4 failed
(EE) Server terminated successfully (0). Closing log file.

/var/log/upstart/lightdm.log
Stopping PAM conversation, interaction requested but not supported

/var/log/upstart/systemd-logind.log
Removed session c1.
New session c3 of user lightdm.
Linked /tmp/.X11-unix/X1 to /run/user/106/X11-display.
Removed session c3.
Removed session c2.
New session c4 of user kofa.

---

