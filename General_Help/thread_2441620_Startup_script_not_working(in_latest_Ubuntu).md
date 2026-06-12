---
title: "Startup script not working(in latest Ubuntu?)"
date: 2020-04-25
forum: General Help
---

### Post by aboka on 2020-04-25
hi, am a newbies in LInux as using Windows most of times. hv follow an online guide to setup SoftEther with Ubuntu and all is working fine until the system is reboot - so i assume the startup script is not working some how

here is the guide -
Create a systemd service:

Create the file /lib/systemd/system/vpnserver.service

$ sudo vi /lib/systemd/system/vpnserver.service

And put the following content within it:
[Unit]
Description=SoftEther VPN Server
After=network.target


[Service]
Type=forking
ExecStart=/usr/local/vpnserver/vpnserver start
ExecStop=/usr/local/vpnserver/vpnserver stop


[Install]
WantedBy=multi-user.target

Then i save the vi using :qw and open it again to make sure the code is in there

One thng i suspect is bcoz of there is different in the Ubuntu's version. The guide is for an older version while im using the latest 19.10 version 

Thanks in advance for your help.

Cheers,

---

### Post by aboka on 2020-04-25
hi, found out the reason and fix it already :) its bcoz its missing the systemctl enable vpnserver

thanks,

---

