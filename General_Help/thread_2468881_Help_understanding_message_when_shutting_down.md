---
title: "Help understanding message when shutting down"
date: 2021-11-12
forum: General Help
---

### Post by lost-in-plex on 2021-11-12
Hello, I have an ubuntu 20.04 system with six external HDDs (2 in external cases and 4 in a 4 bay enclosure) and after a fresh install and shutdown I got this message (see attached). I don't really know what this is or means so any help is greatly appreciated.

---

### Post by Bashing-om on 2021-11-12
lost-in-plex; Hello - Welcome to the forum.

Looks to me like you need to find out what is going on with that 2nd hard drive, sdb.

Bad cable ?
bad power connection ?
bad power cable ?
cross wired ?
inconsistent file system ?
drive failed ?

In isolating the boot file will be your friend,
```

journalctl -b -0  #<-shows all messages from the current boot
journalctl -b |grep failed #<-  to see what failed while booting up
journalctl -p 3 -xb #if you want to filter for errors
journalctl -p 4 --since today #to see messages of priority 'warning' or higher. smaller number = higher priority

```

[INDENT]real UN-fun times
[/INDENT]

---

### Post by lost-in-plex on 2021-11-12
Thank you for the command to try this is the result of journalctl -p 4 : [https://pastebin.com/z2Q73wZV](https://pastebin.com/z2Q73wZV)

> plex@plex:~$ journalctl -p 4 --since today
-- Logs begin at Fri 2021-11-12 13:49:25 CST, end at Fri 2021-11-12 18:30:33 CST. --
Nov 12 13:49:25 plex kernel: ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Nov 12 13:49:25 plex kernel: platform eisa.0: EISA: Cannot allocate resource for mainboard
Nov 12 13:49:25 plex kernel: platform eisa.0: Cannot allocate resource for EISA slot 1
Nov 12 13:49:25 plex kernel: platform eisa.0: Cannot allocate resource for EISA slot 2
Nov 12 13:49:25 plex kernel: platform eisa.0: Cannot allocate resource for EISA slot 3
Nov 12 13:49:25 plex kernel: platform eisa.0: Cannot allocate resource for EISA slot 4
Nov 12 13:49:25 plex kernel: platform eisa.0: Cannot allocate resource for EISA slot 5
Nov 12 13:49:25 plex kernel: platform eisa.0: Cannot allocate resource for EISA slot 6
Nov 12 13:49:25 plex kernel: platform eisa.0: Cannot allocate resource for EISA slot 7
Nov 12 13:49:25 plex kernel: platform eisa.0: Cannot allocate resource for EISA slot 8
Nov 12 13:49:25 plex kernel: resource sanity check: requesting [mem 0xfdffe800-0xfe0007ff], which spans more than pnp 00:07 [mem 0xfdb00000-0xfdffffff]
Nov 12 13:49:25 plex kernel: caller pmc_core_probe+0x81/0x200 mapping multiple BARs
Nov 12 13:49:25 plex kernel: wmi_bus wmi_bus-PNP0C14:00: WQBC data block query control method not found
Nov 12 13:49:25 plex kernel: r8169 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
Nov 12 13:49:25 plex kernel: ata1.00: supports DRM functions and may not be fully accessible
Nov 12 13:49:25 plex kernel: ata1.00: NCQ Send/Recv Log not supported
Nov 12 13:49:25 plex kernel: ata1.00: supports DRM functions and may not be fully accessible
Nov 12 13:49:25 plex kernel: ata1.00: NCQ Send/Recv Log not supported
Nov 12 13:49:26 plex kernel: pcieport 0000:00:1c.7: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
Nov 12 13:49:26 plex kernel: pcieport 0000:00:1c.7:   device [8086:a297] error status/mask=00000001/00002000
Nov 12 13:49:26 plex kernel: pcieport 0000:00:1c.7:    [ 0] RxErr                 
Nov 12 13:49:26 plex kernel: thermal thermal_zone3: failed to read out thermal zone (-61)
Nov 12 13:49:26 plex systemd-udevd[322]: controlC0: Process '/usr/sbin/alsactl -E HOME=/run/alsa -E XDG_RUNTIME_DIR=/run/alsa/runtime restore 0' failed with exit>
Nov 12 13:49:29 plex kernel: kauditd_printk_skb: 12 callbacks suppressed
Nov 12 13:49:32 plex thermald[603]: sensor id 7 : No temp sysfs for reading raw temp
Nov 12 13:49:32 plex thermald[603]: sensor id 7 : No temp sysfs for reading raw temp
Nov 12 13:49:32 plex thermald[603]: sensor id 7 : No temp sysfs for reading raw temp
Nov 12 13:49:32 plex thermald[603]: error: could not parse file /etc/thermald/thermal-conf.xml
Nov 12 13:49:32 plex thermald[603]: error: could not parse file /etc/thermald/thermal-conf.xml
Nov 12 13:49:32 plex thermald[603]: error: could not parse file /etc/thermald/thermal-conf.xml
Nov 12 13:49:32 plex udisksd[607]: failed to load module mdraid: libbd_mdraid.so.2: cannot open shared object file: No such file or directory
Nov 12 13:49:32 plex udisksd[607]: Failed to load the 'mdraid' libblockdev plugin
Nov 12 13:49:32 plex NetworkManager[574]: <warn>  [1636746572.2613] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Nov 12 13:49:32 plex gdm-autologin][736]: gkr-pam: no password is available for user
Nov 12 13:49:32 plex /usr/lib/gdm3/gdm-x-session[765]: (--) Log file renamed from "/home/plex/.local/share/xorg/Xorg.pid-765.log" to "/home/plex/.local/share/xor>
Nov 12 13:49:32 plex /usr/lib/gdm3/gdm-x-session[765]: X.Org X Server 1.20.11
Nov 12 13:49:32 plex /usr/lib/gdm3/gdm-x-session[765]: X Protocol Version 11, Revision 0
Nov 12 13:49:32 plex /usr/lib/gdm3/gdm-x-session[765]: Build Operating System: linux Ubuntu
Nov 12 13:49:32 plex /usr/lib/gdm3/gdm-x-session[765]: Current Operating System: Linux plex 5.11.0-40-generic #44~20.04.2-Ubuntu SMP Tue Oct 26 18:07:44 UTC 2021>
lines 1-40
 

---

### Post by Bashing-om on 2021-11-12
lost-in-plex; Sorry -

Will take one more versed in the plex server to know why the raid array fails to build.

exit stage left -

[INDENT]a know-it-all I am not[/INDENT]

---

### Post by lost-in-plex on 2021-11-12
I think I am figuring it out, my setup is actually a JBOD setup and I "THINK" my issues stems from an external HDD with a spotty control board and permission issues with plex. I will update again if I get anymore of those black screen logs when shutting down or if problems persist. I think this is just multiple "gremlins" in the system that I am hunting down.

---

### Post by ActionParsnip on 2021-11-13
/dev/sdb doesn't look happy. I suggest you make sure your backups are good as a good first step
You can run an fsck on the drive but to me, it sounds like a failing disk

---

