---
title: "Clock problem"
date: 2007-10-31
forum: General Help
---

### Post by satimis on 2007-10-31
Hi folks,


Ubuntu 7.04 server amd64


For unknown cause the clock automatically changes time backware.  I have to run;
$ sudo date -s "mm/dd/yy hh:mm:00"
to correct it.

But after working a while the clock changes the time backwards again.


Please advise how to fix the problem.  TIA


B.R.
satimis

---

### Post by taurus on 2007-10-31
Sounds to me like your system is syncing your machine clock with the network clock.  

If you are in the US, your clock supposed to fall back to EST on Sunday morning but not this year.  We will not reset the clock until this Sunday monring, 2 AM would become 1 AM.

---

### Post by satimis on 2007-10-31
> **taurus said:**
> Sounds to me like your system is syncing your machine clock with the network clock.  

If you are in the US, your clock supposed to fall back to EST on Sunday morning but not this year.  We will not reset the clock until this Sunday monring, 2 AM would become 1 AM.
Thanks for your advice.


How to set it back to local time here, Hong Kong.  I'm now fixing problem on Postfix.  The clock will change on running some commands which are not aware to me.


satimis

---

### Post by taurus on 2007-10-31
Look to see if you have ntp running in the background.

```
ps -A
```

---

### Post by satimis on 2007-10-31
> **taurus said:**
> Look to see if you have ntp running in the background.

