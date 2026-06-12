---
title: "can't syncronize ntp"
date: 2014-08-11
forum: General Help
---

### Post by aviv2 on 2014-08-11
hi guys, i have server 2012 with ntp service,
on ubuntu if have configured /etc/ntp.conf , i have added my server
and i can see it with the command  ntpq -p

     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 server2012dom.a .LOCL.           1 u   47   64  377    0.408    0.872   8.676

i have tried 
sudo ntpdate -u 192.168.16.207
sudo ntpdate -s 192.168.16.207

restart the service and reboot the computer
the date remain the same as he was,
any solution?
10x

---

### Post by ian-weisser on 2014-08-12
Try it with the -d flag for debugging mode.
Try it without the -s flag so output is to the screen instead of log.

---

### Post by SeijiSensei on 2014-08-12
You also need to write the timestamp to the hardware clock after updating.  NTP only updates the system time, not the hardware clock.  To do that, run the command
```
sudo hwclock --systohc
```
after running ntpdate.

If you run ntpdate and then use the "date" command, is the time updated?  If so, then the problem is the hardware clock.

---

### Post by nerdtron on 2014-08-12
```
sudo ntpq -c lpeer
```
Show which NTP servers the machine is contacting. * symbol before the server means the local machine is currently syncing on this server.

```

ntpdate ntp_server_IPaddress
```
If the time difference from an NTP server to your local machine is too great (e.i. more than 30 mins) ntp service can take a long time to synchronize their times.
To synchronize quickly, use ntpdate.


Stop the ntp service, because you can't use ntpdate while ntp service is running.
```
sudo service ntp stop 
```
Run ntpdate at least 3 times and you'll see that time adjustment it made.
```

ntpdate ntp_server_IPaddress
```
Run the ntp service again
```
sudo service ntp start
```
After a few minutes, try checking the ntp peer on which your machine is synced.
```
sudo ntpq -c lpeer
```

---

### Post by HermanAB on 2014-08-12
Howdy,
If the time difference between the computer and the NTP server is very different, then the NTP client will refuse to change the clock.  The ntpdate command however doesn't have any such protection.

---

### Post by aviv2 on 2014-08-13
the main server that run ntp is server 2012 running on vmware so how can if fix  hardware clock problem?
the server date and time is exact as the physical computer he has installed.
when i syncronize xp ,7 or any microsoft vmware with the server there is no problem, its only on ubuntu, i have only just one ubuntu that sync as exact time as my real machine.

i have typed the command
sudo hwclock --systohc



i have turn of the UTC on /etc/default/rcS , still the saem

---

### Post by SeijiSensei on 2014-08-13
As I asked earlier
> If you run ntpdate and then use the "date" command, is the time updated?

---

### Post by SeijiSensei on 2014-08-13
As I asked earlier
> If you run ntpdate and then use the "date" command, is the time updated?

Is UDP port 123 open on all these machines?  Firewalls?

---

### Post by aviv2 on 2014-08-21
i can't understand the syntax ntpdate date, how?
there is no firewall on the server , on windows xp it works.

---

### Post by nerdtron on 2014-08-21
ntpdate syntax?

"sudo ntpdate ntp_server"

ntp_server can be URL like ntp.ubuntu.com or IP address of an NTP server. The ntpdate command can only be ran when the ntp service is stopped. See my post #4.

---

### Post by SeijiSensei on 2014-08-21
> **aviv2 said:**
> i can't understand the syntax ntpdate date, how?

```

[Seiji@GhostWorld ~]$ sudo ntpdate 0.centos.pool.ntp.org
21 Aug 13:30:39 ntpdate[31482]: adjust time server 199.102.46.75 offset -0.003638 sec
[Seiji@GhostWorld ~]$ date
Thu Aug 21 13:30:49 EDT 2014

```

---

