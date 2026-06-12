---
title: "Service Unstable"
date: 2023-08-03
forum: General Help
---

### Post by amsnetms on 2023-08-03
Hello,

I have tested this on several ubuntu 22.04LTS servers (CLI only) and so far proving unstable.  I created a new service which runs a shell script to start up Palo Alto Networks globalprotect VPN client and auto-connect back to our data center.  The script loops every minute to ping an IP address inside the data center and in the event of failure, reconnect VPN client.  I've had several approaches with the code and so far it is unstable.  Sometimes it can be stable until I reboot and then it doesn't work.  The service or script is spooling up multiple instances of globalprotect client which makes it fail to connect to VPN anymore.  Here is the service file:
```
cat /etc/systemd/system/myVpn.service
[Unit]
Description=My Vpn Connection
Wants=network.target
After=syslog.target network-online.target

[Service]
Type=simple
ExecStart=/usr/local/bin/myvpn.sh
ExecStop=/bin/sh -c 'globalprotect disconnect'
Restart=on-failure
RestartSec=10
KillMode=process

[Install]
WantedBy=multi-user.target

The script is:

cat /usr/local/bin/myvpn.sh
#!/bin/bash

#Variables
ping_targets="x.x.x.x"
failed_hosts=""

#Start gp client vpn and log the event
globalprotect connect -p x.x.x.x -u xxxx

echo "myVpn.service: ## Starting globalprotect ##" | systemd-cat -p info

#Check connectivity every minute
while :

do

TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S')

echo "myVpn.service: ${TIMESTAMP} checking opmgr central reachable over vpn" | systemd-cat -p info

   ping -c 1 x.x.x.x > /dev/null
   if [ $? -ne 0 ]; then
      if [ "$failed_hosts" == "" ]; then
         failed_hosts="x.x.x.x"
      else
         failed_hosts="$failed_hosts, 'x.x.x.x'"
      fi
   fi

if [ "$failed_hosts" != "" ]; then
   globalprotect connect -p x.x.x.x -u xxxx
   echo "myVpn.service: ## Reconnecting due to packet loss ##" | systemd-cat -p info
fi

sleep 60

done

```

I removed usernames and IP addresses and replaced them with x for security reasons.  I appreciate any feedback or advise with this.  It's frustrating when I had the first test server stable all weekend long and yesterday it also lost vpn connection.  Is this better accomplished as a crontab job instead of a service?  

Thanks!

Christo

---

### Post by MAFoElffen on 2023-08-03
please go back to your original post and edit it to encapsulate the posted code within [noparse]```
 
```[/noparse] Tags... To follow Forums policy. Trying to keep you out of trouble.

I have a question on your script, and in changing it to test...

RE: man page ping
> 
If ping does not receive any reply packets at all it will exit with code 1. If a packet count and deadline are both specified, and fewer than count packets are received by the time the deadline has arrived, it will also exit with code 1. On other error it exits with code 2. Otherwise it exits with code 0.

If you followed your ping command with 
```

ping -c 1 xxx.xxx.xxx.xxx
exit_code=$? ## capture exit code

```
Then you could evaluate what that did a lot simpler...

But what may be a different perspective, and would prevent multiple instances of the VPN connection would be to capture the PID of the initiated VPN instance to a PID file, then check if that PID exists currently... If not, then load a new instance. Does that make sense to you? That way there is only one instance at a time...

You could do both. If ping fails, then check PID of instance. If PID exists (still), kill it before loading a new instance. If not, just load new instance.

---

### Post by deadflowr on 2023-08-03
> please go back to your original post and edit it to encapsulate the posted code 
I was passing by, so did it myself.

---

### Post by amsnetms on 2023-08-03
> **deadflowr said:**
> I was passing by, so did it myself.

Thank you for helping a noob :)

---

### Post by amsnetms on 2023-08-03
I messed something up because I disabled the customer myVpn service and rebooted the machine.  Next I attempted to run globalprotect vpn client manually but it fails.  This happens when multiple instances are running.  I can see two instances of "PanGPA start" which start the back-end globalprotect service.  The front-end client is command "globalprotect".  Here is a process command output:

```

root@amsmon1:~# ps -aux | grep palo
root         896  0.0  0.1 711604 22848 ?        Ssl  20:03   0:00 /opt/paloaltonetworks/globalprotect/PanGPS
postgres    1122  0.0  0.0 268300 16148 ?        Ssl  20:03   0:00 /opt/paloaltonetworks/globalprotect/PanGPA start
root        1395  0.0  0.0 276504 16092 ?        Ssl  20:04   0:00 /opt/paloaltonetworks/globalprotect/PanGPA start
root        2603  0.0  0.0   6608  2276 pts/0    S+   20:11   0:00 grep --color=auto palo

```

> **MAFoElffen said:**
> please go back to your original post and edit it to encapsulate the posted code within [nopaserse][/noparse] Tags... To follow Forums policy. Trying to keep you out of trouble.

I have a question on your script, and in changing it to test...

RE: man page ping

If you followed your ping command with 
```

ping -c 1 xxx.xxx.xxx.xxx
exit_code=$? ## capture exit code

```
Then you could evaluate what that did a lot simpler...

But what may be a different perspective, and would prevent multiple instances of the VPN connection would be to capture the PID of the initiated VPN instance to a PID file, then check if that PID exists currently... If not, then load a new instance. Does that make sense to you? That way there is only one instance at a time...

You could do both. If ping fails, then check PID of instance. If PID exists (still), kill it before loading a new instance. If not, just load new instance.

---