```
ps -A
```
$ ps -A```

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 migration/1
    6 ?        00:00:00 ksoftirqd/1
    7 ?        00:00:00 watchdog/1
    8 ?        00:00:00 events/0
    9 ?        00:00:00 events/1
   10 ?        00:00:00 khelper
   11 ?        00:00:00 kthread
   34 ?        00:00:00 kblockd/0
   35 ?        00:00:00 kblockd/1
   36 ?        00:00:00 kacpid
   37 ?        00:00:00 kacpi_notify
  194 ?        00:00:00 kseriod
  230 ?        00:00:00 pdflush
  231 ?        00:00:00 pdflush
  232 ?        00:00:00 kswapd0
  233 ?        00:00:00 aio/0
  234 ?        00:00:00 aio/1
 1998 ?        00:00:00 ksuspend_usbd
 1999 ?        00:00:00 khubd
 2017 ?        00:00:00 ata/0
 2018 ?        00:00:00 ata/1
 2019 ?        00:00:00 ata_aux
 2143 ?        00:00:00 scsi_eh_0
 2145 ?        00:00:00 scsi_eh_1
 2167 ?        00:00:00 scsi_eh_2
 2168 ?        00:00:00 scsi_eh_3
 2202 ?        00:00:00 scsi_eh_4
 2203 ?        00:00:00 scsi_eh_5
 2401 ?        00:00:00 kjournald
 2563 ?        00:00:00 udevd
 3524 ?        00:00:00 kpsmoused
 4030 ?        00:00:00 kjournald
 4335 tty4     00:00:00 getty
 4336 tty5     00:00:00 getty
 4340 tty2     00:00:00 getty
 4341 tty3     00:00:00 getty
 4342 tty1     00:00:00 login
 4343 tty6     00:00:00 getty
 4371 ?        00:00:00 syslogd
 4414 ?        00:00:00 dd
 4416 ?        00:00:00 klogd
 4434 ?        00:00:00 dbus-daemon
 4448 ?        00:00:00 hald
 4449 ?        00:00:00 hald-runner
 4455 ?        00:00:00 hald-addon-acpi
 4465 ?        00:00:00 hald-addon-keyb
 4468 ?        00:00:00 hald-addon-keyb
 4484 ?        00:00:00 hald-addon-stor
 4506 ?        00:00:00 named
 4603 ?        00:00:00 mysqld_safe
 4645 ?        00:00:00 mysqld
 4647 ?        00:00:00 logger
 4712 ?        00:00:00 courierlogger
 4713 ?        00:00:00 authdaemond
 4728 ?        00:00:00 courierlogger
 4729 ?        00:00:00 couriertcpd
 4732 ?        00:00:00 authdaemond
 4733 ?        00:00:00 authdaemond
 4734 ?        00:00:00 authdaemond
 4735 ?        00:00:00 authdaemond
 4736 ?        00:00:00 authdaemond
 4753 ?        00:00:00 courierlogger
 4754 ?        00:00:00 couriertcpd
 4767 ?        00:00:00 couriertcpd
 4769 ?        00:00:00 courierlogger
 4788 ?        00:00:00 courierlogger
 4789 ?        00:00:00 couriertcpd
 4897 ?        00:00:00 saslauthd
 4899 ?        00:00:00 saslauthd
 4900 ?        00:00:00 saslauthd
 4901 ?        00:00:00 saslauthd
 4902 ?        00:00:00 saslauthd
 4916 ?        00:00:00 sshd
 4924 ?        00:00:00 xfs
 4972 ?        00:00:00 xinetd
 5008 ?        00:00:00 proftpd
 5022 ?        00:00:00 atd
 5033 ?        00:00:00 cron
 5075 ?        00:00:00 vmnet-bridge
 5089 ?        00:00:00 vmnet-natd
 5094 ?        00:00:00 vmware-serverd
 5117 ?        00:00:00 vmnet-netifup
 5124 ?        00:00:00 vmnet-netifup
 5139 ?        00:00:00 vmnet-dhcpd
 5148 ?        00:00:00 vmnet-dhcpd
 5155 ?        00:00:00 httpd.vmware
 5166 ?        00:00:00 httpd.vmware
 5181 ?        00:00:00 httpd.vmware
 5245 tty1     00:00:00 bash
 5261 tty1     00:00:00 startx
 5277 tty1     00:00:00 xinit
 5278 tty7     00:15:38 Xorg
 5283 tty1     00:00:02 fluxbox
 5286 ?        00:00:00 sh
 5287 ?        00:07:02 firefox-bin
 5292 ?        00:00:00 scim-launcher
 5295 ?        00:00:00 scim-helper-man
 5296 ?        00:00:01 scim-panel-gtk
 5309 ?        00:00:00 netstat <defunct>
 5413 ?        00:00:00 apache2
 5440 ?        00:00:00 apache2
 5441 ?        00:00:00 apache2
 5442 ?        00:00:00 apache2
 5443 ?        00:00:00 apache2
 5444 ?        00:00:00 apache2
 5446 ?        00:00:00 cupsd
 5474 ?        00:00:00 python
 6085 ?        00:00:00 apache2
 6159 ?        00:00:00 sh
 6160 ?        00:00:00 xterm
 6161 pts/0    00:00:00 bash
 6185 ?        00:00:00 sh
 6186 ?        00:00:00 xterm
 6187 pts/1    00:00:00 bash
 6510 ?        00:00:00 sh
 6511 ?        00:00:00 leafpad
 6547 ?        00:00:00 sh
 6548 ?        00:00:00 xterm
 6549 pts/2    00:00:00 bash
 7070 ?        00:00:00 master
 7073 ?        00:00:00 pickup
 7074 ?        00:00:00 qmgr
 7078 ?        00:00:00 tlsmgr
 7130 pts/2    00:00:00 ps

```


I recall on installing this server "ntp ntpdate" have been installed.  How to stop them?  Remove them?  TIA


B.R.
satimis

---

### Post by taurus on 2007-10-31
Use synaptic and Search for it.  Then, remove it.

---

### Post by satimis on 2007-10-31
> **taurus said:**
> Use synaptic and Search for it.  Then, remove it.
I don't have synaptic, running Fluxbox, a light-weight desktop.


Performed following step;


$ sudo apt-get remove ntp ntpdate```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ntp ntpdate ubuntu-minimal
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1229kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 70375 files and directories currently installed.)
Removing ntp ...
 * Stopping NTP server ntpd                                                                                                     
 start-stop-daemon: warning: failed to kill 4989: No such process
                                                                                                                          [ OK ]
Removing ubuntu-minimal ...
Removing ntpdate ...
satimis@ubuntu:~$ sudo date -s "11/01/2007 02:23:00"
Thu Nov  1 02:23:00 PDT 2007
satimis@ubuntu:~$ 
```
Thanks


B.R.
satimis

---

