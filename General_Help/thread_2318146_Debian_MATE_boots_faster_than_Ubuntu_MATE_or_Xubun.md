---
title: "Debian MATE boots faster than Ubuntu MATE or Xubuntu"
date: 2016-03-23
forum: General Help
---

### Post by no-spam-to-me on 2016-03-23
Hi!

I have installed Xubuntu 15.10 on my Notebook and boot time is a pain (Startup finished in 29.234s (kernel) + 33.218s (userspace) = 1min 2.452s).

So I booted Debian MATE live from usb and got: Startup finished in 6.818s (kernel) + 12.609s (userspace) = 19.427s.

That is a big difference!

To be fair I booted Ubuntu MATE live from usb and got: Startup finished in 47.775s (kernel) + 22.177s (userspace) = 1min 9.952s.

So Ubuntu MATE live takes longer to boot from usb than Xubuntu from a HDD, that is even worse.

I used systemd-analyze to show boot times.

How do I get 20s boot time with ubuntu?

---

### Post by sammiev on 2016-03-23
Depends on your hardware and memory.

I boot Xubuntu from a SSD in seconds, takes longer to type in my password than to boot.

Ubuntu Mate boots in about 30 seconds via USB cable to my external HDD on a USB2 port.

---

### Post by no-spam-to-me on 2016-03-23
Debian boots in 20s and Ubuntu needs over a minute- so I doubt that it is hardware or memory dependent.

---

### Post by Edison_James on 2016-03-23
[quote] How do I get 20s boot time with ubuntu?

Try lubuntu

---

### Post by QIII on 2016-03-23
That doesn't help the user with the stated problem: Xubuntu or Ubuntu MATE boot time.

"Use something else" is avoidance, not a solution.

---

### Post by Edison_James on 2016-03-23
lubuntu is designed to be lightweight and fast. If startup time is an issue, then it can very much be a solution.

---

### Post by QIII on 2016-03-23
Please take care not to contest Staff moderation within a thread - to wit: correcting thread drift.  If you take issue with Staff action, that is to be dealt with by means of a post in the Resolution Center.

The user is asking about the solution to an issue with two specific flavors, not Lubuntu.  Using Lubuntu does not address the stated support request. 

Please stay on topic.

---

### Post by vasa1 on 2016-03-23
> **no-spam-to-me said:**
> ...

So I booted Debian MATE live from usb and got: Startup finished in 6.818s (kernel) + 12.609s (userspace) = 19.427s.
...

I used systemd-analyze to show boot times.
...
Where did you get Debian MATE from? Could you post a link to the iso?

---

### Post by vasa1 on 2016-03-23
> **sammiev said:**
> Depends on your hardware and memory.

I boot Xubuntu from a SSD in seconds, takes longer to type in my password than to boot.

Ubuntu Mate boots in about 30 seconds via USB cable to my external HDD on a USB2 port.
We should assume OP is using the same hardware and same memory for the comparison. Otherwise the values won't have any meaning.

---

### Post by deadflowr on 2016-03-23
What's the output for
```
systemd-analyze blame
```
might easier to export it to a file
```
systemd-analyze blame > blame.txt
```
which will be in the top folder of your home folder; not in any folder like Documents, fer what it's worth.

Might also look at that in debian mate, as to compare and contrast.

Also,
How do the boot times compare for actual installs?

---

### Post by X-RED_Tech on 2016-03-23
Results from the above notwithstanding, I guess the explanation is quite mundane: Debian MATE is more frugal, it loads less "things" than Ubuntu MATE at boot.

---

### Post by mikewhatever on 2016-03-23
It should be fairly simple to look at startup  programs, and compare running precesses. Look at the outputs of 'ps aux' and 'dmesg', compare and understand them, disable or uninstall  what seems to be redundant.

---

### Post by no-spam-to-me on 2016-03-23
> **vasa1 said:**
> Where did you get Debian MATE from? Could you post a link to the iso?

