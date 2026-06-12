---
title: "Re: Hdd light constantly blinking"
date: 2016-02-09
forum: General Help
---

### Post by maglin2 on 2016-02-09
Using Xubuntu 14.04.  Intel quad core 2 ghz, 4gigs ram, 2.8 gigs "swap  total", hard drives have tons of unused free space on them.  On my  desktop, the hard drive light blinks constantly once or twice a second.   I tried physically disconnecting from the internet, same thing still  happens.  I have system load monitor installed on a panel, and cpu usage  is zero or close to zero, ram is about 600 used of 4000 total, swap is  zero.  This has been going on for a long time. I also have a laptop with  xubuntu 14.04 and the same thing happens, but not on my netbook with  xubuntu 14.04.  Any suggestions on how to stop this?  I just bought a  new desktop which I have not taken out of the box yet.  It has ssd's and  they are not supposed to be as durable as the rotary drives in my  current desktop, laptop and netbook, so if they will be constantly  written to they won't last long. Before I set up the new comp I want to  know how to fix this problem in case it happens with it.

Just a thought - and the only thought I will have on this, since I have no special subject knowledge, but I did have a blinking/clicking HDD.
Does this command temporarily solve the problem?
```
[COLOR=#0000FF]sudo hdparm -B 254 /dev/sda[/COLOR]
```
Taken from [https://sites.google.com/site/easylinuxtipsproject/bugs](https://sites.google.com/site/easylinuxtipsproject/bugs) - I think it is unlikely that this will be your desktop problem, since the author says it is related to laptop power management, but it may be worth a try.

---

### Post by QIII on 2016-02-09
How big is the drive? Have you replaced one lately?  Run iotop and see if there is a process called ext4lazyinit running.  If so, your system is building inodes and the inode table, which is normal and may take a while on a large mechanical drive.

---

### Post by marsdenf on 2016-02-09
The newest hard drive is 2 or 3 years old.  All drives are 600 gigs.  I installed iotop and ran it and don't see extr4lazyinit but there is : [ext4-rsv-conver] running.  I am not sure if I am seeing everything in the terminal window, I expanded it vertically to the top and bottom of my screen but maybe there is more?  How to scroll down a terminal window?

---

### Post by QIII on 2016-02-09
Would you please post the output of iotop?

---

### Post by marsdenf on 2016-02-09
if 'select all' is clicked, the copy to clipboard button becomes unshaded for half a second and then becomes shaded again.  In the terminal the output of iotop is constantly changing, is there a way to freeze it so I can copy it?

I managed to quickly copy it.   Here is the output: (not sure if I managed to get all of it)

```
Total DISK READ :       0.00 B/s | Total DISK WRITE :       0.00 B/s
Actual DISK READ:       0.00 B/s | Actual DISK WRITE:       0.00 B/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND                              
22469 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.23 % [kworker/u8:2]
22960 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.16 % [kworker/u8:0]
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]
    3 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/0]
 2455 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % udisksd --no-debug [gdbus]
    5 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/0:0H]
    7 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcu_sched]
    8 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [rcu_bh]
    9 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/0]
   10 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/0]
   11 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/1]
   12 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/1]
   13 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/1]
   15 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/1:0H]
   16 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/2]
   17 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/2]
   18 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/2]
   20 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/2:0H]
   21 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/3]
   22 rt/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/3]
   23 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/3]
  536 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kvm-irqfd-clean]
   25 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/3:0H]
   26 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khelper]
   27 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kdevtmpfs]
   28 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [netns]
   29 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [writeback]
   30 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kintegrityd]
   31 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [bioset]
   32 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/u9:0]
   33 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kblockd]
   34 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ata_sff]
   35 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khubd]
   36 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [md]
   37 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [devfreq_wq]
 1063 be/4 whoopsie    0.00 B/s    0.00 B/s  0.00 %  0.00 % whoopsie [gdbus]
  552 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [hd-audio0]
23593 be/4 postfix     0.00 B/s    0.00 B/s  0.00 %  0.00 % pickup -l -t fifo -u -c
   42 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khungtaskd]
   43 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kswapd0]
   44 be/5 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksmd]
   45 be/7 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khugepaged]
   46 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [fsnotify_mark]
   47 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ecryptfs-kthrea]
   48 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [crypto]
  562 be/4 avahi       0.00 B/s    0.00 B/s  0.00 %  0.00 % avahi-daemon: runni~arsdenf-P5Q-E.local]
  564 be/4 avahi       0.00 B/s    0.00 B/s  0.00 %  0.00 % avahi-daemon: chroot helper
 2398 be/4 marsdenf    0.00 B/s    0.00 B/s  0.00 %  0.00 % Thunar --daemon [gdbus]
20534 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % cupsd -f
   60 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthrotld]
 1085 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % acpid -c /etc/acpi/~var/run/acpid.socket
21566 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % dhclient -d -sf /us~lient-eth0.conf eth0
   63 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_0]
   64 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_1]
   66 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_2]
   67 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [scsi_eh_3]
 2117 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % lightdm --session-child 12 19 [gdbus]
 2316 be/4 marsdenf    0.00 B/s    0.00 B/s  0.00 %  0.00 % xfwm4 --replace
  439 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % bluetoothd
 2914 be/4 marsdenf    0.00 B/s    0.00 B/s  0.00 %  0.00 % dconf-service
 2126 be/4 marsdenf    0.00 B/s    0.00 B/s  0.00 %  0.00 % gnome-keyring-daemon --daemonize --login
 2127 be/4 marsdenf    0.00 B/s    0.00 B/s  0.00 %  0.00 % gnome-keyring-daemon --daemonize --login
 2128 be/4 marsdenf    0.00 B/s    0.00 B/s  0.00 %  0.00 % init --user
 2403 be/4 marsdenf    0.00 B/s    0.00 B/s  0.00 %  0.00 % wrapper-1.0 /usr/li~ovable media [gdbus]
   89 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [deferwq]
   90 be/0 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [charger_manager]
21775 be/4 marsdenf    0.00 B/s    0.00 B/s  0.00 %  0.00 % wrapper-1.0 /usr/li~ry footprint [gdbus]
 1117 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % cups-browsed
 2458 be/4 marsdenf    0.00 B/s    0.00 B/s  0.00 %  0.00 % alarmclock [gmain]
 1552 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % upowerd
11875 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kworker/1:2]
 2409 be/4 marsdenf    0.00 B/s    0.00 B/s  0.00 %  0.00 % gvfs-udisks2-volume-monitor
 2411 be/4 marsdenf    0.00 B/s    0.00 B/s  0.00 %  0.00 % wrapper-1.0 /usr/li~and memory footprint
```

---

### Post by QIII on 2016-02-09
Not much there.  If you watch it for a bit, is there anything that pops to the top with the same period as the disk activity light?

---

### Post by marsdenf on 2016-02-09
Iotop output changes very regularly once a second, and the hdd light blinks once a second or once in two seconds, more irregularly than iotop.   The top of iotop output changes from a process "init" to "[kworker/u8:0]" every second  with "[jbd2/sbd2-8]" showing at the top less often, every 40 secs approx.

---

### Post by QIII on 2016-02-09
I would say that init is probably the culprit, and it is likely running to do some sort of logging.

Do you have anything set to log something every second?

---

### Post by marsdenf on 2016-02-09
I vaguely remember installing something to log,  I think it was a bootlogger, but I forget the name of it.  How do I find out?

Toward the bottom of iotop output on my desktop there is " rsyslog [in:imsocks] " appearing briefly about every 5-10 seconds.

---

### Post by QIII on 2016-02-09
Try running

```
tail -f /var/log/syslog
``` and see if something is showing up every second.

---

### Post by marsdenf on 2016-02-09
here is the output from that code, I don't know how to interpret it:

```
marsdenf@marsdenf-P5Q-E:~$ tail -f /var/log/syslog
Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info> (eth0): DHCPv4 state changed renew -> renew
Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info>   address 192.168.0.10
Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info>   prefix 24 (255.255.255.0)
Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info>   gateway 192.168.0.1
Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info>   nameserver '64.59.135.135'
Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info>   nameserver '64.59.128.112'
Feb  9 15:22:25 marsdenf-P5Q-E dbus[383]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb  9 15:22:25 marsdenf-P5Q-E dbus[383]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  9 07:56:46 marsdenf-P5Q-E rsyslogd: message repeated 3 times: [ [origin software="rsyslogd" swVersion="7.4.4" x-pid="453" x-info="http://www.rsyslog.com"] rsyslogd was HUPed]
Feb  9 15:24:11 marsdenf-P5Q-E rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="453" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

---

### Post by QIII on 2016-02-09
Is the drive light blinking all day, or does it just have periods of activity?

---

### Post by marsdenf on 2016-02-09
I blinks whenever I look at it.   Seems like all the time

---

### Post by QIII on 2016-02-09
Run tail on syslog again for a bit.  Are you gettinv a lot of logging from network manager?

---

### Post by marsdenf on 2016-02-09
here is is output:```
marsdenf@marsdenf-P5Q-E:~$ marsdenf@marsdenf-P5Q-E:~$ tail -f /var/log/syslog
marsdenf@marsdenf-P5Q-E:~$: command not found
marsdenf@marsdenf-P5Q-E:~$ Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info> (eth0): DHCPv4 state changed renew -> renew
bash: syntax error near unexpected token `('
marsdenf@marsdenf-P5Q-E:~$ Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info>   address 192.168.0.10
bash: info: No such file or directory
marsdenf@marsdenf-P5Q-E:~$ Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info>   prefix 24 (255.255.255.0)
bash: syntax error near unexpected token `('
marsdenf@marsdenf-P5Q-E:~$ Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info>   gateway 192.168.0.1
bash: info: No such file or directory
marsdenf@marsdenf-P5Q-E:~$ Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info>   nameserver '64.59.135.135'
bash: info: No such file or directory
marsdenf@marsdenf-P5Q-E:~$ Feb  9 15:22:25 marsdenf-P5Q-E NetworkManager[838]: <info>   nameserver '64.59.128.112'
bash: info: No such file or directory
marsdenf@marsdenf-P5Q-E:~$ Feb  9 15:22:25 marsdenf-P5Q-E dbus[383]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
bash: syntax error near unexpected token `('
marsdenf@marsdenf-P5Q-E:~$ Feb  9 15:22:25 marsdenf-P5Q-E dbus[383]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb: command not found
marsdenf@marsdenf-P5Q-E:~$ Feb  9 07:56:46 marsdenf-P5Q-E rsyslogd: message repeated 3 times: [ [origin software="rsyslogd" swVersion="7.4.4" x-pid="453" x-info="http://www.rsyslog.com"] rsyslogd was HUPed]
Feb: command not found
marsdenf@marsdenf-P5Q-E:~$ Feb  9 15:24:11 marsdenf-P5Q-E rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="453" x-info="http://www.rsyslog.com"] exiting on signal 15.
Feb: command not found
marsdenf@marsdenf-P5Q-E:~$ 
marsdenf@marsdenf-P5Q-E:~$ 
```

looks like network manager is active

---

