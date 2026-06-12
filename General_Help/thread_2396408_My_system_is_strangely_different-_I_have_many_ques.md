---
title: "My system is strangely different- I have many questions"
date: 2018-07-15
forum: General Help
---

### Post by Gnusboy on 2018-07-15
There is something weird about my system tonight. I did a reboot Sat, 07/14 and was away until 1:00 AM now.
When I looked at the screen there several differences from usual. I keep the programs I use regularly on the left side of my screen. I turned on the monitor and:
The system icons were mixed up from where they usually are
Grsync icon was added
Gparted icon was added
Libre Writer icon was different
All the other icons were in different places.

And when I tried to move from one site to another in Firefox, a master password was required. I tried to cancel out of it, but it was persistent.
I closed Firefox, tried opening Chromium - but the Master Keyring password, popped up. I closed every open browser and looked at the logs. As I said before, I'm not knowledgeable of using the logs, 
but I do occasionally look at them. They just don't seem right.
I don't think I'm overly paranoid, but a recent incident gives me a nudge toward worry.
Here's the real question: Is there anything shown in excerpts of the logs I pasted that I should watch for?
Any explanation is welcome. Thank you.

Theres is also a 194.2 MB software d/l waiting.

I'm Running an AMD phenom with 4 GB ram on a desktop.

I opened the syslog:
dpkg log had large amount of data (I don't really know how to read the logs, but I scanned them and it seemed like they were different than usual)
Syslog file was initially blank

pm-powersave.log.3.g I have never seen listed before.

When syslog.1 opened, these are some of the entries I don't recall seeing before

```


***Your BIOS doesn't leave a aperture memory hole***
Jul 14 16:14:27 Ranha kernel: [    0.000000] ***Please enable the IOMMU option in the BIOS setup***
Jul 14 16:14:27 Ranha kernel: [    0.000000] This costs you 64 MB of RAM
Jul 14 16:14:27 Ranha kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
Jul 14 16:14:27 Ranha kernel: [    0.000000] PM: Registered nosave memory: [mem 0xc4000000-0xc7ffffff]
Jul 14 16:14:27 Ranha kernel: [    0.000000] Memory: 3701396K/3931252K available (7488K kernel code, 1163K rwdata, 3436K rodata, 1368K init, 1448K bss, 229856K reserved)
Jul 14 16:14:27 Ranha kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 14 16:14:27 Ranha kernel: [    0.000000] Hierarchical RCU implementation.
Jul 14 16:14:27 Ranha kernel: [    0.000000]    [I][B] RCU dyntick-idle grace-period acceleration is enabled.
Jul 14 16:14:27 Ranha kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Jul 14 16:14:27 Ranha kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Jul 14 16:14:27 Ranha kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[/B][/I]
```
```

Jul 14 16:14:27 Ranha kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
***Jul 14 16:14:27 Ranha kernel: [    0.000000] spurious 8259A interrupt: IRQ7.***
Jul 14 16:14:27 Ranha kernel: [    0.000000] Console: colour VGA+ 80x25
Jul 14 16:14:27 Ranha kernel: [    0.000000] console [tty0] enabled
Jul 14 16:14:27 Ranha kernel: [    0.000000] allocated 15728640 bytes of page_cgroup
***Jul 14 16:14:27 Ranha kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups***
Jul 14 16:14:27 Ranha kernel: [    0.000000] hpet clockevent registered
Jul 14 16:14:27 Ranha kernel: [    0.004000] tsc: Fast TSC calibration using PIT
Jul 14 16:14:27 Ranha kernel: [    0.008000] tsc: Detected 2510.918 MHz processor
Jul 14 16:14:27 Ranha kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 5021.83 BogoMIPS (lpj=10043672)
Jul 14 16:14:27 Ranha kernel: [    0.000066] pid_max: default: 32768 minimum: 301
Jul 14 16:14:27 Ranha kernel: [    0.000129] Security Framework initialized
[code]
[I][B]Jul 14 16:14:27 Ranha kernel: [    0.000178] AppArmor: AppArmor initialized
Jul 14 16:14:27 Ranha kernel: [    0.000208] Yama: becoming mindful.

```

```

Jul 14 16:14:27 Ranha kernel: [    0.286425] pci 0000:00:14.2: System wakeup disabled by ACPI

Jul 14 16:14:27 Ranha kernel: [    0.330637] NetLabel:  unlabeled traffic allowed by default

Jul 14 16:14:33 Ranha NetworkManager[818]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jul 14 16:14:33 Ranha dhclient: Listening on LPF/eth0/00:24:8c:33:e1:35
Jul 14 16:14:33 Ranha dhclient: Sending on   LPF/eth0/00:24:8c:33:e1:35
Jul 14 16:14:33 Ranha dhclient: Sending on   Socket/fallback
Jul 14 16:14:33 Ranha dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x6134eb4b)

```
```

ul 14 16:14:34 Ranha rtkit-daemon[1265]: Successfully called chroot.
Jul 14 16:14:34 Ranha rtkit-daemon[1265]: Successfully dropped privileges.
Jul 14 16:14:34 Ranha rtkit-daemon[1265]: Successfully limited resources.
Jul 14 16:14:34 Ranha rtkit-daemon[1265]: Running.
Jul 14 16:14:34 Ranha rtkit-daemon[1265]: Watchdog thread running.
Jul 14 16:14:34 Ranha rtkit-daemon[1265]: Canary thread running.
Jul 14 16:14:34 Ranha rtkit-daemon[1265]: Successfully made thread 1263 of process 1263 (n/a) owned by '112' high priority at nice level -11.
Jul 14 16:14:34 Ranha rtkit-daemon[1265]: Supervising 1 threads of 1 processes of 1 users.
Jul 14 16:14:34 Ranha rtkit-daemon[1265]: Successfully made thread 1319 of process 1263 (n/a) owned by '112' RT at priority 5.
Jul 14 16:14:34 Ranha rtkit-daemon[1265]: Supervising 2 threads of 1 processes of 1 users.
Jul 14 16:14:34 Ranha avahi-daemon[508]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::224:8cff:fe33:e135.
Jul 14 16:14:34 Ranha avahi-daemon[508]: New relevant interface eth0.IPv6 for mDNS.
Jul 14 16:14:34 Ranha avahi-daemon[508]: Registering new address record for fe80::224:8cff:fe33:e135 on eth0.*.

Jul 14 16:21:25 Ranha rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="407" x-info="http://www.rsyslog.com"] rsyslogd was HUPed

```

[/B][/I]dpkg.log had these entries (as well as many more lines of code.I have seen this before, but still don't understand their use.)
[I][B]
```

ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
    HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII

```








[/B][/I]

---

