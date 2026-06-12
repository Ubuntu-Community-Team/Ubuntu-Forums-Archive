---
title: "Ubuntu Studio 20.10 login screen freezing intermittently"
date: 2021-01-19
forum: General Help
---

### Post by JamKromium on 2021-01-19
Hi,

As per the above on occasion, say 1 in 5 boot ups, the Ubuntu Studio login screen is unresponsive and I need to Ctrl+Alt+F2 to the terminal to reboot or shutdown which then again has a 1 in 5 chance of letting me into the Plasma desktop. I can still see and move the mouse cursor but cannot select anything.

Grateful if anyone could offer any suggestions or perhaps logs to review to see why this is happening and how to solve it.

System Info as follows:
**Software:**
Ubuntu Studio 20.10
KDE Plasma Version: 5.19.5
KDE Frameworks Version: 5.74.0
Qt version: 5.15.2
Kernel Version: 5.8.0-38-lowlatency
OS Type: 64-bit
[B]Hardware
[/B]Processors: 8 x AMD Ryzen 7 4700U with Radeon Graphics
Memory: 7.2GiB of RAM
Graphics Processor: AMD RENOIR

Thanks

---

### Post by CelticWarrior on 2021-01-20
Before anything else update firmwares, UEFI ("BIOS") and SSD's.

---

### Post by JamKromium on 2021-01-24
Checked and I'm up to date, what's next?

---

### Post by CelticWarrior on 2021-01-24
You may need an even newer kernel than the one shipped with 20.10 for the new Ryzen 7.

---

### Post by vidtek on 2021-01-25
> **CelticWarrior said:**
> You may need an even newer kernel than the one shipped with 20.10 for the new Ryzen 7.

No-that won't help.   It's happening on Intel/Nvidia 20.10 Greedy too.   There is something else going on.

Tony.

---

### Post by vidtek on 2021-01-26
This was in my boot log file.

```
tony@linuxmint:~$ journalctl --boot=670561f1b926447ca7993fb59a2b5a13

[I][B]Then nearly 4000 lines of boot code and this:
[/B][/I]


Jan 25 12:39:34 linuxmint systemd[1]: Stopped LSB: Record successful boot for GRUB.
[COLOR="#FF0000"]Jan 25 12:39:34 linuxmint org.kde.ActivityManager[2588]: The X11 connection broke (error 1). Did the X11 server die?[/COLOR]
Jan 25 12:39:34 linuxmint org.kde.kglobalaccel[2584]: The X11 connection broke (error 1). Did the X11 server die?
Jan 25 12:39:34 linuxmint apport[7885]:  * Stopping automatic crash report generation: apport
Jan 25 12:39:34 linuxmint systemd[1]: Stopped target Network is Online.
Jan 25 12:39:34 linuxmint systemd[1]: NetworkManager-wait-online.service: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: Stopped Network Manager Wait Online.
Jan 25 12:39:34 linuxmint systemd[1]: cups-browsed.service: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: Stopped Make remote CUPS printers available locally.
Jan 25 12:39:34 linuxmint systemd[1]: Stopping Avahi mDNS/DNS-SD Stack...
Jan 25 12:39:34 linuxmint systemd[1]: Stopping CUPS Scheduler...
Jan 25 12:39:34 linuxmint avahi-daemon[1393]: Got SIGTERM, quitting.
Jan 25 12:39:34 linuxmint avahi-daemon[1393]: Leaving mDNS multicast group on interface enp0s31f6.IPv6 with address fe80::cb93:c21a>
Jan 25 12:39:34 linuxmint apport[7885]:    ...done.
Jan 25 12:39:34 linuxmint avahi-daemon[1393]: Leaving mDNS multicast group on interface enp0s31f6.IPv4 with address 192.168.0.42.
Jan 25 12:39:34 linuxmint avahi-daemon[1393]: Leaving mDNS multicast group on interface lo.IPv6 with address ::1.
Jan 25 12:39:34 linuxmint avahi-daemon[1393]: Leaving mDNS multicast group on interface lo.IPv4 with address 127.0.0.1.
Jan 25 12:39:34 linuxmint systemd[1]: apport.service: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: Stopped LSB: automatic crash report generation.
Jan 25 12:39:34 linuxmint systemd[1]: polkit.service: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: Stopped Authorization Manager.
Jan 25 12:39:34 linuxmint avahi-daemon[1393]: avahi-daemon 0.8 exiting.
Jan 25 12:39:34 linuxmint systemd[1]: avahi-daemon.service: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: Stopped Avahi mDNS/DNS-SD Stack.
Jan 25 12:39:34 linuxmint kernel: nfsd: last server has exited, flushing export cache
Jan 25 12:39:34 linuxmint systemd[1]: nfs-server.service: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: Stopped NFS server and services.
Jan 25 12:39:34 linuxmint systemd[1]: Stopping NFSv4 ID-name mapping service...
Jan 25 12:39:34 linuxmint systemd[1]: Stopping NFS Mount Daemon...
Jan 25 12:39:34 linuxmint rpc.mountd[1648]: Caught signal 15, un-registering and exiting.
Jan 25 12:39:34 linuxmint systemd[1]: nfs-idmapd.service: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: Stopped NFSv4 ID-name mapping service.
[COLOR="#FF0000"]Jan 25 12:39:34 linuxmint org.kde.KScreen[2744]: The X11 connection broke (error 1). Did the X11 server die?[/COLOR]
Jan 25 12:39:34 linuxmint systemd[1]: Unmounting RPC Pipe File System...
Jan 25 12:39:34 linuxmint systemd[1]: nfs-mountd.service: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: Stopped NFS Mount Daemon.
Jan 25 12:39:34 linuxmint systemd[2395]: run-rpc_pipefs.mount: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: run-rpc_pipefs.mount: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: Unmounted RPC Pipe File System.
Jan 25 12:39:34 linuxmint systemd[1]: cups.service: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: Stopped CUPS Scheduler.
Jan 25 12:39:34 linuxmint systemd[1]: session-3.scope: Succeeded.
Jan 25 12:39:34 linuxmint systemd[1]: Stopped Session 3 of user tony.
Jan 25 12:39:34 linuxmint systemd[1]: Stopping User Manager for UID 1000...
Jan 25 12:39:34 linuxmint systemd-logind[1451]: Removed session 3.

```

