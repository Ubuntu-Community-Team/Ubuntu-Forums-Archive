---
title: "[SOLVED] HELP! Major problems after update this morning"
date: 2008-06-05
forum: General Help
---

### Post by nowhere@cox.net on 2008-06-05
Hey all,

There were a few updates to stuff this morning (I have backports enabled). 25 of them to be precise. I remember evolution updates and some stuff with gnome. 

After the update, hal cannot start any more, even after rebooting. I have several errors in various logs. Here are a few:
[B]
daemon.log[/B]
```
Jun  5 09:55:29 Legolas hcid[6080]: Can't connect to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
```
```
Jun  5 09:56:40 Legolas hcid[5705]: Unable to get on D-Bus
Jun  5 09:56:41 Legolas gdm[5763]: WARNING: Didn't understand `' (expected true or false) 
```

**sys.log**
```
Jun  5 09:57:16 Legolas ck-launch-session: error connecting to ConsoleKit
Jun  5 09:57:18 Legolas pulseaudio[6254]: module-hal-detect.c: Unable to contact DBUS system bus: org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
Jun  5 09:57:18 Legolas pulseaudio[6254]: module.c: Failed to load  module "module-hal-detect" (argument: ""): initialization failed.
Jun  5 09:57:18 Legolas pulseaudio[6254]: main.c: Module load failed.
Jun  5 09:57:18 Legolas pulseaudio[6254]: main.c: Failed to initialize daemon.
```

**messages**
```
Jun  5 09:56:34 Legolas kernel: [   19.833159] Early unpacking initramfs... done
Jun  5 09:56:34 Legolas kernel: [   20.121629] ACPI: Core revision 20070126
Jun  5 09:56:34 Legolas kernel: [   20.121692] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
```
```
Jun  5 09:56:34 Legolas kernel: [   20.467498] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467500] system 00:00: iomem range 0xc0000-0xc3fff has been reserved
Jun  5 09:56:34 Legolas kernel: [   20.467503] system 00:00: iomem range 0xc4000-0xc7fff has been reserved
Jun  5 09:56:34 Legolas kernel: [   20.467505] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
Jun  5 09:56:34 Legolas kernel: [   20.467507] system 00:00: iomem range 0xcc000-0xcffff has been reserved
Jun  5 09:56:34 Legolas kernel: [   20.467509] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467512] system 00:00: iomem range 0x0-0x0 could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467514] system 00:00: iomem range 0x0-0x0 could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467516] system 00:00: iomem range 0x0-0x0 could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467519] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467521] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467523] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467530] system 00:02: ioport range 0x164e-0x164f has been reserved
Jun  5 09:56:34 Legolas kernel: [   20.467532] system 00:02: ioport range 0x1000-0x107f has been reserved
Jun  5 09:56:34 Legolas kernel: [   20.467535] system 00:02: ioport range 0x1180-0x11bf has been reserved
Jun  5 09:56:34 Legolas kernel: [   20.467537] system 00:02: ioport range 0x800-0x80f has been reserved
Jun  5 09:56:34 Legolas kernel: [   20.467539] system 00:02: ioport range 0x15e0-0x15ef has been reserved
Jun  5 09:56:34 Legolas kernel: [   20.467542] system 00:02: ioport range 0x1600-0x165f could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467544] system 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467547] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467550] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467552] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467555] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467557] system 00:02: iomem range 0xfed45000-0xfed4bfff could not be reserved
Jun  5 09:56:34 Legolas kernel: [   20.467935] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0
```
```
Jun  5 09:56:40 Legolas dhcdbd: dbus_svc_init failed: org.freedesktop.DBus.Error.FileNotFound Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
Jun  5 09:56:40 Legolas dhcdbd: Failed to initialise D-Bus service. 
Jun  5 09:56:40 Legolas kernel: [   36.647403] Bluetooth: Core ver 2.11
Jun  5 09:56:40 Legolas kernel: [   36.648017] NET: Registered protocol family 31
Jun  5 09:56:40 Legolas kernel: [   36.648022] Bluetooth: HCI device and connection manager initialized
Jun  5 09:56:40 Legolas kernel: [   36.648028] Bluetooth: HCI socket layer initialized
Jun  5 09:56:40 Legolas kernel: [   36.781159] Bluetooth: L2CAP ver 2.9
Jun  5 09:56:40 Legolas kernel: [   36.781167] Bluetooth: L2CAP socket layer initialized
Jun  5 09:56:40 Legolas kernel: [   36.785973] Bluetooth: RFCOMM socket layer initialized
Jun  5 09:56:40 Legolas kernel: [   36.785994] Bluetooth: RFCOMM TTY layer initialized
Jun  5 09:56:40 Legolas kernel: [   36.785998] Bluetooth: RFCOMM ver 1.8
Jun  5 09:56:45 Legolas kernel: [   40.153957] ACPI: ACPI Dock Station Driver 
Jun  5 09:56:45 Legolas kernel: [   40.263470] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
Jun  5 09:57:31 Legolas gnome-power-manager: (gemorgan) This program cannot start until you start the dbus system service. It is <b>strongly recommended</b> you reboot your computer after starting this service.
```

So I see a missing file for the dbus thingy but don't know what to do to fix it. Can anyone help?

Thanks!

---

### Post by Mander on 2008-06-05
I've been fiddling around with this all day long, and couldn't figure out how to fix it.

In the end, I booted into the previous kernel (.17) and uninstalled yesterday's update.  So far it seems to be working the way it was before.

Probably not an especially elegant solution, but it did seem to work for now.

---

### Post by nowhere@cox.net on 2008-06-05
Here's a list of what updated:
```
Commit Log for Thu Jun  5 08:23:53 2008


