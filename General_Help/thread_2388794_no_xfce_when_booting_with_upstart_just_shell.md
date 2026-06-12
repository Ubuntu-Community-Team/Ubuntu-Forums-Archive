---
title: "no xfce when booting with upstart just shell"
date: 2018-04-07
forum: General Help
---

### Post by williman9999 on 2018-04-07
Hy,
I have Ubuntu 16.04.4 LTS and a encrypted home folder, encrypted swap and 3 encrypted drives (all luks, system partition is unencrypted). 1 of the luks drives is iscsi.

I had it all set up that it was working and on bootup and wake after hibernate it only asks the luks password once (same password for all encrypted entities).

This works with booting kernel (generic) (at this time: "Ubuntu, mit Linux 4.4.0-119-generic") but not wieth upstart.

It used to also work when automatically booting the upstart version (now "Ubuntu, with Linux 4.4.0-119-generic (upstart)")

I suppose I had an ssd crash and some systemd files went corrupt. I cloned the ssd to a new one, and since then only the "generic" version boots into xfce. The upstart version only boots into a shell and 
asks for the luks password consecutively as often as i have encrypted entities. the iscsi drive with both boot configs is only mounted after login as it somehow is not able to reach it over the network before login (generic and upstart boot).

I tried a packet check, reinstall of packets, but it didnt help.

I am unable to find an error message to trace the source of the problem.

If you wonder wether my luks setup might be culprit, i followed this:
[https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap)

I already tried 
```
[COLOR=#333333][FONT=UbuntuMono]sudo update-initramfs -u -k all[/FONT][/COLOR]
```[COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono](which it anyway always does when updating the kernel)

My grub parameter are

current upstart version:
```


```[/FONT][/COLOR]```
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  29..<remark: uuid of / according to fstab>
    else
      search --no-floppy --fs-uuid --set=root 29..<remark: uuid of / according to fstab>
    fi
    echo    'Linux 4.4.0-119-generic wird geladen &#8230;'
        linux    /boot/vmlinuz-4.4.0-119-generic root=UUID=29..<remark: uuid of / according to fstab> ro  splash quiet pci=nomsi resume=/dev/mapper/cryptswap1 $vt_handoff init=/sbin/upstart
    echo    'Initiale Ramdisk wird geladen &#8230;'
    initrd    /boot/initrd.img-4.4.0-119-generic



```[COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR]"generic" conf is:

```

    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  29..<remark: UUID of />
    else
      search --no-floppy --fs-uuid --set=root 29<remark: />
    fi
    echo    'Linux 4.4.0-119-generic wird geladen &#8230;'
        linux    /boot/vmlinuz-4.4.0-119-generic root=UUID=29..<remark: /> ro  splash quiet pci=nomsi resume=/dev/mapper/cryptswap1 $vt_handoff
    echo    'Initiale Ramdisk wird geladen &#8230;'
    initrd    /boot/initrd.img-4.4.0-119-generic




```

in dmesg (version after "upstart" boot) i found the following odd entries:

```

[FONT=monospace][COLOR=#000000][    0.153448] pci 0000:00:1f.0: can't claim BAR 13 [io  0x0800-0x087f]: address conflict with ACPI CPU throttle [io  0x0810-0x0815][/COLOR]
[/FONT][FONT=monospace][COLOR=#000000][   60.211755] upstart: Error while reading from descriptor: Broken pipe[/COLOR]
[   60.217066] upstart: failsafe main process (1676) killed by TERM signal
[/FONT][FONT=monospace][COLOR=#000000][   60.539530] upstart: cups main process (1784) killed by HUP signal[/COLOR]
[   60.539548] upstart: cups main process ended, respawning
[/FONT][FONT=monospace][COLOR=#000000][   60.647635] upstart: samba-ad-dc main process (1767) terminated with status 1[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000][   80.540962] systemd-logind[3571]: Failed to enable subscription: Launch helper exited with unknown return code 1[/COLOR]
[   80.541030] systemd-logind[3571]: Failed to fully start up daemon: Input/output error
[   86.583449] systemd-logind[3687]: Failed to enable subscription: Launch helper exited with unknown return code 1
[   86.583517] systemd-logind[3687]: Failed to fully start up daemon: Input/output error
[   90.607000] audit_printk_skb: 144 callbacks suppressed

[/FONT]
```

and syslog 

```

[FONT=monospace][COLOR=#000000]Apr  7 12:42:05 fry-pc rsyslogd-2039: Could not open output pipe '/dev/xconsole':: No such file or directory [v8.16.0 try http://www.rsyslog.com/e/2039 ][/COLOR]
[/FONT]pr  7 12:42:25 fry-pc dbus[1732]: [system] Activating service name='org.freedesktop.login1' (using servicehelper)
Apr  7 12:42:25 fry-pc dbus[1732]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Apr  7 12:42:25 fry-pc dbus[1732]: [system] Activated service 'org.freedesktop.systemd1' failed: Launch helper exited with unknown return code 1
Apr  7 12:42:25 fry-pc dbus[1732]: [system] Activated service 'org.freedesktop.login1' failed: Launch helper exited with unknown return code 1
Apr  7 12:42:25 fry-pc dbus[1732]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Apr  7 12:42:25 fry-pc dbus[1732]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
[FONT=monospace][COLOR=#000000]Apr  7 12:42:31 fry-pc dbus[1732]: [system] Activated service 'org.freedesktop.systemd1' failed: Launch helper exited with unknown return code 1[/COLOR]
Apr  7 12:42:31 fry-pc dbus[1732]: [system] Activated service 'org.freedesktop.login1' failed: Launch helper exited with unknown return code 1
[/FONT][FONT=monospace][COLOR=#000000]Apr  7 12:42:36 fry-pc dbus[1732]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)[/COLOR]
Apr  7 12:42:36 fry-pc dbus[1732]: [system] Successfully activated service 'org.freedesktop.ColorManager'
[/FONT]

```

I checked dmesg after a "generic" boot wether the same output is there:
-"cant claim" isnt there
-descriptor isnt there
-failsafe isnt there
-killed messages arent there
-samba message isnt there
-no  failed systemd messages 

and syslog generic:
-could not open output pipe is there
-launch helper exit messages are not there

What could I try to fix upstart- boot?
thx!

p.s.:
with the non-upstart boot after entering the luks password the system waits 1,5minutes before booting on for "dev-mapper-backup\x2dcrypt.device" which is the iscsi luks drive. i suppose at this stage of boot it simply cant mount iscsi yet because there is no network. the message is alternating and alos shows: "A start job is running for dev-disk-by\x2duuid-0....\x2d...\x2d...\s2d.....\x2...device"

---

### Post by oldos2er on 2018-04-07
Thread moved to *General Help*.

---

