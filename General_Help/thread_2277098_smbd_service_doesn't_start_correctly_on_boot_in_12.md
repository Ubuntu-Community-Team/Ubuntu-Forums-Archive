---
title: "smbd service doesn't start correctly on boot in 12.04 or 14.04"
date: 2015-05-06
forum: General Help
---

### Post by Jive Turkey on 2015-05-06
For years I've had to restart the service manually after rebooting but I'm determined to get it working properly on my headless server box. I've seen this same behavior on both desktop and server and also on an ubuntu based mint system. 
After a fresh boot the service is purported to be running according to initctl, it has a pid last I checked was #631, but the service isn't available to any clients. PID 631 seems kind of low to me, like its starting too early before dependencies are started.

So far I have tried changing the default rc*.d symlinks from S20smbd to S99smbd. It didn't seem to make a difference. All I can find in the logs for samba is messages about failing to connect to cups which is not installed and I have seen the same behavior on desktop machines that do have cups running.

I have also tried adding the command "/etc/init.d/smbd restart" to /etc/rc.local. Also no change, the only way I can get it going is to ssh into the box and restart the service myself :(.

---

### Post by bab1 on 2015-05-06
> **Jive Turkey said:**
> For years I've had to restart the service manually after rebooting but I'm determined to get it working properly on my headless server box. I've seen this same behavior on both desktop and server and also on an ubuntu based mint system. 
After a fresh boot the service is purported to be running according to initctl, it has a pid last I checked was #631, but the service isn't available to any clients. PID 631 seems kind of low to me, like its starting too early before dependencies are started.

So far I have tried changing the default rc*.d symlinks from S20smbd to S99smbd. It didn't seem to make a difference. All I can find in the logs for samba is messages about failing to connect to cups which is not installed and I have seen the same behavior on desktop machines that do have cups running.

I have also tried adding the command "/etc/init.d/smbd restart" to /etc/rc.local. Also no change, the only way I can get it going is to ssh into the box and restart the service myself :(.
How is the service "unavailable"?  The smbd daemon can be running and you can still have problems.  Reboot the system and post the output of this command```
pgrep -l mbd
```
I get this```
pgrep -l mbd
651 smbd
668 smbd
2226 nmbd

```... note the PID's for the 2 smbd daemons.

What do you get from the /var/log/samba/log.smbd?  Post the output of this command```
tail /var/log/samba/log.smbd
```

---

### Post by Jive Turkey on 2015-05-08
> **bab1 said:**
> How is the service "unavailable"?  The smbd daemon can be running and you can still have problems.  Reboot the system and post the output of this command```
pgrep -l mbd
```
I get this```
pgrep -l mbd
651 smbd
668 smbd
2226 nmbd

```... note the PID's for the 2 smbd daemons.

What do you get from the /var/log/samba/log.smbd?  Post the output of this command```
tail /var/log/samba/log.smbd
```

The service is unavailable in the sense that clients can't connect to it until I ssh to the server and reload the service. You are correct, smbd is running, and having problems after rebooting. 
/var/log/samba/log.smbd is filled with entries like this:
```
[2015/05/08 13:28:32.263158,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/05/08 13:28:32.263329,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
```

pids for smbd/nmbd are in the 600's fresh after booting, after reloading the service they are in the 2000's.

Additionally, I have tried disabling startup entries in rc*.d and I find that it starts at boot anyway. Something, somewhere starts it too early in the bootup sequence and I don't even know how to disable/modify it. grrr.

---

### Post by bab1 on 2015-05-08
> **Jive Turkey said:**
> The service is unavailable in the sense that clients can't connect to it until I ssh to the server and reload the service. You are correct, smbd is running, and having problems after rebooting. 

The problem is not with either smbd or nmbd daemons.  The problem most likely is with the configuration or the network naming (hosts and netbios)  services.
> 

/var/log/samba/log.smbd is filled with entries like this:
```
[2015/05/08 13:28:32.263158,  0] ../source3/printing/print_cups.c:151(cups_connect)
  Unable to connect to CUPS server localhost:631 - Bad file descriptor
[2015/05/08 13:28:32.263329,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
```


This is normal if you are not using Samba to share printer information.  I don't use Samba to share my printers.  They are networked HP printers and use IPP for location.
> 

pids for smbd/nmbd are in the 600's fresh after booting, after reloading the service they are in the 2000's.

This also is normal.
> 
Additionally, I have tried disabling startup entries in rc*.d and I find that it starts at boot anyway. Something, somewhere starts it too early in the bootup sequence and I don't even know how to disable/modify it. grrr.
Ubuntu hasn't used Sys V Init for quit a while.  Your assumption is incorrect.  The only thing that Samba needs to know is that the network is up.  This is all handled by Upstart at the present time if you are using Ubuntu 14.10 or less.  In Ubuntu 15.04 the init system has changed to systemd.

So if you are using a version of Ubuntu that is less than 15.04 it is safe to say that if you see smbd and nmbd running then the daemons where launched with network services and are running correctly.

Let's start with a little simple diagnosis.  Reboot the system and without restarting smbd, please post the output of these commands```

cat /etc/samba/smbd.conf

smbtree -d3

```

---

### Post by Jive Turkey on 2015-05-09
First, thank you so much for your help with this.
here's the output of "testparm -s" so you don't have to sift through the commented default values:
```
:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[Music]"
Processing section "[Packages]"
Processing section "[Backups]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = WORKGROUP
        server string = %h server (Samba, Ubuntu)
        interfaces = lo, br0
        bind interfaces only = Yes
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = dns, lmhosts, wins, bcast
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        hosts allow = 127.0.0.0/8, 192.168.1.0/24
        hosts deny = 0.0.0.0/0

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = No

[Music]
        comment = Music
        path = /srv/Music
        read only = No
        browseable = No

[Packages]
        comment = Software Store
        path = /srv/Packages
        read only = No

[Backups]
        comment = Backup Share
        path = /srv/Backups
        read only = No
        browseable = No

```

I think I need to turn my attention to this upstart thing. I know I definitely need smbd to start well after dnsmasq which does dns and dhcp on my network. I suspect this is the problem and it will be complicated by the fact that dnsmasq doesn't have an upstart conf in /etc/init/ yet. 

This is on 14.04 server and it doesn't have smbclient installed so I can't run smbtree.

---

### Post by bab1 on 2015-05-09
> **Jive Turkey said:**
> First, thank you so much for your help with this.
here's the output of "testparm -s" so you don't have to sift through the commented default values:

If you want my help you have to respond to what I ask for, not what you think I need.  Post the output for the commands I listed.
> 
I think I need to turn my attention to this upstart thing. I know I definitely need smbd to start well after dnsmasq which does dns and dhcp on my network. I suspect this is the problemYour suspicions are not correct.  Samba does not directly use DNS and really doesn't care what the servers IP address is.  The hosts file is as close as it gets to dns style name services.  Samba uses NETBIOS for browsing the network for SMB resources (shares).

My advice is to leave the Upstart scripts alone.  It appears at first blush that your problem is related to a failure to create a valid Browse List.  When I see the info I asked for I will know more.

[COLOR="#0000FF"]Edit:  Add the package for smbclient then.  I believe that is cifs-utils.[/COLOR]

---

### Post by Jive Turkey on 2015-05-09
I found the solution here [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/951087](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/951087)

Thanks for pointing me toward the upstart configs BAB1, even though you had some different ideas about the problem. I think you are right that it wasn't the name resolution, but the bridge I have (wlan0+eth0=>br0). The box is a wireless AP too! I changed /etc/init/smbd.conf so that now the upstart job waits for br0 specifically to be up. I rebooted a couple of times to be sure and clients can now connect without needing to bounce the smbd service manually.

---