---

### Post by vidtek on 2021-01-31
This may help.   ```
journalctl --list-boots 
``` This gives a list of all logged boots in /var/log/boot.log

then to see individual boot entries just do ```
journalctl --boot=***************************
```

That may show something.  I'll be checking myself on my system, we can then compare.

Cheers Tony.

---

### Post by JamKromium on 2021-02-05
[COLOR=#000000]I've saved a successful boot to a text file using the above so will compare with the next unsuccessful boot. One thing I'll need to do more testing on; I think it may be more likely to fail when I have an external monitor connected to my DisplayPort, the other thing I've done was under Settings>Startup and Shutdown>Desktop Session>On Login>Start with an empty session (previously I had this as Restore previous session).

No failures in the past 5 days after the above is it may *may* be fixed[/COLOR]

---

### Post by vidtek on 2021-02-05
Still happening with me, I can't seem to get to the bottom of it.   We surely cannot be the only ones?

Tony.

---

### Post by vidtek on 2021-02-05
If anyone is looking at this thread, this is an extract from my boot today when it failed:```
Jan 27 15:33:51 linuxmint systemd[1]: Stopping Session 3 of user tony.
Jan 27 15:33:51 linuxmint sddm[1611]: Authentication error: "Process crashed"
Jan 27 15:33:51 linuxmint sddm[1611]: Auth: sddm-helper crashed (exit code 15)
Jan 27 15:33:51 linuxmint ModemManager[1571]: <info>  caught signal, shutting down...
Jan 27 15:33:51 linuxmint org.kde.runners.baloo[2776]: The X11 connection broke (error 1). Did the X11 server die?
Jan 27 15:33:51 linuxmint sddm[1611]: Authentication error: "Process crashed"
Jan 27 15:33:51 linuxmint polkitd(authority=local)[1383]: Unregistered Authentication Agent for unix-session:3 (system bus name :1.60,>
Jan 27 15:33:51 linuxmint sddm[1611]: Auth: sddm-helper exited with 15
Jan 27 15:33:51 linuxmint ModemManager[1571]: <info>  ModemManager is shut down
Jan 27 15:33:51 linuxmint sddm[1611]: Socket server stopping...
Jan 27 15:33:51 linuxmint sddm[1611]: Socket server stopped.
Jan 27 15:33:51 linuxmint sddm[1611]: Display server stopping...
Jan 27 15:33:51 linuxmint systemd[1]: Removed slice system-getty.slice.
Jan 27 15:33:51 linuxmint systemd[1]: Removed slice system-modprobe.slice.
Jan 27 15:33:51 linuxmint systemd[1]: Stopped target Bluetooth.
Jan 27 15:33:51 linuxmint bluetoothd[1347]: Terminating
Jan 27 15:33:51 linuxmint systemd[1]: Stopped target Graphical Interface.
Jan 27 15:33:51 linuxmint systemd[1]: Stopped target Multi-User System.
Jan 27 15:33:51 linuxmint systemd[1]: Stopped target Login Prompts.
Jan 27 15:33:51 linuxmint systemd[1]: Stopped target RPC Port Mapper.
Jan 27 15:33:51 linuxmint systemd[1]: Stopped target Sound Card.
Jan 27 15:33:51 linuxmint systemd[1]: Stopped target Timers.
Jan 27 15:33:51 linuxmint systemd[1]: anacron.timer: Succeeded.
Jan 27 15:33:51 linuxmint systemd[1]: Stopped Trigger anacron every hour.
Jan 27 15:33:51 linuxmint systemd[1]: apt-daily-upgrade.timer: Succeeded.
Jan 27 15:33:51 linuxmint systemd[1]: Stopped Daily apt upgrade and clean activities.
Jan 27 15:33:51 linuxmint systemd[1]: apt-daily.timer: Succeeded.
Jan 27 15:33:51 linuxmint systemd[1]: Stopped Daily apt download activities.
Jan 27 15:33:51 linuxmint systemd[1]: e2scrub_all.timer: Succeeded.
Jan 27 15:33:51 linuxmint systemd[1]: Stopped Periodic ext4 Online Metadata Check for All Filesystems.

```

Gobbledegook to me.....

---

