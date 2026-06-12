---
title: "&#65279;recent unexplained slow boot on 14.04"
date: 2014-10-01
forum: General Help
---

### Post by sp5 on 2014-10-01
Hello,

Recently, for reasons I can't understand, my boot times have gone from 5 seconds to 25 seconds.
By boot, I mean from grub flash screen to login prompt.
Obviously, I don't remember installing a program/service/hardware that could cause this huge delay.
The only updates that i see are from ubuntu update center.
Boot.log has also become huge. Instead of few lines, it is now a page and half of info that seems to repeat itself.


Only changes, that I can remember,and I don't think they are the problem because the delay was already there (I think):
--For dsl isp connection problems and troubleshooting, we've put the modem into router mode, created a dsl connection in ubuntu and deleted the ethernet connection.  After that was fixed, the dsl connection was deleted, the ethernet connection was recreated and modem switch back to bridge mode to use with my router.  There was, at a moment, an error about dns.  I've notice that in the logs there was an error about nss_hostname or something like it. So I've installed libnss-myhostname. That warning is gone, no effect on boot time.
---I've also installed a usb 3 extension cable. Unplugged it and no change on boot time.


Pc specs are:
-boot to linux from a ssd evo 1TB
-64 GB ram
-a 1TB hdd 
-another 1TB hdd
-a samsung 256GB ssd (for Windows only, boot to this drive by pressing f8 at bios boot time)
-dvd-rw
-cpu 3930k 6-cores hyperthreaded
-/var/log is mounted as tmpfs, same for /tmp.
All this setup was already there before the slow down.

You'll find the bootchart attached.

---

### Post by TheFu on 2014-10-01
Network issues, especially slow name resolution, are known to slow down boots.
/etc/nsswitch.conf normally has hosts resolution using files, then dns. I'd start there. Also, if either the hostname, hosts file or domainname have been touched recently ...

---

### Post by oldfred on 2014-10-01
Boot charts are almost always too small to read when attached. But I never learned how to read them anyway.
I prefer to look at dmesg.
You can use log file viewer, now system log. But you may have to click on far right star type icon to load dmseg.
Or just look at it in /var/log.

I look for outright error messages, warnings, repeated tries and either eventual failure or even success, and long times between entries. Do not post entire dmesg as most is just standard boot, but you can post bits that look like issues. If longer use code tags, easy to add in advanced editor by highlighting and clicking # icon in edit panel.

Just noticed in my new system it seems slow on mounting system partition or something from NVidia, I still do not know if time posted is start or end:

```
[    2.497866] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    9.310248] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro

```

---

### Post by sp5 on 2014-10-02
He're are parts of the dmesg where there are gaps:

[    2.114591] hid-generic 0003:046D:C408.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:1d.0-1.5/input0
[    3.230516] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.596531] random: init urandom read with 108 bits of entropy available
[    4.052132] random: nonblocking pool is initialized
[    5.112786] systemd-udevd[451]: starting version 204
[    5.650476] lp: driver loaded but no devices found
[    5.738739] nct6775: Found NCT6776D/F or compatible chip at 0x2e:0x290
[    5.754250] ppdev: user-space parallel port driver
[    6.290986] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    6.611836] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: errors=remount-ro
[    6.659163] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: errors=remount-ro


[    9.292084] e1000e 0000:00:19.0: irq 91 for MSI/MSI-X
[   10.849819] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   10.849823] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[   13.151070] vboxdrv: Found 12 processor cores.

[   13.462120] vboxpci: IOMMU not found (not registered)
[   14.338140] init: samba-ad-dc main process (1465) terminated with status 1
[   17.711771] fglrx_pci 0000:01:00.0: irq 93 for MSI/MSI-X

[   18.160699] init: plymouth-upstart-bridge main process ended, respawning
[   18.164744] init: plymouth-upstart-bridge main process (3579) terminated with status 1
[   18.164766] init: plymouth-upstart-bridge main process ended, respawning
[   38.029778] audit_printk_skb: 153 callbacks suppressed
[   38.029781] type=1400 audit(1412089581.155:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=5817 comm="apparmor_parser"
[   38.029785] type=1400 audit(1412089581.155:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=5817 comm="apparmor_parser"
[   38.030155] type=1400 audit(1412089581.155:65): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=5817 comm="apparmor_parser"

---

### Post by oldfred on 2014-10-02
Is this a Gigabyte board? I see a IOMMU reference.

       turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
    
But some others may need a boot parameter?
 IOMMU for USB3 ports Gigabyte board
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
Linux kernel enable the IOMMU &#8211; input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)

It looks like vbox install? Do not know about that.

Your main issue is 18 to 38 or a 20 sec delay. Do not know about either but possibly related to iommu?

---

### Post by sp5 on 2014-10-06
This is an asus sabertooth x79 not a Gigabyte motherboard.
As far as iommu, I don't have a clue what is that.  All bios settings are the same as they always were. (before and after the slow down).
Vbox (virtualbox) is and was installed before the slow down.
Network part, as fas as i know, seem identical to a brand new installation except the file/etc/nsswitch.conf that also has the word “myhostname” in the line of hosts.
Generally, if I login as soon as the login window appears, the last messages in dmesg are the ones at second 18.  Today those messages are at second 22.
I've reattached the initial bootchart but inside a zip file.

I've attached the boot.log.  
Theese messages were not many when I booted quickly. Now they're many, and the seem to repeat themselves in the same boot. It's like it's trying to dosomething and can't do it and retries, and retries, respawns,.... it's like I'm back in Windows world and a mechanical drive with theese boot times.

---

### Post by sp5 on 2014-10-28
This is now solved.  The problem was due to the samsung evo ssd known problem.  After applying their "performance restoration tool"  Everyting is back to normal and boot is back to 5 seconds.

---

