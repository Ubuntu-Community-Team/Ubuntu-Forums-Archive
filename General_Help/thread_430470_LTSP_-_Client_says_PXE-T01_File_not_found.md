---
title: "LTSP - Client says PXE-T01: File not found"
date: 2007-05-02
forum: General Help
---

### Post by NTBlade on 2007-05-02
Hi everyone,

I've just installed Ubuntu Server 7.04 and followed the instructions here:
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall) to install the server.
I'm using Windows Server DHCP so followed the instructions here:
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP)

When I try to boot a client, the client picks up an IP, and Gateway  Address and then tries to boot but I get the following message:

TFTP.
PXE-T01: File not found
PXE-E3B: TFTP Error - File not found.

netstat -apn | grep ":69 "  gives:
udp        0      0 0.0.0.0:69              0.0.0.0:*                          3871/inetd
so I guess xinetd will start it as required??

I've googled, searched the forums here and played with the DHCP options settings but I still can't boot.

Can anyone help me with this please?

Many thanks
NTB
8o)

---

### Post by smhickel on 2007-05-03
The key for us was the "filename "ltsp/i386/pxelinux.0" was changed from "filename "/ltsp/i386/pxelinux.0".

Best way to ts was to start a tftp client on another box. Then tftp the pxelinux.0 file from the server to the client. Only worked when syntax was "ltsp/i386" and not /ltsp/i386.

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.150 192.168.1.155;
  option domain-name "yourdomainhere";
  option domain-name-servers 192.168.1.50;
  option broadcast-address 192.168.1.255;
  option routers 192.168.1.69;
  option subnet-mask 255.255.255.0;

 
  filename "ltsp/i386/pxelinux.0";
  option root-path "/opt/ltsp/i386";
}

---

### Post by NTBlade on 2007-05-07
Thanks for the reply,
Still no luck.
The full path to pxelinux.0 is actually /opt/ltsp/i386/boot/pxelinux.0

Ive tried:
Root Path - /opt/ltsp/i386
Bootfile Name - boot/pxelinux.0 and /boot/pxelinux.0 and many other combinations but still no luck.

Any ideas?  (Remeber I'm using windows server DHCP)

Thanks
N

---

### Post by NTBlade on 2007-05-07
OK Clients now booting.
2003 Server DHCP Server Client Reservation is now:

017 Root Path - /opt/ltsp/i386
067 Bootfile Name - /i386/boot/pxelinux.0

However I can't login!

Any clues?

Thanks

---

### Post by smhickel on 2007-05-07
"...can't login..."

I take it that the pxe client gets a login screen gui (graphical user interface) and when you put in your user name and password it returns to the username and password screen without success?

DO you have AD integration or are you using PAM or NIS or LDAP?

I would load webmin ([www.webmin.com](www.webmin.com)) on the machine and then add several users and passwords under system (in webmin). Use the debian download of webmin.

Log into webmin as your system user and password (one you used when you installed ubuntu).

Make sure you know which users are setup and what their passwords are...

Try logging in again. 

Steve

---

### Post by NTBlade on 2007-05-08
Thanks for the reply,

I have an MS Small Business Server doing DHCP so, Yes I'm running AD but I'm not trying to authenticate against AD, LDAP or anything else.  This is simply an experiment to see if I can get this to work for a friend I'm helping.  They have a server on which I want to install Ubuntu server running LTSP for a thin client internet terminal.  The server will also run freeradius, LAMP, phpmyadmin, phpmyprepaid.  You probably guessed that the server is in a hotel.  :-)

The only user on the system is myself.  I can log on locally just fine.
Do you have to create separate users for LTS access?

Thanks
N

---

