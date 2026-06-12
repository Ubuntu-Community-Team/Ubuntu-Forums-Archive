---
title: "Vodafone MCC"
date: 2005-10-28
forum: General Help
---

### Post by myha on 2005-10-28
Hi all!

I'm having a little problem with connecting to internet with Vodafone Mobile Connect Card, so I was wondering if smbdy can kelp me with it....

I have card on /dev/ttyS16, ubuntu recognises it and I can connect, but it disconnects in about 30 seconds... I dont get IP or whatever from ISP...

Here is the connection log:
```

GNOME PPP: Connecting...
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.54.0
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: AT+CGDCONT=1,"IP","apn"
GNOME PPP: STDERR: AT+CGDCONT=1,"IP","apn"
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM1L3DT*99#
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT*99#
GNOME PPP: STDERR: CONNECT 57600
GNOME PPP: STDERR: --> Carrier detected.  Waiting for prompt.
GNOME PPP: STDERR: ~[7f]}#@!}!}5} }<}!}$}&@}#}$@#}%}&_8^G}"}&} } } } }'}"}(}"[01]t~~~
GNOME PPP: STDERR: --> PPP negotiation detected.
GNOME PPP: STDERR: --> Starting pppd at Fri Oct 28 09:36:50 2005
GNOME PPP: STDERR: --> pid of pppd: 12358
GNOME PPP: STDERR: --> Using interface ppp0
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> pppd: ATZ
GNOME PPP: STDERR: --> Disconnecting at Fri Oct 28 09:37:24 2005
GNOME PPP: STDERR: --> The PPP daemon has died: PPP negotiation failed (exit code = 10)
GNOME PPP: STDERR: --> man pppd explains pppd error codes in more detail.
GNOME PPP: STDERR: --> I guess that's it for now, exiting
GNOME PPP: STDERR: --> The PPP daemon has died. (exit code = 10)

```

And here is output from /var/log/messages:
```

Oct 28 09:36:51 localhost pppd[12358]: pppd 2.4.3 started by root, uid 0
Oct 28 09:36:51 localhost pppd[12358]: Using interface ppp0
Oct 28 09:36:51 localhost pppd[12358]: Connect: ppp0 <--> /dev/ttyS16
Oct 28 09:36:54 localhost pppd[12358]: appear to have received our own echo-reply!
Oct 28 09:36:54 localhost pppd[12358]: Remote message: TTP Com PPP - Password Verified OK
Oct 28 09:36:54 localhost pppd[12358]: PAP authentication succeeded
Oct 28 09:37:23 localhost pppd[12358]: appear to have received our own echo-reply!
Oct 28 09:37:24 localhost pppd[12358]: IPCP: timeout sending Config-Requests
Oct 28 09:37:24 localhost pppd[12358]: Connection terminated.
Oct 28 09:37:24 localhost pppd[12358]: Exit.

```

Does anyone know what could be wrong?

Thanks,
Miha

---

