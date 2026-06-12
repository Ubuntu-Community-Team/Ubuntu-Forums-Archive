---
title: "modem not responding in my laptop"
date: 2006-12-15
forum: General Help
---

### Post by housam on 2006-12-15
G'day all, 
Can I get a help in this matter? 
Trying to connect to the internet using a dial-up modem, I did the following:
-downloading & unpacking the SLMODEMD.gcc4 .
- copying the slmodemd to /usr/sbin then,

housam@housam-laptop:~$ sudo chmod +x /usr/sbin/slmodemd
housam@housam-laptop:~$ sudo modprobe snd-intel8x0m
housam@housam-laptop:~$ sudo slmodemd -c EGYPT --alsa snd-intel8x0m hw:0,6 

I,ve got the following:> Usage: slmodemd [option...] <device>
Where 'device' is name of modem device (default `/dev/slamr0')
  and 'option' may be:
  -h, --help            this usage
  -u, --usage           this usage
  -v, --version         show version and exit
  -c, --country=VAL     default modem country name (default `EGYPT')
      --countrylist     show list of supported countries
  -a, --alsa            ALSA mode (see README for howto)
  -g, --group=VAL       Modem TTY group (default `uucp')
  -p, --perm=VAL        Modem TTY permission (default `0660')
  -r, --ringdetector    with internal ring detector (software)
  -n, --nortpriority    run with regular priority
  -s, --shortbuffer     use short buffer (4 periods length)
  -d, --debug=VAL       debug level (default `0')
  -l, --log=VAL         logging mode (default `5')
housam@housam-laptop:~$ sudo slmodemd --alsa -c EGYPT hw:0,6
SmartLink Soft Modem: version 2.9.11 Mar 13 2006 18:27:33
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `hw:0,6' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.


and in another terminal I configured wvdial:
housam@housam-laptop:~$ sudo wvdialconf /etc/wvdial.conf
and got the following:

> Password:
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31
Modem Port Scan<*1>: S32  S33  S34  S35  S36  S37  S38  S39
Modem Port Scan<*1>: S40  S41  S42  S43  S44  S45  S46  S47
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"


and editing wvdial.conf:
housam@housam-laptop:~$ sudo gedit /etc/wvdial.conf
and running sudo wvdial
got the following:
> --> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT07770777
--> Waiting for carrier.
ATDT07770777
CONNECT 50667
--> Carrier detected.  Waiting for prompt.
** Welcome **
ascend%
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend%
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend%
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend%
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend%
--> Hmm... a prompt.  Sending "ppp".
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Fri Dec 15 15:47:47 2006
--> Pid of pppd: 6906
--> Using interface ppp0
--> Disconnecting at Fri Dec 15 15:48:17 2006
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd 
man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ascend%
ascend%
ascend%
ascend%
ascend%
ascend%
ascend%
ascend%
ascend%
ascend% ATZ
Unknown command
ascend%
--> Sending: ATQ0
ATQ0
Unknown command
ascend%
--> Re-Sending: ATZ
ATZ
Unknown command
ascend%
--> Modem not responding.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ascend%
ascend%
ascend%
ascend%
ascend%
ascend%
ascend%
ascend%
ascend%
ascend%
ascend%
ascend% ATZ
Unknown command
ascend%
--> Sending: ATQ0
ATQ0
Unknown command
ascend%
--> Re-Sending: ATZ
ATZ
Unknown command
ascend%
--> Modem not responding.
--> Disconnecting at Fri Dec 15 15:48:41 2006



Now what is the problem? and what to do??
thanks for the help

---

### Post by housam on 2006-12-16
Now i'm online from my laptop. There was an error editing wvdial.conf and I fixed it.

Thanks for the FORUM

---

### Post by nsleiman on 2006-12-19
hi Housam,
you are the first guy i know got the winmodem working, can u please tell me what kind of laptop u have? it might be helpful for me :)

---

### Post by housam on 2006-12-22
> **nsleiman said:**
> hi Housam,
you are the first guy i know got the winmodem working, can u please tell me what kind of laptop u have? it might be helpful for me :)

I'm using a Laptop 
HP compaq nx7400, dual core T2500 2.00GHz , 100 G HDD, 1024 Mb RAM,

I can help if you stuck in a step or something.

Good luck

---

