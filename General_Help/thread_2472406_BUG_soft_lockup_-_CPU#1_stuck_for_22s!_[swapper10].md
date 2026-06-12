---
title: "BUG: soft lockup - CPU#1 stuck for 22s! [swapper/1:0] on mini PC N4020"
date: 2022-02-25
forum: General Help
---

### Post by mikeubell on 2022-02-25
I have installed Ubuntu 20.04 on a Coofun N40:
&#8206;2.8 GHz celeron_n4020&#8206;4 GB ddr3l
&#8206;64 GB
&#8206;Intel HD Graphics 400

I installed from a SD card in a USB reader.  All went well and I booted into the installed system.  Installed Zoneminder and it worked well.  I then powercycled the box and during boot I repeatedly got messages similar to:

BUG: soft lockup - CPU#1 stuck for 22s! [swapper/1:0] 

I then booted again from the USB card and when it came up skipped the install and exited removing the card.  The system booted to the installed system with no problems.  Powercycling causes the same symptoms.
I have reviewed various other similar reports and have tried modifying the boot parameters  with pci=noacpi and acpi=off.  I did not see anything else that might be useful.

---

### Post by Bashing-om on 2022-02-25
mikeubell - Hello; Welcome to the Forum

Hummmm ...
> 
 [swapper/1:0]


In respect to "swap" abilities ?

Might be instructive to see what is provided:
post back - between code tags - the outputs of terminal commands:
```

sudo blkid
cat /etc/fstab

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

this is one thought
[INDENT][INDENT]could be others
[/INDENT][/INDENT]

---

### Post by mikeubell on 2022-02-26
Here is the output.  I did not do any special configuration of the swap area.  When the system is up and running there are no problems.
```

[COLOR=#2FB41D][FONT=Menlo]**ubell@mini-pc**[COLOR=#000000]:[/COLOR][COLOR=#400BD9]**~**[/COLOR][COLOR=#000000]$ sudo blkid[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][sudo] password for ubell:
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]/dev/mmcblk0p2: UUID="d0309aa8-c61f-44ad-870a-273a43578bd9" TYPE="ext4" PARTUUID="874c1365-f9da-4d85-85b4-63f0c625f940"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop0: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop1: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop2: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop3: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop4: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop5: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop6: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop7: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/mmcblk0p1: UUID="948C-B4AC" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="134a6442-4092-4978-a763-0c6c5b0d46fa"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop8: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop9: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop10: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop11: TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#2FB41D]**ubell@mini-pc**[/COLOR]:[COLOR=#400BD9]**~**[/COLOR]$ cat /etc/fstab[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# /etc/fstab: static file system information.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# Use 'blkid' to print the universally unique identifier for a[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# device; this may be used with UUID= as a more robust way to name devices[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# that works even if disks are added and removed. See fstab(5).[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# / was on /dev/mmcblk0p2 during installation[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]UUID=d0309aa8-c61f-44ad-870a-273a43578bd9 /               ext4    errors=remount-ro 0       1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# /boot/efi was on /dev/mmcblk0p1 during installation[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]UUID=948C-B4AC  /boot/efi       vfat    umask=0077      0       1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/swapfile [/FONT][/COLOR][COLOR=#000000][FONT=Menlo]none[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]swap[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]sw[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]0 [/FONT][/COLOR][COLOR=#000000][FONT=Menlo]0[/FONT][/COLOR]
```

---

### Post by Bashing-om on 2022-02-26
mikeubell; Humm ..

I honestly do not know what to make of the flag in your fstab entry -  are the loss of space separations a result of translitterations ?
I think the separations of the flags are needed !
My swapfile:
> 
/swapfile                                 none            swap    sw              0       0


suggest that you insure the integrity of your file.

-only a best maybe-

---

### Post by mikeubell on 2022-02-27
Looks like pasting into <code> got rid of the tabs.

[COLOR=#000000][FONT=Menlo]# /etc/fstab: static file system information.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# Use 'blkid' to print the universally unique identifier for a[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# device; this may be used with UUID= as a more robust way to name devices[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# that works even if disks are added and removed. See fstab(5).[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# / was on /dev/mmcblk0p2 during installation[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]UUID=d0309aa8-c61f-44ad-870a-273a43578bd9 /               ext4    errors=remount-ro 0       1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# /boot/efi was on /dev/mmcblk0p1 during installation[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]UUID=948C-B4AC  /boot/efi       vfat    umask=0077      0       1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/swapfile                                 none            swap    sw              0       0[/FONT][/COLOR]

---

### Post by mikeubell on 2022-02-27
I doubt this is a configuration issue as I have not modified the configuration.  I suspect it is related to some hardware startup issues which are handled by the install boot but not by the production.  Possibly timing?

---

### Post by Bashing-om on 2022-02-27
mikeubell; Well -

We can take a look at the boot log and see if the kernel reports any issues:
```

journalctl -p 4 -xb