Upgraded the following packages:
dpkg (1.14.16.6ubuntu3) to 1.14.16.6ubuntu4
dpkg-dev (1.14.16.6ubuntu3) to 1.14.16.6ubuntu4
evolution (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-common (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-data-server (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-data-server-common (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-plugins (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libcamel1.2-11 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libebook1.2-9 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libecal1.2-7 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libedata-book1.2-2 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libedata-cal1.2-6 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libedataserver1.2-9 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libedataserverui1.2-8 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libegroupwise1.2-13 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libexchange-storage1.2-3 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libgdata-google1.2-1 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libgdata1.2-1 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libgnomeui-0 (2.22.1.0-0ubuntu1) to 2.22.1.0-0ubuntu2
libgnomeui-common (2.22.1.0-0ubuntu1) to 2.22.1.0-0ubuntu2
libgtk-vnc-1.0-0 (0.3.4-0ubuntu1) to 0.3.4-0ubuntu2
libnautilus-extension1 (1:2.22.2-0ubuntu6) to 1:2.22.3-0ubuntu2
nautilus (1:2.22.2-0ubuntu6) to 1:2.22.3-0ubuntu2
nautilus-data (1:2.22.2-0ubuntu6) to 1:2.22.3-0ubuntu2
rhythmbox (0.11.5-0ubuntu6) to 0.11.5-0ubuntu7
```

And before that was this, but I am pretty sure I have rebooted since this update
```
Commit Log for Tue Jun  3 22:03:47 2008


Upgraded the following packages:
linux-backports-modules-hardy (2.6.24.17.19) to 2.6.24.18.20
linux-backports-modules-hardy-generic (2.6.24.17.19) to 2.6.24.18.20
linux-generic (2.6.24.17.19) to 2.6.24.18.20
linux-headers-generic (2.6.24.17.19) to 2.6.24.18.20
linux-image-generic (2.6.24.17.19) to 2.6.24.18.20
linux-restricted-modules-generic (2.6.24.17.19) to 2.6.24.18.20

Installed the following packages:
linux-backports-modules-2.6.24-18-generic (2.6.24-18.16)
linux-headers-2.6.24-18 (2.6.24-18.32)
linux-headers-2.6.24-18-generic (2.6.24-18.32)
linux-image-2.6.24-18-generic (2.6.24-18.32)
linux-restricted-modules-2.6.24-18-generic (2.6.24.13-18.41)
linux-ubuntu-modules-2.6.24-18-generic (2.6.24-18.26)

```

---

### Post by nowhere@cox.net on 2008-06-05
How do I uninstall the whole update? I know how to boot to the previous kernel...

Thanks!

---

### Post by nowhere@cox.net on 2008-06-05
Ok here is some more info. 

I re-installed dbus since there was a file reported missing or something. Didn't fix the problem

If I try to re-install hal I get a post-installation script failure
```
Log started: 2008-06-05  14:14:19
(Reading database ... 170660 files and directories currently installed.)

Preparing to replace hal 0.5.11~rc2-1ubuntu8.1 (using .../hal_0.5.11~rc2-1ubuntu8.1_amd64.deb) ...

 * Stopping Hardware abstraction layer hald

   ...done.

Unpacking replacement hal ...

Setting up hal (0.5.11~rc2-1ubuntu8.1) ...

 * Reloading system message bus config...

Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

invoke-rc.d: initscript dbus, action "force-reload" failed.

polkit-auth: This operation requires the system message bus and ConsoleKit to be running

polkit-auth: AuthorizationAlreadyExists: An authorization for uid 111 for the action org.freedesktop.policykit.read with constraint '' already exists

dpkg: error processing hal (--configure):

 subprocess post-installation script returned error exit status 1

Errors were encountered while processing:

 hal

Log ended: 2008-06-05  14:14:35
```

So I booted to the previous kernel (0,17) then downgraded dpkg since it was just upgraded tried reinstalling hal but get the same error. BUT If I used synaptic to re-install dbus and hal together sequentially, they both succeed. 

```
(Reading database ... 170660 files and directories currently installed.)
Preparing to replace dbus 1.1.20-1ubuntu2 (using .../dbus_1.1.20-1ubuntu2_amd64.deb) ...
Unpacking replacement dbus ...
Setting up dbus (1.1.20-1ubuntu2) ...
The user `messagebus' already exists. Exiting.
 * Starting system message bus dbus
   ...done.
 * Starting network connection manager NetworkManager
   ...done.
 * Starting network events dispatcher NetworkManagerDispatcher
   ...done.
 * Starting System Tools Backends system-tools-backends
   ...done.
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon
   ...done.
 * Starting DHCP D-Bus daemon dhcdbd
   ...done.
 * Starting Hardware abstraction layer hald
   ...done.

Setting up hal (0.5.11~rc2-1ubuntu8.1) ...
 * Reloading system message bus config...
   ...done.
 * Starting Hardware abstraction layer hald
/usr/sbin/hald already running.
   ...done.
```

I can then log out and back in and everything is running. If I reboot, everything is messaged up again but I can repeat the synaptic re-install of dbus and hal and fix it all again.

What's up with THAT?

---

### Post by HermanAB on 2008-06-05
Hmm, I'm not a great fan of Automatic Screwups^WUpdates.

I always turn auto updates off.

Don't fix it if it ain't broke...

---

### Post by nowhere@cox.net on 2008-06-05
I hear that. I actually wanted all the evolution updates... Anyway, some more information:

While booted in the previous kernel I notice on the Services panel, dbus was unchecked. Don't know how that happened. I checked it, rebooted to the same kernel, hal still would not initialize but now the dbus entry in Services IS checked. I did a sudo /init.d/hal start and hal started fine. Then logged out and back in and all the stuff that needs hal (battery mon, network mon etc) seems to be fine. I reboot, hal won't start again. 

I boot to the newest kernel with the same results and there I can start hal on the command line just fine too. So the problem is with the startup scripts for hal. Other than the rcX.d run level scripts, I don't know where hal would be started at boot. In all runlevel folders, dbus is S12 and hal is S24 so that means dbus should be started before hal yes? 

Anyone?

---

### Post by nowhere@cox.net on 2008-06-05
I found the problem. For some reason (probably related to the unchecking of dbus in the Services app), in /etc/rc2.d the startup script for dbus was S50dbus while hal was S24hal. I didn't know run level 2 was used but just trying anything I mv'ed S50dbus to S12dbus and all works fine again.

I then started searching launchpad for bugs with this new info to improve my searches and found some stuff exactly like this going all the way back to breezy and mostly related to when kernel upgrades were done (we've had 2 in the last couple days). So...

Mander if you are still having trouble, give this a look...

Thanks all

---

