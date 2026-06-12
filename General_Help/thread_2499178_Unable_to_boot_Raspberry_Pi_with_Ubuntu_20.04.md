---
title: "Unable to boot Raspberry Pi with Ubuntu 20.04"
date: 2024-07-17
forum: General Help
---

### Post by flamethrow3r on 2024-07-17
[SIZE=3][COLOR=#555555][FONT=Roboto]Hello. A while ago, I successfully installed Ubuntu MATE 20.04 on my Raspberry Pi and used it for ROS for a while. Then, I decided to upgrade to MATE 22.04 by flashing it into the card and, after some issues with compatibility, I decided to go back to 20.04. however, I just can't get it to boot correctly! I've tried many different Raspberry Pi eeprom versions; the ones from 2024 and 2020 just give me a black screen, with the light blinking four times slower then four times faster. Other eeprom versions, like from 2023 or 2022, give me a "this board requires newer software" screen, which says that start4x.elf and fixup4x.dat are incompatible. I've tried to replace just those files with the ones from the Raspberry Pi firmware repo on GitHub, to no avail. 
Replacing just the .elf files ends up with "---[ end Kernel panic - not syncing: Can not allocate SWIOTLB buffer earlier and can't now provide you with the DMA bounce buffer ]---"
Replacing just the .dat files actually gives me the aforementioned LED blinking pattern, with the screen also black.
Replacing all of the start*.elf and fixup*.dat files actually leads to the board booting, but then the Ubuntu installer crashes, apparently while configuring the keyboard. Ubuntu Server 20.04 doesn't work, either. I'm using the same SD card, the same power supply and the same board as when it was working. I even tried with a brand new board, but nothing.
I've tried both the Raspberry Pi imager and Balena Etcher to flash Ubuntu 20.04 into the card, but none work. Also, it has worked with other OSs, as I've used Raspberry Pi OS to upgrade and downgrade the eeprom. Here is an image of the aforementioned screen:
[/FONT][/COLOR][/SIZE][IMG]https://i.sstatic.net/gYYUtJVI.jpg[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293984&stc=1[/IMG]

UPDATE: I accessed var/log/installer/dm.txt, this is it:
```

ubiquity-dm: starting
ubiquity-dm: plymouth
ubiquity-dm: start X ['X', '-br', '-ac', '-noreset', '-nolisten', 'tcp', '-background', 'none', 'vt1', ':0']


X.Org X Server 1.20.8
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.15.0-109-generic aarch64 Ubuntu
Current Operating System: Linux ubuntu 5.4.0-1022-raspi #25-Ubuntu SMP PREEMPT Thu Oct 15 13:31:49 UTC 2020 aarch64
Kernel command line:  coherent_pool=1M 8250.nr_uarts=0 snd_bcm2835.enable_compat_alsa=0 snd_bcm2835.enable_hdmi=1 snd_bcm2835.enable_headphones=1 video=HDMI-A-1:1680x1050M@60 smsc95xx.macaddr=2C:CF:67:2A:CD:DD vc_mem.mem_base=0x3ec00000 vc_mem.mem_size=0x40000000  net.ifnames=0 dwc_otg.lpm_enable=0 console=tty1 root=LABEL=writable rootfstype=ext4 elevator=deadline rootwait fixrtc quiet splash quiet splash
Build Date: 04 September 2020  01:34:27PM
xorg-server 2:1.20.8-2ubuntu2.4 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.38.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr  1 18:24:14 2020
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) modeset(0): Initializing kms color map for depth 24, 8 bpc.
ubiquity-dm: set vars
ubiquity-dm: pam_open_session
ubiquity-dm: oem dm-scripts
/usr/bin/prime-supported: 38: cannot create /var/log/prime-supported.log: Permission denied
/sbin/prime-offload: 29: cannot create /var/log/prime-offload.log: Permission denied
ubiquity-dm: start frontend gtk_ui
ubiquity-dm: start greeter


** (mate-settings-daemon:1059): WARNING **: 18:24:21.660: There was a problem when setting QT_AUTO_SCREEN_SCALE_FACTOR=0: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


** (mate-settings-daemon:1059): WARNING **: 18:24:21.665: There was a problem when setting QT_SCALE_FACTOR=1: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


(nm-applet:1061): Gtk-WARNING **: 18:24:21.864: Can't set a parent on widget which has a parent


(nm-applet:1061): libnotify-WARNING **: 18:24:24.590: Failed to connect to proxy


(nm-applet:1061): nm-applet-WARNING **: 18:24:24.652: Failed to show notification: Error calling StartServiceByName for org.freedesktop.Notifications: Process org.freedesktop.Notifications exited with status 1


(nm-applet:1061): Gtk-CRITICAL **: 18:24:25.509: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 18:24:25.509: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 18:24:25.679: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 18:24:25.790: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 18:24:25.790: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 18:24:25.925: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 18:24:59.053: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 18:24:59.053: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 18:24:59.190: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 18:24:59.300: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 18:24:59.300: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 18:24:59.421: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 18:25:19.428: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 18:25:19.428: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 18:25:19.563: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 18:25:19.692: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 18:25:19.692: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 18:25:19.825: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 18:25:21.933: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 18:25:21.933: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 18:25:22.076: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 18:25:22.192: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 18:25:22.192: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 18:25:22.306: Can't set a parent on widget which has a parent
Fontconfig warning: Directory/file mtime in the future. New fonts may not be detected.


(nm-applet:1061): Gtk-CRITICAL **: 18:25:24.413: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 18:25:24.413: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 18:25:24.527: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 18:25:27.087: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 18:25:27.087: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 18:25:27.208: Can't set a parent on widget which has a parent


(nm-applet:1061): nm-applet-WARNING **: 18:25:27.251: Failed to show notification: Error calling StartServiceByName for org.freedesktop.Notifications: Process org.freedesktop.Notifications exited with status 1


(nm-applet:1061): Gtk-CRITICAL **: 18:25:27.345: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 18:25:27.345: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 18:25:27.465: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 12:19:10.763: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 12:19:10.763: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 12:19:10.886: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 12:19:10.987: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 12:19:10.987: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 12:19:10.997: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 12:21:59.074: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 12:21:59.074: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 12:21:59.083: Can't set a parent on widget which has a parent


(nm-applet:1061): Gtk-CRITICAL **: 12:22:00.750: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-CRITICAL **: 12:22:00.750: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed


(nm-applet:1061): Gtk-WARNING **: 12:22:00.758: Can't set a parent on widget which has a parent

```

[SIZE=3][COLOR=#555555][FONT=Roboto]The image I'm trying to flash can be found here: [https://releases.ubuntu-mate.org/20.04/arm64/](https://releases.ubuntu-mate.org/20.04/arm64/)[/FONT][/COLOR][/SIZE][SIZE=3][COLOR=#555555][FONT=Roboto]
[/FONT][/COLOR][/SIZE][IMG]https://imgur.com/a/tBN11Fm[/IMG][IMG]https://imgur.com/a/tBN11Fm[/IMG]
[IMG]https://imgur.com/a/tBN11Fm[/IMG]

---

### Post by genesis170 on 2024-07-18
Hey flamethrow3r,


Welcome back to Ubuntu! Sounds like you've been through the wringer trying to get 20.04 working again. The blinking light pattern suggests an issue with the firmware/bootloader compatibility. Have you tried flashing a fresh 20.04 image using the Raspberry Pi Imager tool? It might be worth a shot to ensure a clean install.


While you're troubleshooting, why not explore some potential online job opportunities? Learning new skills can be a great way to earn extra income and boost your resume. Check out resources like online job boards or freelancing platforms to discover [how to get an online job]("https://freelancesage.com/") that suits your interests and expertise.

---

### Post by flamethrow3r on 2024-07-18
Yes; I've used Raspberry Pi OS to do eeprom upgrades and downgrades (to see if any version worked) so I've had to flash Ubuntu 20.04 multiple times. I've even downloaded different 20.04 image files, to see if the original was corrupted.

---

### Post by flamethrow3r on 2024-07-18
Was the picture attached correctly, by the way? I'm new here so I didn't really know how to do it.
EDIT: Okay I figured it out, it's attached now.

---

### Post by currentshaft on 2024-07-18
4 long flashes followed by 4 short ones indicates "Unsupported board type"

Are you sure you performed the rpi-imager update? The screenshots shows you using firmware from years ago.

---

### Post by flamethrow3r on 2024-07-18
Isn't the firmware part of the Ubuntu image? I have the latest version of the imager, but I think Ubuntu 20.04 is supposed to come with firmware from 2020...

---

### Post by flamethrow3r on 2024-07-20
I've tried everything I've seen on the internet, but nothing seems to work. It seems Ubuntu is specialin that replacing the .elf and .dat files doesn't resolve the issue. I've managed to get some other interesting information, though (and updated the post with it), but no new leads.

---

### Post by him610 on 2024-07-21
Look at the sixth line from the bottom in the #1 attachment; it tells you what to do.

---

### Post by flamethrow3r on 2024-07-22
It's a book. You mean the sixth to last chapter?

---

### Post by currentshaft on 2024-07-22
> **flamethrow3r said:**
> Isn't the firmware part of the Ubuntu image? I have the latest version of the imager, but I think Ubuntu 20.04 is supposed to come with firmware from 2020...

No. You need to install it with rpi-imager as the official documentation says.

---

### Post by flamethrow3r on 2024-07-22
But I've used the Raspberry Pi imager to flash the card, so that should also flash the firmware, right?

---

### Post by flamethrow3r on 2024-07-22
(Sorry, I didn't see my previous reply and thought it had been deleted; I didn't know there were different pages. This is a duplicate)

---

### Post by him610 on 2024-07-22
> **flamethrow3r said:**
> It's a book. You mean the sixth to last chapter?
No, look at the screenshot posted in #1, here is what those lines read...
```
start4x.elf: is **not compatible**
This **board requires newer software**
Get the **latest software from https://www.raspberrypi.com/software/**

```
It says your board is incompatible with the software you are trying to load, your board needs newer software, and to get it you need to download one of the recommended Raspberry Pi OS releases.

I have used the OS on my Pi-1, my Pi-3B, and a netbook (x86) for years. It is a good OS; it's made for the Raspberry PI family of SBCs.

---

### Post by flamethrow3r on 2024-07-23
But I need Ubuntu 20.04 to be able to use ROS Humble for my project, Raspberry Pi OS is no good in this case. What confuses me is how it worked before and not anymore...

---

### Post by him610 on 2024-07-23
>  I need Ubuntu 20.04 to be able to use ROS Humble
maybe this will help, *Install ROS2 Humble on Raspberry Pi 4*
[https://roboticsbackend.com/install-ros2-on-raspberry-pi/]("https://roboticsbackend.com/install-ros2-on-raspberry-pi/")

---

### Post by flamethrow3r on 2024-07-24
But that page uses 22.04. That version isn't giving me boot problems, but due to compatibility issues with some programs, I must use 20.04.

---

### Post by ActionParsnip on 2024-07-24
Use Raspberry Pi OS on the SDCard. Use the EEPROM updater to update the board, then re-transfer Ubuntu to the SDCard and boot up. You will now be on the latest firmware in the Pi

---

### Post by flamethrow3r on 2024-07-24
I already tried that along with other older versions of the eeprom, but no luck.

---

### Post by flamethrow3r on 2024-07-26
I'm just guessing here, but given that replacing the .elf and .dat files got Ubuntu 20.04 to at least boot, maybe the subsequent installer crash is due to another reason. Does anyone know why this could be happening?

---

### Post by flamethrow3r on 2024-07-31
I just bought a new Raspberry Pi 4B and tried Ubuntu 20.04 in it. It gave me the exact same error, so it seems it's easily reproducible. I've also found new information and updated the original post with it.

---

### Post by flamethrow3r on 2024-08-01
I've just tried a few different things, including using older start*.elf and fixup*.dat files, making other combinations of new kernel and other boot partition files and booting Ubuntu by installing it into the disk (SD card) from the Raspberry Pi OS desktop. However, nothing seems to work. Is anyone able to reproduce the issue or suggest some solutions?

---

### Post by currentshaft on 2024-08-01
4b

---

### Post by flamethrow3r on 2024-08-02
Yes; Ubuntu 22.04 doesn't cause any boot issues, but I need 20.04 for my project. I've left a link to the image in the original post.

---

### Post by flamethrow3r on 2024-08-02
So I managed to get Ubuntu MATE by installing Ubuntu Server 20.04 through the image built into the Raspberry Pi imager and then installing the desktop in there (through "sudo apt install ubuntu-mate-desktop"). However, I think it didn't turn out quite right: the password thing is on the left, with the MATE background behind it, although it does work. When you enter the password, the background turns into a blue screen and everything is extremely laggy. Even though I had connected to a Wi-Fi network to install the desktop, it doesn't find any networks anymore (opening the tab with the Wi-Fi symbol on top shows "device not ready" instead of the network options). It also installed GNOME as well, for some reason.
I did a reboot and the blue screen thing doesn't happen anymore. Still no network, though.
Edit: even though the network symbol appears as if I had no Wi-Fi, I seem to be able to use the internet with no problem.

---

### Post by flamethrow3r on 2024-08-03
I haven't had any more issues, so it seems the solution is to install Ubuntu Server 20.04 through the Raspberry Pi imager (not from the official downloads) and then install the MATE desktop there. I'm therefore marking this as solved.
It seems to be an issue with the official images, so they might need an update, or a fix. I'm not sure what exactly caused the issue, but I'll look into it if I have time in the future.

---