Sure I used this torrent: [http://cdimage.debian.org/debian-cd/current-live/amd64/bt-hybrid/debian-live-8.3.0-amd64-mate-desktop.iso.torrent](http://cdimage.debian.org/debian-cd/current-live/amd64/bt-hybrid/debian-live-8.3.0-amd64-mate-desktop.iso.torrent)

> **vasa1 said:**
> We should assume OP is using the same hardware and same memory for the comparison. Otherwise the values won't have any meaning.

That's right.

> **deadflowr said:**
> What's the output for
```
systemd-analyze blame
```


Ubuntu MATE live cd (on sd card via usb card reader):
```

[FONT=-moz-fixed]         17.411s plymouth-quit-wait.service
          4.177s dev-sda1.device
          4.057s gpu-manager.service
          2.170s dev-loop0.device
          1.788s systemd-udev-trigger.service
          1.049s ModemManager.service
           924ms accounts-daemon.service
           760ms systemd-logind.service
           725ms rsyslog.service
           582ms apport.service
           580ms irqbalance.service
           578ms grub-common.service
           571ms lvm2-monitor.service
           563ms systemd-user-sessions.service
           554ms speech-dispatcher.service
           545ms pppd-dns.service
           539ms ondemand.service
           381ms NetworkManager.service
           261ms systemd-modules-load.service
           152ms udisks2.service
           141ms wpa_supplicant.service
           139ms polkitd.service
           128ms systemd-tmpfiles-setup-dev.service
           118ms ubiquity.service
           116ms systemd-setup-dgram-qlen.service
           113ms console-setup.service
           104ms systemd-udevd.service
           102ms systemd-hostnamed.service
           100ms kmod-static-nodes.service
            99ms systemd-journald.service
            98ms systemd-vconsole-setup.service
            96ms bluetooth.service
            87ms systemd-remount-fs.service
            86ms networking.service
            84ms lightdm.service
            82ms dev-hugepages.mount
            79ms avahi-daemon.service
            74ms dev-sdb5.swap
            73ms ufw.service
            68ms plymouth-read-write.service
            67ms dev-mqueue.mount
            66ms apparmor.service
            66ms ntp.service
            50ms kerneloops.service
            48ms user@999.service
            47ms systemd-update-utmp.service
            40ms ifup-wait-all-auto.service
            39ms systemd-backlight@backlight:acpi_video0.service
            36ms systemd-sysctl.service
            34ms systemd-random-seed.service
            33ms debian-fixup.service
            33ms sys-kernel-debug.mount
            33ms systemd-journal-flush.service
            30ms dns-clean.service
            26ms rtkit-daemon.service
            24ms systemd-backlight@backlight:radeon_bl0.service
            24ms resolvconf.service
            23ms upower.service
             9ms ureadahead-stop.service
             8ms tmp.mount
             8ms systemd-update-utmp-runlevel.service
             7ms systemd-tmpfiles-setup.service
             6ms sys-fs-fuse-connections.mount
             5ms rc-local.service
[/FONT]


```

Debian MATE live cd (on sd card via usb card reader):
```

          7.733s live-config.service
          2.396s NetworkManager.service
          2.361s ModemManager.service
          1.322s exim4.service
           866ms lightdm.service
           838ms rpcbind.service
           791ms nfs-common.service
           760ms systemd-logind.service
           726ms rsyslog.service
           659ms pppd-dns.service
           650ms irqbalance.service
           644ms loadcpufreq.service
           644ms speech-dispatcher.service
           637ms rc-local.service
           621ms avahi-daemon.service
           513ms bluetooth.service
           504ms polkitd.service
           457ms systemd-modules-load.service
           320ms dev-hugepages.mount
           318ms dev-mqueue.mount
           315ms sys-kernel-debug.mount
           304ms udisks2.service
           270ms networking.service
           261ms upower.service
           190ms systemd-tmpfiles-setup-dev.service
           148ms hdparm.service
           136ms systemd-journal-flush.service
           136ms cpufrequtils.service
           113ms saned.service
            92ms systemd-tmpfiles-setup.service
            76ms systemd-udev-trigger.service
            75ms systemd-update-utmp.service
            61ms systemd-user-sessions.service
            59ms user@1000.service
            57ms systemd-remount-fs.service
            55ms plymouth-read-write.service
            53ms systemd-setup-dgram-qlen.service
            52ms kmod-static-nodes.service
            51ms systemd-random-seed.service
            31ms systemd-rfkill@rfkill1.service
            30ms systemd-rfkill@rfkill0.service
            29ms systemd-udevd.service
            28ms plymouth-quit.service
            28ms systemd-backlight@backlight:acpi_video0.service
            26ms systemd-rfkill@rfkill3.service
            25ms systemd-rfkill@rfkill2.service
            25ms systemd-sysctl.service
            24ms rtkit-daemon.service
            17ms live-tools.service
            15ms plymouth-quit-wait.service
            14ms keyboard-setup.service
            13ms tmp.mount
            13ms console-setup.service
            12ms systemd-update-utmp-runlevel.service
            12ms udev-finish.service
             3ms sys-fs-fuse-connections.mount

```

Xubuntu currently installed on HDD:
```

[FONT=-moz-fixed]         12.120s dev-sda1.device
         10.486s NetworkManager-wait-online.service
         10.026s apparmor.service
          7.697s systemd-journal-flush.service
          6.619s gpu-manager.service
          4.698s accounts-daemon.service
          4.445s ModemManager.service
          4.001s NetworkManager.service
          3.749s thermald.service
          3.736s grub-common.service
          2.890s irqbalance.service
          2.845s alsa-restore.service
          2.844s pppd-dns.service
          2.617s systemd-udevd.service
          2.354s binfmt-support.service
          2.344s lm-sensors.service
          2.340s apport.service
          2.335s systemd-logind.service
          2.316s ondemand.service
          2.316s systemd-user-sessions.service
          2.315s speech-dispatcher.service
          2.314s rsyslog.service
          2.307s avahi-daemon.service
          2.150s systemd-udev-trigger.service
          1.950s systemd-tmpfiles-setup-dev.service
          1.587s console-setup.service
          1.342s upower.service
          1.272s systemd-modules-load.service
          1.186s systemd-journald.service
          1.002s systemd-setup-dgram-qlen.service
          1.001s sys-kernel-debug.mount
           945ms colord.service
           910ms networking.service
           866ms systemd-tmpfiles-setup.service
           823ms dev-mqueue.mount
           811ms systemd-backlight@backlight:acpi_video0.service
           710ms udisks2.service
           676ms systemd-sysctl.service
           637ms dns-clean.service
           606ms dev-hugepages.mount
           560ms ufw.service
           511ms ifup-wait-all-auto.service
           504ms systemd-backlight@backlight:radeon_bl0.service
           493ms plymouth-read-write.service
           480ms dev-sda5.swap
           460ms systemd-random-seed.service
           444ms systemd-rfkill@rfkill0.service
           396ms kmod-static-nodes.service
           364ms resolvconf.service
           272ms systemd-timesyncd.service
           266ms systemd-tmpfiles-clean.service
           219ms systemd-vconsole-setup.service
           215ms polkitd.service
           209ms systemd-update-utmp.service
           115ms systemd-remount-fs.service
            87ms lightdm.service
            79ms user@1000.service
            69ms wpa_supplicant.service
            45ms kerneloops.service
            13ms hddtemp.service
             9ms plymouth-quit-wait.service
             9ms proc-sys-fs-binfmt_misc.mount
             6ms rtkit-daemon.service
             4ms ureadahead-stop.service
             4ms systemd-update-utmp-runlevel.service
             2ms sys-fs-fuse-connections.mount
             2ms rc-local.service
[/FONT]


```

---

### Post by montag dp on 2016-03-23
I recently installed Debian from a netinstall (minimal) image and then added KDE to that.  I was amazed at how blazingly fast the boot time was.  I'm interested to hear what you find out.  My guess is that Ubuntu and others with a similar target audience install more services than you get with Debian, not that I know what services those might be, though.

---

### Post by no-spam-to-me on 2016-03-23
Here is a comparison of processes loaded by Debian MATE and Ubuntu MATE- identical processes are already deleted.

```

         [TABLE]
[TR]
[TD="align: left"]DEBIAN MATE[/TD]
[TD="align: left"]UBUNTU MATE[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][acpi_thermal_pm][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][charger_manager][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][devfreq_wq][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][ecryptfs-kthrea][/TD]
[/TR]
[TR]
[TD="align: left"][hd-audio0][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][hd-audio1][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][irq/42-mei_me][/TD]
[TD="align: left"][irq/27-mei_me][/TD]
[/TR]
[TR]
[TD="align: left"][jbd2/sda1-8][/TD]
[TD="align: left"][jbd2/sdb1-8][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kfd_process_wq][/TD]
[/TR]
[TR]
[TD="align: left"][khubd][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kloopd0][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][krfcommd][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/0:4][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/0:5][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/0:6][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/0:7][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/0:8][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/1:5][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/1:6][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/u16:6][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/u16:7][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/u17:3][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/u17:4][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/u17:5][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/u17:6][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/u17:7][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/u17:8][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][kworker/u17:9][/TD]
[/TR]
[TR]
[TD="align: left"][loop0][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][md][/TD]
[/TR]
[TR]
[TD="align: left"][nfsiod][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][perf][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][radeon-crtc][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][radeon-crtc][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][radeon-crtc][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][radeon-crtc][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][radeon-crtc][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][radeon-crtc][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][rcuob/0][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][rcuob/1][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][rcuos/0][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][rcuos/1][/TD]
[/TR]
[TR]
[TD="align: left"][rpciod][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"][ttm_swap][/TD]
[/TR]
[TR]
[TD="align: left"][xbrlapi] <defunct>[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/bin/bash[/TD]
[/TR]
[TR]
[TD="align: left"]/sbin/init[/TD]
[TD="align: left"]/sbin/init splash ---[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/sbin/lvmetad -f[/TD]
[/TR]
[TR]
[TD="align: left"]/sbin/rpc.statd[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"]/sbin/rpcbind -w[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/sbin/wpa_supplicant -u -s -O /run/wpa_supplicant[/TD]
[/TR]
[TR]
[TD="align: left"]/usr/bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session[/TD]
[TD="align: left"]/usr/bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session[/TD]
[/TR]
[TR]
[TD="align: left"]/usr/bin/dbus-launch --exit-with-session x-session-manager[/TD]
[TD="align: left"]/usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch mate-session[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/bin/python /usr/bin/blueman-applet[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/bin/python3 /usr/share/system-config-printer/applet.py[/TD]
[/TR]
[TR]
[TD="align: left"]/usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager[/TD]
[TD="align: left"]/usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch mate-session[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/bin/whoopsie -f[/TD]
[/TR]
[TR]
[TD="align: left"]/usr/bin/X :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch[/TD]
[TD="align: left"]/usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/lib/accountsservice/accounts-daemon[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/lib/bluetooth/obexd[/TD]
[/TR]
[TR]
[TD="align: left"]/usr/lib/gvfs/gvfs-goa-volume-monitor[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/lib/gvfs/gvfsd-fuse /run/user/999/gvfs -f -o big_writes[/TD]
[/TR]
[TR]
[TD="align: left"]/usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0[/TD]
[TD="align: left"]/usr/lib/gvfs/gvfsd-trash --spawner :1.11 /org/gtk/gvfs/exec_spaw/1[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/lib/mate-applets/trashapplet[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor[/TD]
[/TR]
[TR]
[TD="align: left"]/usr/sbin/atd -f[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/sbin/avahi-dnsconfd -s[/TD]
[/TR]
[TR]
[TD="align: left"]/usr/sbin/cupsd -f[/TD]
[TD="align: left"]/usr/sbin/cupsd -l[/TD]
[/TR]
[TR]
[TD="align: left"]/usr/sbin/exim4 -bd -q30m[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/sbin/kerneloops[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 108:115[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]/usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 108:115[/TD]
[/TR]
[TR]
[TD="align: left"]/usr/sbin/rpc.idmapd[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"]/usr/sbin/sshd -D[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"]avahi-daemon: running [debian.local][/TD]
[TD="align: left"]avahi-daemon: running [ubuntu-mate.local][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]gnome-pty-helper[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]gnome-pty-helper[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]mate-maximus[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]mate-session[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]mate-terminal[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]syndaemon -i 0.5 -k -R[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]tilda[/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: left"]update-notifier[/TD]
[/TR]
[TR]
[TD="align: left"]x-session-manager[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"]xterm[/TD]
[TD="align: left"][/TD]
[/TR]
[/TABLE]


```

Tomorrow afternoon I will look if Debian MATE loads radeon.ko.

---

### Post by Dorian_Mode on 2016-03-23
Having used xubuntu and ubuntu Mate, my boot times were very compareable to the OP.  I have never used Debian Mate, but a boot time of 20 seconds or less is fast.
Depending on hardware, I do get faster boot times with one laptop that has i5 processor, 6 gib ram and SSD. On that laptop I can boot lubuntu in under 20 seconds.

---

### Post by no-spam-to-me on 2016-03-24
So- radeon.ko is loaded in debian. Why there are six radeon-crtc processes running in ubuntu (my local Xubuntu installation also has six of them) and debian spawns none?

---

### Post by no-spam-to-me on 2016-03-30
Now I installed Debian Mate on my HDD:
> Startup finished in 3.742s (kernel) + 28.568s (userspace) = 32.311s

That is with firmware for my radeon and network card.

---

### Post by no-spam-to-me on 2016-06-14
Hi!

It seems that this was triggered by the free radeon drivers. With kernel 4.7 rc2 something was obviously changed -> boot times are fast again.

---

