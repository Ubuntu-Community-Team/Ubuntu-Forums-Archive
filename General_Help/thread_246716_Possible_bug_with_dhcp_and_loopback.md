---
title: "Possible bug with dhcp and loopback"
date: 2006-08-29
forum: General Help
---

### Post by ultralame on 2006-08-29
Background:
Running 6.06, static IP on eth0.

I previously posted about booting up to find a badly configured loopback.  I think it may be due to a bug I found listed during hoary development, but I am not sure.

This problem did not start right away after I installed Dapper (from scratch).  But I can't say what may have caused it as I did not reboot after configuring each of the packages.  (I switched to Universe and I use the machine as a DNS server, dhcp server, and LAMP).

When I boot up:
#ifconfig lo
> lo Link encap:Local Loopback
LOOPBACK MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

If I use /etc/init.d/networking restart, this does not help!
So I use:
[INDENT]#ifdown lo
#ifup lo[/INDENT]

and that reconfigures the lo:
#ifconfig lo
> lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

So I found this bug report (google search):
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/13947]("https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/13947")

And they mention how the dhcp3 client may mess up the lo interface by issuing:
> ifconfig lo 0 up

So I checked my config, and to my untrained eye it looks like the  /etc/dhcp3/dhclient-script might issue that command on lo.

But I can't be sure.  Also, I am not running as a dhcp client!

I checked my rc folders, and the only place that specifically mentions '/etc/dhcp3/dhclient-script' is the readahead script.  but that doesn't seem to invoke the code.

Also, the problem persists in Single User mode (from boot) so it should be in rcS.d, right?

Does anyone know how to step through the startup scripts, so I can check and see which one may be doing the damage?

Here's the contents of my rcS.d:
> S01mountvirtfs -> ../init.d/mountvirtfs
S01readahead -> ../init.d/readahead
S02hostname.sh -> ../init.d/hostname.sh
S05keymap.sh -> ../init.d/keymap.sh
S07linux-restricted-modules-common -> ../init.d/linux-restricted-modules-common
S08loopback -> ../init.d/loopback
S10udev -> ../init.d/udev
S11mountdevsubfs -> ../init.d/mountdevsubfs
S13pcmciautils -> ../init.d/pcmciautils
S15module-init-tools -> ../init.d/module-init-tools
S17procps.sh -> ../init.d/procps.sh
S20checkroot.sh -> ../init.d/checkroot.sh
S22mtab -> ../init.d/mtab
S25brltty -> ../init.d/brltty
S25mdadm-raid -> ../init.d/mdadm-raid
S26lvm -> ../init.d/lvm
S27evms -> ../init.d/evms
S30checkfs.sh -> ../init.d/checkfs.sh
S35mountall.sh -> ../init.d/mountall.sh
S39readahead-desktop -> ../init.d/readahead-desktop
S40networking -> ../init.d/networking
S40pcmcia -> ../init.d/pcmcia
S45waitnfs.sh -> ../init.d/waitnfs.sh
S50hwclock.sh -> ../init.d/hwclock.sh
S55dns-clean -> ../init.d/dns-clean
S55pppd-dns -> ../init.d/pppd-dns
S70screen -> ../init.d/screen
S70x11-common -> ../init.d/x11-common
S80bootmisc.sh -> ../init.d/bootmisc.sh
S85urandom -> ../init.d/urandom
S90console-screen.sh -> ../init.d/console-screen.sh

---

### Post by ultralame on 2006-08-31
Semi-Fixed.

I added the lines to my interfaces file to hopefully force the ip address:

#cat /etc/network/interfaces
> auto lo
iface lo inet loopback
[COLOR="Red"]address 127.0.0.1
netmask 255.0.0.0[/COLOR]

And when I boot, this seems to work.

Now, I found this article about a possible bug on Ubuntu Hoary (5.10):
[https://launchpad.net/distros/ubuntu...ols/+bug/13947](https://launchpad.net/distros/ubuntu...ols/+bug/13947)

And it states that the dhcp client may execute:
> ifconfig lo 0 up

Which would have the effect of removing the ip address from the loopback.

Problem is, that I don't have any dynamic addresses on my system, so I am trying to figure out what might be causing that to happen.

I am also not sure what the concensus is concerning adding those lines, and what other effect that might have on the system.

---

### Post by ultralame on 2006-09-01
Not working again.  It rebooted correctly once, but not again after that.

Anyone have any idea?!

---

