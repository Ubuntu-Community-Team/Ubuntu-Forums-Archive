---
title: "Problem with Dialup #777.. Pleeeeease HELP!"
date: 2006-07-30
forum: General Help
---

### Post by bit-stalker on 2006-07-30
Hi..... everyone...

i am running Ubuntu BB and i am using a "standard external modem" connected t com1. This is a modem built inside my CDMA phone and i connect the whole unit to the com1 through RS232 cable.

i can connect to the net from windows xp through the standard modem drivers.... and the duialup number i have to use is #777.

i tried wvdial / kppp / Gnome-ppp and i still cant get the dialup to be working

if i dial a standard number which my internet service provider also supports i can see the it's dialing on the phones LCD (ASYC Call... but in fax mode 14.4x) and does not connect coz i my line is CDMA

i did the same in winXP and same problem... can't connect to generel numbers.

but when i dial #777..... this is what i get in the terminal and log files. 

root@ubuntu:~# wvdial --config /etc/ppp/peers/wvdial.conf
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT#777
--> Waiting for carrier.


similar error gnome-ppp

kppp will not even try sometimes and it dies. probably i set the config wrong

since dialing a general number.... the modem dialouts to connect but will not since the network does not support....

dialling #777 there is nothing diaplyed on the phones LCD as well.

Dialing from windows XP the phone diaplays that i am dialing (ASYNC CALL) and it shows it connects and the duration.

pleeeeeeeeeeeeeeeeease pleeeeeeeeeeeeeeease... if there is anybody who can at least suggest something that i can tryout it will be a big help.

---

### Post by jos meijer on 2006-09-27
As far as I understand your problem, it is a GPRS od UMTS modem.
Thus it needs an APN name to hook up to this network, and maybe also a DNS adress.
You should get these from your provider, and ususlly these are stored somewhere in the phone settings menu too.
Yoy can pass the string to most modems by adding the modemstring
AT+CGDCONT=1,"IP","apn"
in which apn should be replaced by the string typical to your provider.

There is another way, that is to choose the relevant profile from your phone but as we use other numbers in the Netherlands I cant but tel you how it works here.

Profiles are stored in the phone, numbered 0-9
Normal GPRS call in Holand is *99#
call by profile is *99**N#  where N is 0-9

---

