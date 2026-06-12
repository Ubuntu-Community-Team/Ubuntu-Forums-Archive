---
title: "Unable to auto start service (SoftEther VPN) on Ubuntu Server 22.04"
date: 2022-05-26
forum: General Help
---

### Post by xkyzda on 2022-05-26
I am running Ubuntu 22.04 in a VMware Workstation VM (Host OS is Windows 11 Pro). 


I find that I have to manually start the Softether VPN by running "/etc/init.d/vpnserver start". 


I tried running "update-rc.d vpnserver defaults" to make it autostart after login to no avail.

I tried this guide,: [https://www.digitalocean.com/community/questions/softether-is-not-starting-after-reboot](https://www.digitalocean.com/community/questions/softether-is-not-starting-after-reboot)




However, the problem is when I go enable the service with
> sudo systemctl enable vpnserver.service



It gives me an error:


> update-rc.d: error: vpnserver Default-Start contains no runlevels, aborting


I tried 3 variations:


**#1**
"sudo nano /etc/init.d/vpnserver"


> 
#!/bin/sh
# chkconfig: 2345 99 01
# description: SoftEther VPN Server
sleep 10
DAEMON=/usr/local/vpnserver/vpnserver
LOCK=/var/lock/subsys/vpnserver
test -x $DAEMON || exit 0
case "$1" in
start)
$DAEMON start
touch $LOCK
;;
stop)
$DAEMON stop
rm $LOCK
;;
restart)
$DAEMON stop
sleep 3
$DAEMON start
;;
*)
echo "Usage: $0 {start|stop|restart}"
exit 1
esac
/etc/init.d/vpnserver start
exit 0








**#2 (with code below)**
"sudo nano /etc/systemd/system/vpnserver.service"

-- and--

**#3 (with code below)**
"nano /lib/systemd/system/vpnserver.service"


> 
[Unit]
Description=SoftEther VPN Server
After=network.target


[Service]
Type=forking
ExecStart=/usr/local/vpnserver/vpnserver start
ExecStop=/usr/local/vpnserver/vpnserver stop


[Install]
WantedBy=multi-user.target




Any ideas? Thanks!

---

