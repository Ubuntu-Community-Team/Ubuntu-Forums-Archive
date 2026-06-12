---
title: "Ubuntu Gnome 16.04.3 freezing"
date: 2017-08-14
forum: General Help
---

### Post by Arbiter on 2017-08-14
Hello all, 

I've been using Ubuntu 16.04 since release without an issue, until recently. Ever since the third point release, my computer will hard-lock on or shortly after login.  After a couple resets, I can use the system, but its getting very frustrating having to reboot my PC three times just to use it. 

I am on the latest available 4.10 kernel after doing a dist-upgrade. Here is a quick listing of my hardware :

CPU: AMD FX-8150 "Zambezi" 8-Core 3.6GHz Socket AM3+ CPU
Mobo: Asus M5A99X EVO AM3+ AMD 990X Chipset Motherboard
RAM: G.Skill Sniper Series 16GB (4x4GB) DDR3-1866 240-Pin SDRAM PC3-14900
Video: EVGA GeForce GTX 960 4GB SC GAMING
ODD0: LG Blu-Ray Burner WH16NS40 SATA BD/DVD/CD-RW
HDD0: Seagate NAS 2TB ST2000VN000 SATA 6Gb/s Hard Drive

Any insight would be greatly appreciated. 

Thank you!

---

### Post by VMC on 2017-08-14
Check the logs (/var/log/) syslog then kernlog. Look for any errors. Also what errors does
```
journalctl -b -p err
```show?

---

### Post by Arbiter on 2017-08-15
Hello VMC,

Thank you for replying to me.  For the record now, I've now witnessed the same problem happening in Linux Mint 18.2 XFCE.  If I'm not mistaken Mint 18.2 is based on Ubuntu 16.04.2, which makes me think this is more hardware than software related.  Random system hard-locks.  Here's the output of the command you specified:

```

-- Logs begin at Tue 2017-08-15 20:50:14 EDT, end at Tue 2017-08-15 21:05:28 EDT. --
Aug 15 20:50:20 shodan systemd[1]: Failed to start Tell Plymouth To Write Out Runtime Data.
Aug 15 20:50:20 shodan systemd[1]: Failed to start Braille Device Support.
Aug 15 20:50:20 shodan systemd[1]: Failed to start Show Plymouth Boot Screen.
Aug 15 20:50:27 shodan ntpdate[1206]: name server cannot be used: Temporary failure in name resolution (-3)
Aug 15 20:50:28 shodan NetworkManager[951]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Aug 15 20:50:30 shodan /hpfax[1267]: [1267]: error: Failed to create /var/spool/cups/tmp/.hplip
Aug 15 20:50:36 shodan lightdm[1474]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or dire
Aug 15 20:50:36 shodan lightdm[1474]: PAM adding faulty module: pam_kwallet.so
Aug 15 20:50:36 shodan lightdm[1474]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or di
Aug 15 20:50:36 shodan lightdm[1474]: PAM adding faulty module: pam_kwallet5.so
Aug 15 20:50:37 shodan ntpd[1531]: unable to bind to wildcard address :: - another process may be running - EXITING
Aug 15 20:50:40 shodan lightdm[1668]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or dire
Aug 15 20:50:40 shodan lightdm[1668]: PAM adding faulty module: pam_kwallet.so
Aug 15 20:50:40 shodan lightdm[1668]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or di
Aug 15 20:50:40 shodan lightdm[1668]: PAM adding faulty module: pam_kwallet5.so
Aug 15 20:50:52 shodan pulseaudio[2123]: [pulseaudio] pid.c: Daemon already running.
Aug 15 20:50:52 shodan pulseaudio[2127]: [pulseaudio] pid.c: Daemon already running.
Aug 15 20:51:17 shodan pulseaudio[1971]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. 
lines 1-19/19 (END)

```

I've poured over the syslog and kern.log files, I can't seem to find anything that looks out of the ordinary.  Not sure what any of the above means exactly.

Again, thank you for taking the time to help me out.

---

### Post by VMC on 2017-08-15
Are you running on nouveau or nvidia driver? If I don't have nvidia driver installed my system will freeze.

---

### Post by Arbiter on 2017-08-15
I have the Nvidia driver installed.

---

### Post by VMC on 2017-08-16
Sometimes re-seating ram modules will fix the problem. Run the memtest from the grub. Also have you run a hard drive diagnostics test?

---

