---
title: "[xubuntu] system froze"
date: 2020-04-19
forum: General Help
---

### Post by dbee on 2020-04-19
My xubuntu 18.0.4 LTS crashed on me all of a sudden. I checked 'top' before the crash and some swap program was hogging about 55% of the cpu so maybe it was a swap issue ...

here's my tail /var/log/syslog
```

dara@dara-HP-Stream-Laptop-11-y0XX:/var/log$ tail /var/log/syslog
Apr 19 18:36:14 dara-HP-Stream-Laptop-11-y0XX kernel: [   19.620441] random: crng init done
Apr 19 18:36:14 dara-HP-Stream-Laptop-11-y0XX kernel: [   19.620446] random: 7 urandom warning(s) missed due to ratelimiting
Apr 19 18:36:16 dara-HP-Stream-Laptop-11-y0XX dbus-daemon[776]: [session uid=1000 pid=776] Activating service name='org.gnome.keyring.SystemPrompter' requested by ':1.6' (uid=1000 pid=867 comm="gnome-keyring-daemon --start " label="unconfined")
Apr 19 18:36:16 dara-HP-Stream-Laptop-11-y0XX dbus-daemon[776]: [session uid=1000 pid=776] Successfully activated service 'org.gnome.keyring.SystemPrompter'
Apr 19 18:36:16 dara-HP-Stream-Laptop-11-y0XX gcr-prompter[1276]: GtkDialog mapped without a transient parent. This is discouraged.
Apr 19 18:36:27 dara-HP-Stream-Laptop-11-y0XX gcr-prompter[1276]: GtkDialog mapped without a transient parent. This is discouraged.
Apr 19 18:36:31 dara-HP-Stream-Laptop-11-y0XX systemd-timesyncd[470]: Synchronized to time server 91.189.94.4:123 (ntp.ubuntu.com).
Apr 19 18:36:41 dara-HP-Stream-Laptop-11-y0XX blueman-mechanism: Exiting
Apr 19 18:36:52 dara-HP-Stream-Laptop-11-y0XX systemd[1]: Starting Stop ureadahead data collection...
Apr 19 18:36:52 dara-HP-Stream-Laptop-11-y0XX systemd[1]: Started Stop ureadahead data collection.


```

here's a snap shot of my hardware ...

```

H/W path       Device  Class       Description
==============================================
                       system      HP Stream Laptop 11-y0XX (X9W60EA#ABU)
/0                     bus         82A9
/0/0                   memory      64KiB BIOS
/0/4                   processor   Intel(R) Celeron(R) CPU  N3060  @ 1.60GHz
/0/4/6                 memory      32KiB L1 cache
/0/4/7                 memory      1MiB L2 cache
/0/5                   memory      24KiB L1 cache
/0/20                  memory      2GiB System Memory
/0/20/0                memory      2GiB Row of chips DDR3 Synchronous 1600 MHz (0.6 ns)
/0/20/1                memory      Row of chips DDR Synchronous [empty]
/0/100                 bridge      Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register
/0/100/2               display     Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
/0/100/b               generic     Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
/0/100/14              bus         Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller
/0/100/1a              generic     Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine
/0/100/1b              multimedia  Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller
/0/100/1c              bridge      Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1
/0/100/1c/0            generic     RTS5229 PCI Express Card Reader
/0/100/1c.3            bridge      Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #4
/0/100/1c.3/0  wlo1    network     Wireless 7265
/0/100/1f              bridge      Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU
/0/100/1f.3            bus         Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx SMBus Controller
/1                     power       PO02037
/2                     power       OEM Define 5

```

```

dara@dara-HP-Stream-Laptop-11-y0XX:/var/log$ uname -a
Linux dara-HP-Stream-Laptop-11-y0XX 4.15.0-96-generic #97-Ubuntu SMP Wed Apr 1 03:25:46 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

Can anyone tell me why my system crashed ? I don't want it to happen again ...

---

### Post by CelticWarrior on 2020-04-19
```
memory      2GiB System Memory
```

In this day and age 2GiB of RAM is quite short so it tends to swap a lot depending on the use.

---