```

-the journal might tell the tale-

---

### Post by mikeubell on 2022-02-28
Here are the first 70 lines:

[COLOR=#000000][FONT=Menlo]-- Logs begin at Wed 2022-02-23 10:08:44 PST, end at Mon 2022-02-28 09:33:51 PST. --[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Feb 24 17:28:55 mini-pc kernel: [COLOR=#B42419]**x86/cpu: SGX disabled by BIOS.**[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:55 mini-pc kernel: [/COLOR]**Expanded resource Reserved due to conflict with PCI Bus 0000:00**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:55 mini-pc kernel: [/COLOR]**platform eisa.0: EISA: Cannot allocate resource for mainboard**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:55 mini-pc kernel: [/COLOR]**platform eisa.0: Cannot allocate resource for EISA slot 1**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:55 mini-pc kernel: [/COLOR]**platform eisa.0: Cannot allocate resource for EISA slot 2**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:55 mini-pc kernel: [/COLOR]**platform eisa.0: Cannot allocate resource for EISA slot 3**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:55 mini-pc kernel: [/COLOR]**platform eisa.0: Cannot allocate resource for EISA slot 4**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:55 mini-pc kernel: [/COLOR]**platform eisa.0: Cannot allocate resource for EISA slot 5**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:55 mini-pc kernel: [/COLOR]**platform eisa.0: Cannot allocate resource for EISA slot 6**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:55 mini-pc kernel: [/COLOR]**platform eisa.0: Cannot allocate resource for EISA slot 7**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:55 mini-pc kernel: [/COLOR]**platform eisa.0: Cannot allocate resource for EISA slot 8**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:55 mini-pc kernel: [/COLOR]**usb: port power management may be unreliable**[/FONT][/COLOR]
[COLOR=#B42419][FONT=Menlo][COLOR=#000000]Feb 24 17:28:56 mini-pc kernel: [/COLOR]**Bluetooth: hci0: unexpected event for opcode 0xfc2f**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:56 mini-pc kernel: [/COLOR]**thermal thermal_zone1: failed to read out thermal zone (-61)**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:57 mini-pc kernel: [/COLOR]**sof-audio-pci-intel-apl 0000:00:0e.0: ASoC: Parent card not yet available, widget card binding deferred**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:58 mini-pc systemd-udevd[308]: [/COLOR]**controlC0: Process '/usr/sbin/alsactl -E HOME=/run/alsa -E XDG_RUNTIME_DIR=/run/alsa/runtime restore 0' failed with exit code**[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:58 mini-pc thermald[584]: [/COLOR]**sensor id 6 : No temp sysfs for reading raw temp**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:58 mini-pc thermald[584]: [/COLOR]**sensor id 6 : No temp sysfs for reading raw temp**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:58 mini-pc thermald[584]: [/COLOR]**sensor id 6 : No temp sysfs for reading raw temp**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:58 mini-pc thermald[584]: [/COLOR]**error: could not parse file /etc/thermald/thermal-conf.xml**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:58 mini-pc thermald[584]: [/COLOR]**error: could not parse file /etc/thermald/thermal-conf.xml**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:58 mini-pc thermald[584]: [/COLOR]**error: could not parse file /etc/thermald/thermal-conf.xml**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:58 mini-pc udisksd[595]: [/COLOR]**failed to load module mdraid: libbd_mdraid.so.2: cannot open shared object file: No such file or directory**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:58 mini-pc udisksd[595]: [/COLOR]**Failed to load the 'mdraid' libblockdev plugin**[/FONT][/COLOR]
[COLOR=#B42419][FONT=Menlo][COLOR=#000000]Feb 24 17:28:58 mini-pc bluetoothd[543]: [/COLOR]**Failed to set mode: Blocked through rfkill (0x12)**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:58 mini-pc NetworkManager[549]: [/COLOR]**<warn>  [1645752538.9562] ifupdown: interfaces file /etc/network/interfaces doesn't exist**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc colord[665]: [/COLOR]**failed to get session [pid 545]: No data available**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc kernel: [/COLOR]**kauditd_printk_skb: 26 callbacks suppressed**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc NetworkManager[549]: [/COLOR]**<warn>  [1645752539.3972] Error: failed to open /run/network/ifstate**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc NetworkManager[549]: [/COLOR]**<warn>  [1645752539.5437] sup-iface: failed to cancel p2p connect: P2P cancel failed**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc tracker-miner-f[909]: [/COLOR]**Unable to get XDG user directory path for special directory &DOCUMENTS. Ignoring this location.**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc tracker-miner-f[909]: [/COLOR]**Unable to get XDG user directory path for special directory &MUSIC. Ignoring this location.**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc tracker-miner-f[909]: [/COLOR]**Unable to get XDG user directory path for special directory &PICTURES. Ignoring this location.**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc tracker-miner-f[909]: [/COLOR]**Unable to get XDG user directory path for special directory &VIDEOS. Ignoring this location.**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc tracker-miner-f[909]: [/COLOR]**Unable to get XDG user directory path for special directory &DOWNLOAD. Ignoring this location.**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc tracker-miner-f[909]: [/COLOR]**Unable to get XDG user directory path for special directory &DOCUMENTS. Ignoring this location.**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc tracker-miner-f[909]: [/COLOR]**Unable to get XDG user directory path for special directory &MUSIC. Ignoring this location.**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc tracker-miner-f[909]: [/COLOR]**Unable to get XDG user directory path for special directory &PICTURES. Ignoring this location.**[/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc tracker-miner-f[909]: [/COLOR]**Unable to get XDG user directory path for special directory &VIDEOS. Ignoring this location.**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Feb 24 17:28:59 mini-pc pulseaudio[890]: [COLOR=#B42419]**Failed to find a working profile.**[/COLOR][/FONT][/COLOR]
[COLOR=#B42419][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc pulseaudio[890]: [/COLOR]**Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_0e.0-platform-skl_hda_dsp_generic" card_nam**[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activating service name='org.freedesktop.systemd1' requested **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activated service 'org.freedesktop.systemd1' failed: Process **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activating service name='org.freedesktop.systemd1' requested **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activated service 'org.freedesktop.systemd1' failed: Process **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc gnome-session-binary[936]: [/COLOR]**WARNING: Falling back to non-systemd startup procedure due to error: GDBus.Error:org.freedesktop.DBus.Error.Spawn.Chil**[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activating service name='org.freedesktop.systemd1' requested **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activated service 'org.freedesktop.systemd1' failed: Process **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activating service name='org.freedesktop.systemd1' requested **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activated service 'org.freedesktop.systemd1' failed: Process **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activating service name='org.freedesktop.systemd1' requested **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activated service 'org.freedesktop.systemd1' failed: Process **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activating service name='org.freedesktop.systemd1' requested **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activated service 'org.freedesktop.systemd1' failed: Process **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Feb 24 17:28:59 mini-pc pulseaudio[890]: [COLOR=#B42419]**Failed to find a working profile.**[/COLOR][/FONT][/COLOR]
[COLOR=#B42419][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc pulseaudio[890]: [/COLOR]**Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_0e.0-platform-skl_hda_dsp_generic" card_nam**[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activating service name='org.freedesktop.systemd1' requested **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc /usr/lib/gdm3/gdm-wayland-session[933]: [/COLOR]**dbus-daemon[933]: [session uid=125 pid=933] Activated service 'org.freedesktop.systemd1' failed: Process **[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Feb 24 17:28:59 mini-pc pulseaudio[890]: [COLOR=#B42419]**Failed to find a working profile.**[/COLOR][/FONT][/COLOR]
[COLOR=#B42419][FONT=Menlo][COLOR=#000000]Feb 24 17:28:59 mini-pc pulseaudio[890]: [/COLOR]**Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_0e.0-platform-skl_hda_dsp_generic" card_nam**[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Feb 24 17:29:00 mini-pc pulseaudio[890]: [COLOR=#B42419]**Failed to find a working profile.**[/COLOR][/FONT][/COLOR]
[COLOR=#B42419][FONT=Menlo][COLOR=#000000]Feb 24 17:29:00 mini-pc pulseaudio[890]: [/COLOR]**Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_0e.0-platform-skl_hda_dsp_generic" card_nam**[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Feb 24 17:29:00 mini-pc pulseaudio[890]: [COLOR=#B42419]**Failed to find a working profile.**[/COLOR][/FONT][/COLOR]
[COLOR=#B42419][FONT=Menlo][COLOR=#000000]Feb 24 17:29:00 mini-pc pulseaudio[890]: [/COLOR]**Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_0e.0-platform-skl_hda_dsp_generic" card_nam**[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Feb 24 17:29:00 mini-pc pulseaudio[890]: [COLOR=#B42419]**Failed to find a working profile.**[/COLOR][/FONT][/COLOR]
[COLOR=#B42419][FONT=Menlo][COLOR=#000000]Feb 24 17:29:00 mini-pc pulseaudio[890]: [/COLOR]**Failed to load module "module-alsa-card" (argument: "device_id="0" name="pci-0000_00_0e.0-platform-skl_hda_dsp_generic" card_nam**[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#D9DC55][FONT=Menlo][COLOR=#000000]Feb 24 17:29:00 mini-pc pulseaudio[890]: [/COLOR]**Tried to configure /devices/pci0000:00/0000:00:0e.0/skl_hda_dsp_generic/sound/card0 (alsa_card.pci-0000_00_0e.0-platform-skl_hda**[COLOR=#FFFFFF]>[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Feb 24 17:29:00 mini-pc /etc/mysql/debian-start[1053]: [COLOR=#D9DC55]**Looking for 'mysql' as: /usr/bin/mysql**[/COLOR][/FONT][/COLOR]

---

### Post by Bashing-om on 2022-03-01
mikeubell; :(

After due consideration -

these issues as shown in the log output are not in my skill set to address. I had hoped that others would come to our aid.

sorry but
[INDENT][INDENT]a know-it-all
[INDENT][INDENT]I am not[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by him610 on 2022-03-04
> Looks like pasting into <code> got rid of the tabs.
You may be able to configure your editor to convert tabs to spaces.

---

