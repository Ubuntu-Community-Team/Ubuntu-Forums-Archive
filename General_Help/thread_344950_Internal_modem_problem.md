---
title: "Internal modem problem"
date: 2007-01-23
forum: General Help
---

### Post by Quartlow on 2007-01-23
Dell dimension 3000
Fresh install of Dapper drake
Modem Intel 537EP Chipset

Followed 
[http://ubuntuforums.org/showthread.php?t=210405](http://ubuntuforums.org/showthread.php?t=210405)
and this
[https://help.ubuntu.com/community/DialupModemHowto/Intel537EP](https://help.ubuntu.com/community/DialupModemHowto/Intel537EP)

> root@janice-desktop:/home/janice# sudo bash /etc/init.d/537_boot start
error loading /etc/init.d/2.6.15-23-386/Intel537.ko
ERROR: Module Intel537 does not exist in /proc/modules

I'm about to lose my mind here, ](*,)  ](*,)    keep in mind I'm a noob so be very explicit giving instructions. Daon't assume I know anything :biggrin:

---

### Post by Quartlow on 2007-01-24
problem part solved, managed to get it on the net by using my network connection via networking card. got a everthing upgraded, for some reason its not passing the password on the dialup connection



Apparently its connecting, passing the username but not the password.

Any ideas? I know the password is right I can boot to windows and get it connected

And where is it hiding man pppd so I can see the error codes

```
janice@janice-desktop:~$ wvdial
--> WvDial: Internet dialer version 1.55
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+GCI=3D
AT+GCI=3D
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Modem initialized.
--> Sending: ATDT3307870020
--> Waiting for carrier.
ATDT3307870020
CONNECT 52000
--> Carrier detected.  Waiting for prompt.
Level 3 Comm nas40.2in1 UQKT2
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: mickleymouse
mickleymouse
Password:
--> Looks like a password prompt.
--> Sending: (password)
** Bad Password
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: mickleymouse
mickleymouse
Password:
--> Looks like a password prompt.
--> Sending: (password)
** Bad Password
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: mickleymouse
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Jan 24 20:06:27 2007
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 26689
--> Using interface ppp0
--> pppd: P&#65533;[05][08]
--> pppd: P&#65533;[05][08]
--> pppd: P&#65533;[05][08]
--> pppd: P&#65533;[05][08]
--> pppd: P&#65533;[05][08]
--> Disconnecting at Wed Jan 24 20:06:34 2007
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)
janice@janice-desktop:~$
```

---

