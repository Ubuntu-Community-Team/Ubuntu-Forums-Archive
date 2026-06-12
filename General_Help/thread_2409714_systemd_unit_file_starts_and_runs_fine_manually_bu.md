---
title: "systemd unit file starts and runs fine manually but not on bootup"
date: 2019-01-05
forum: General Help
---

### Post by ken35 on 2019-01-05
This example is running on a Raspberry P13B with Ubuntu Mate 18.04 running at the multi-user target (no gui).  The script runs fine by hand.  The .service runs fine if I start it manually (systemctl start protonvpn).  I have enabled it but when I reboot the computer it does not run.  Here are the specifics:

protonvpn.service```
ken@taylor21:~$ cat /etc/systemd/system/protonvpn.service 
[Unit]
Description=Connect to ProtonVPN
Requires=network.target

[Service]
Type=simple
ExecStart=/usr/sbin/protonvpn.sh

[Install]
WantedBy=multi-user.target
```and the script is```
ken@taylor21:~$ cat /usr/sbin/protonvpn.sh 
#!/bin/bash
#
# This script will launch the Proton VPN and relaunch if it drops
#
echo >> /var/log/protonvpn.log
echo >> /var/log/protonvpn.log
echo launching vpn  `date` >> /var/log/protonvpn.log

pvpn -d  | tee -a /var/log/protonvpn.log
pvpn --cc US  | tee -a /var/log/protonvpn.log

while [ 0 -lt 1 ]
   do
# Check for the presence of the tunnel
   ifconfig tun0 > /dev/null
#   ifconfig tun0 >> /var/log/protonvpn.log
if [ $? -eq 0 ]; then
     sleep 5
   else 
     echo  >> /var/log/protonvpn.log
     echo `date` " vpn down, restarting" >> /var/log/protonvpn.log       
     pvpn -d | tee -a /var/log/protonvpn.log
     pvpn --cc US | tee -a /var/log/protonvpn.log
   fi
done

exit
```After a reboot I see ```
ken@taylor21:~$ systemctl status protonvpn
&#9679; protonvpn.service - Connect to ProtonVPN
   Loaded: loaded (/etc/systemd/system/protonvpn.service; enabled; vendor preset: enabled)
   Active: inactive (dead)
```but after manually starting the service```
ken@taylor21:~$ systemctl status protonvpn
&#9679; protonvpn.service - Connect to ProtonVPN
   Loaded: loaded (/etc/systemd/system/protonvpn.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2019-01-04 18:37:48 EST; 4s ago
 Main PID: 1303 (protonvpn.sh)
   CGroup: /system.slice/protonvpn.service
           &#9500;&#9472;1303 /bin/bash /usr/sbin/protonvpn.sh
           &#9500;&#9472;1393 bash /usr/local/bin/pvpn --cc US
           &#9500;&#9472;1394 tee -a /var/log/protonvpn.log
           &#9500;&#9472;1433 bash /usr/local/bin/pvpn --cc US
           &#9500;&#9472;1434 bash /usr/local/bin/pvpn --cc US
           &#9500;&#9472;1435 tr   @
           &#9500;&#9472;1436 bash /usr/local/bin/pvpn --cc US
           &#9500;&#9472;1437 wget --header x-pm-appversion: Other --header x-pm-apiversion: 3 --header Accept: application/vnd.protonmail.v1+json -o /dev/null --timeout 20
           &#9492;&#9472;1438 tee /root/.protonvpn-cli/.response_cache

Jan 04 18:37:48 taylor21 systemd[1]: Started Connect to ProtonVPN.
Jan 04 18:37:48 taylor21 protonvpn.sh[1303]: Disconnecting...
Jan 04 18:37:49 taylor21 protonvpn.sh[1303]: [#] Disconnected.
Jan 04 18:37:50 taylor21 protonvpn.sh[1303]: [#] Current IP: 99.99.99.99
Jan 04 18:37:51 taylor21 protonvpn.sh[1303]: Fetching ProtonVPN servers...
```
I have found a lot of pages discussing this same issue. I have tried various "fixes" such as changing the Type (it was initially oneshot), changing the WantedBy (to default.target) but I have not found a solution. Based on some feedback on linuxquestions.org I tried changing the [Unit] to ```
[Unit]
Description=Connect to ProtonVPN
After=network.target and
[Unit]
Description=Connect to ProtonVPN
Wants=network-online.target
After=network-online.target
``` but the results were the same.  Upon reviewing the log created by the script it does not appear that the script even started. 

Is multi-user.target a predecessor to network.target perhaps?  I do not really care when it fires off as long as the network is available. Is there a better WantedBy to use?  default.target did not do the trick.  Any suggestons?

TIA,

Ken

---

