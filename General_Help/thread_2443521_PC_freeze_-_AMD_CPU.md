---
title: "PC freeze - AMD CPU"
date: 2020-05-16
forum: General Help
---

### Post by JakcV on 2020-05-16
Hi,
I am long time user of Ubuntu. I just bought a new desktop with spec:
Tested on Ubuntu 20.04, 19.10, Ubuntu Budgie 19.10
CPU: AMD 3600
Mainboard: b450M
Graphic: Radeon RX 570

I ran memtest86 on my RAM, 4 passed without error

My old laptop with Intel T8100 CPU run Ubuntu 19.10 with no issue. 

Initially, I suspect is due to AMD C6 state issue. I use this [https://github.com/joakimkistowski/amd-disable-c6](https://github.com/joakimkistowski/amd-disable-c6) to disable the c6 state.
Then I also append intel_idle.max_cstate=0 processor.max_cstate=1 to the kernel parameter. 

My desktop still freeze after these workaround. I can't reproduce it. It happen randomly, when I browser webpage, watching Youtube. Freezing also happen when i Folding with my CPU, so I suspect not related to C6 state issue. I dual boot with Windows 10. In Windows, freezing does not happen.

I checked with journalctl, I didn't find any error.

Any way to debug this issue?

journalctl last 20 line of 2 freeze
```

May 02 05:48:35 -B450M-Ver1-0 systemd[1]: Starting Network Manager Script Dispatcher Service...
May 02 05:48:35 -B450M-Ver1-0 dbus-daemon[877]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 02 05:48:35 -B450M-Ver1-0 systemd[1]: Started Network Manager Script Dispatcher Service.
May 02 05:48:45 -B450M-Ver1-0 systemd[1]: NetworkManager-dispatcher.service: Succeeded.
May 02 06:14:31 -B450M-Ver1-0 systemd-resolved[843]: Grace period over, resuming full feature set (UDP+EDNS0) for DNS server fe80::66ee:b7ff:fe8a:8e62%3.
May 02 06:15:01 -B450M-Ver1-0 systemd-resolved[843]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
May 02 06:15:01 -B450M-Ver1-0 systemd-resolved[843]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
May 02 06:15:01 -B450M-Ver1-0 systemd-resolved[843]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
May 02 06:15:01 -B450M-Ver1-0 systemd-resolved[843]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
May 02 06:15:11 -B450M-Ver1-0 systemd-resolved[843]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
May 02 06:15:11 -B450M-Ver1-0 systemd-resolved[843]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
May 02 06:16:01 -B450M-Ver1-0 systemd-resolved[843]: Using degraded feature set (UDP) for DNS server fe80::66ee:b7ff:fe8a:8e62%3.
May 02 06:17:01 -B450M-Ver1-0 CRON[13285]: pam_unix(cron:session): session opened for user root by (uid=0)
May 02 06:17:01 -B450M-Ver1-0 CRON[13286]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 02 06:17:01 -B450M-Ver1-0 CRON[13285]: pam_unix(cron:session): session closed for user root
May 02 06:25:01 -B450M-Ver1-0 CRON[13346]: pam_unix(cron:session): session opened for user root by (uid=0)
May 02 06:25:01 -B450M-Ver1-0 CRON[13347]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
May 02 06:25:01 -B450M-Ver1-0 CRON[13346]: pam_unix(cron:session): session closed for user root
May 02 06:35:50 -B450M-Ver1-0 systemd-resolved[843]: Grace period over, resuming full feature set (UDP+EDNS0) for DNS server 192.168.1.1.
May 02 06:35:55 -B450M-Ver1-0 systemd-resolved[843]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
May 02 06:37:09 -B450M-Ver1-0 systemd-resolved[843]: Using degraded feature set (UDP) for DNS server 192.168.1.1.

```
```

May 06 18:25:07 -B450M-Ver1-0 rtkit-daemon[1172]: Supervising 4 threads of 2 processes of 1 users.
May 06 18:25:07 -B450M-Ver1-0 rtkit-daemon[1172]: Supervising 4 threads of 2 processes of 1 users.
May 06 18:25:08 -B450M-Ver1-0 rtkit-daemon[1172]: Supervising 4 threads of 2 processes of 1 users.
May 06 18:25:08 -B450M-Ver1-0 rtkit-daemon[1172]: Supervising 4 threads of 2 processes of 1 users.
May 06 18:25:38 -B450M-Ver1-0 rtkit-daemon[1172]: Supervising 4 threads of 2 processes of 1 users.
May 06 18:25:38 -B450M-Ver1-0 rtkit-daemon[1172]: Supervising 4 threads of 2 processes of 1 users.
May 06 18:26:39 -B450M-Ver1-0 gnome-shell[1971]: Could not create transient scope for PID 5056: GDBus.Error:org.freedesktop.DBus.Error.UnixProcessIdUnknown: Process with ID 5056 does not exist.
May 06 18:26:41 -B450M-Ver1-0 gnome-shell[5058]: X Error of failed request:  BadWindow (invalid Window parameter)
May 06 18:26:41 -B450M-Ver1-0 gnome-shell[5058]:   Major opcode of failed request:  18 (X_ChangeProperty)
May 06 18:26:41 -B450M-Ver1-0 gnome-shell[5058]:   Resource id in failed request:  0x300005f
May 06 18:26:41 -B450M-Ver1-0 gnome-shell[5058]:   Serial number of failed request:  13
May 06 18:26:41 -B450M-Ver1-0 gnome-shell[5058]:   Current serial number in output stream:  15
May 06 18:26:41 -B450M-Ver1-0 gnome-shell[1971]: Could not create transient scope for PID 5058: GDBus.Error:org.freedesktop.DBus.Error.UnixProcessIdUnknown: Process with ID 5058 does not exist.
May 06 18:26:41 -B450M-Ver1-0 dbus-daemon[913]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.130' (uid=1000 pid=2697 comm="/usr/lib/firefox/firefox -new-window " label="unconfined")
May 06 18:26:41 -B450M-Ver1-0 systemd[1]: Starting Hostname Service...
May 06 18:26:41 -B450M-Ver1-0 dbus-daemon[913]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 06 18:26:41 -B450M-Ver1-0 systemd[1]: Started Hostname Service.
May 06 18:27:11 -B450M-Ver1-0 systemd[1]: systemd-hostnamed.service: Succeeded.

```

---

### Post by mörgæs on 2020-05-17
Is the UEFI firmware updated?

---

### Post by kurt18947 on 2020-05-17
What Morgaes said. Check with your motherboard manufacturer's web site. Ryzen 3xxx will likely require a fairly recent BIOS version. If you have an older video card, you could try disabling the onboard video and inserting a PCIe video. I had quite a few challenges with onboard video on a Ryzen 2200G until Ubuntu 20.04 came out. In my case resume from suspend didn't work most of the time.

---

### Post by JakcV on 2020-05-19
I have update my bios to the latest which dated Oct 2019. In the description said, update to support Zen 1/2/3 processor. Ryzen 5 3600 does not have APU. I use discrete PCIe Video Radeon RX570.

---

### Post by JakcV on 2020-05-23
Is there any suggestion debug this issue?

---

### Post by kurt18947 on 2020-05-25
This probably won't help but it doesn't cost anything to try and shouldn't break anything irrecoverably I don't think. No guarantees though. When you log on, you should see a little round thing in the lower right side of the monitor. If you click on it you should have a choice of using X.org or Wayland. Select Wayland and log in. When I was having trouble with 18.04 Wayland seemed to be a little better though not perfect. Beyond that have you checked into your motherboard's manufacturer forums? My problem board was an Asrock AB350M and found some helpful hints on Asrock's forums. 

Which video driver is your system using? You can tell by issuing this command in a terminal:

```
lsmod
```

I have a 2012 vintage chip in my machine currently. It uses the older AMD driver, radeon. Newer cards use AMDGPU. This is purely a feeling on my part but it seems like radeon is more trouble-free. You don't have a choice about which driver is used as far as I know; older GPUs use radeon, newer GPUs use AMDGPU.

---

### Post by ra7411 on 2020-05-25
I built a Ryzen 3 3200g w/ a B450 mobo in January.

The BIOS is easy to update from instructions on MSI site.

Mine required a Kernel 5 to run right.  Then the suspend/resume didn't work right until I went to a 5.1.0 by trial and error of a series going from 5.1 to around 5.7?

I use the built in vid, and whatever driver Ub 18.04 plugged in has been fine.

And, I installed Ub 20.04 a few weeks ago as an aux o/s and all went well  - i.e. so will yours with a little of the usual wrangling.

 Good luck.

---

### Post by JakcV on 2020-05-26
lshw -class display

```

*-display                 
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:09:00.0
       version: ef
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:66 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:f000(size=256) memory:fcf00000-fcf3ffff memory:c0000-dffff

```

I am using the amdgpu driver as default. 

Now using Wayland, still have the issue. 

I got a few days without issue, thought some update solve this issue. But then yesterday, this issue came back.


Thanks

---

### Post by JakcV on 2020-06-22
After testing for long time, seem like the issue related to WIFI driver that I am using rtl8192ce.

After analyze for long time the freeze happen when I am torrenting. I reduce the total connection from 300 to 50, until now it does not freeze again. Tested with total connection of 100 still freeze.

---

