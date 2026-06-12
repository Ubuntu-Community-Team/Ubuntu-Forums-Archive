---
title: "[SOLVED] How to Use W810i modem in Kubuntu."
date: 2008-04-16
forum: General Help
---

### Post by kumarkrishnan on 2008-04-16
Hi,
  I want to use my W810I modem with Kubuntu using USB cable comes along with it.
  Please guide me.
With Thanks,
KK

---

### Post by ibuclaw on 2008-04-16
Do you mean using your phone as an internet access point for KUbuntu?

There is a feature called wvdial in Ubuntu.

And all you need to do is edit a config file to match the settings of your phone.
```
 sudo gedit /etc/wvdial.conf 
```
And add details such as Modem, Phone, Password, etc.

Sorry, I can't give full details, as I've never tried it before.

[EDIT]
Found a site in spanish about the subject.
[Here is the google translation into english.]("http://translate.google.com/translate?hl=en&sl=es&u=http://www.cesarius.net/wvdial-conecta-tu-movilcelular-a-internet-facil-y-rapido-en-ubuntulinux/&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dhttp://www.cesarius.net/wvdial-conecta-tu-movilcelular-a-internet-facil-y-rapido-en-ubuntulinux/%26hl%3Den%26sa%3DG")

Here is another site that might help
[http://www.williambrownstreet.net/wordpress/?p=103](http://www.williambrownstreet.net/wordpress/?p=103)

Regards
Iain

---

### Post by kumarkrishnan on 2008-04-17
Hi,
  Thanks for your links. I will try and update.

---

### Post by kumarkrishnan on 2008-05-21
Got succeded. Find the steps below.


Find below the steps how I got GPRS connection with my W810I using wvdial.
Note: {} - command
Step 1: Open Terminal.

Step 2: type {sudo wvdialconfig} and enter.
Find the modem type with the line contains &#8220;/dev/ttyACM0&#8221; in W810I.

Step 3: edit wvdial.conf with vi editor or known editor with root permission as below

[Dialer Defaults]

Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT = 1,"IP","Type your access point name"
Modem Type = USB Modem
ISDN = 0
Baud = 460800
Phone = Type your Dialup number (contact your service provider looks like *99# or *99****5#)
Modem = /dev/ttyACM0
Username = Type your username (Contact your service provider)
Password = Type your password (Contact your service provider)
Stupid Mode = Yes 
New PPPD = Yes

Step 4: type {sudo wvdial} and enter. Typically as below

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT = 1,"IP","xyz"
AT+CGDCONT = 1,"IP","xyz"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!}!} }8}#}$@#}(}"}'}"}"}&} } } } }%}&[07]Y[02]$\8~
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Tue Apr 22 20:42:36 2008
--> Pid of pppd: 3372
--> Using interface ppp0
--> local IP address **.*.***.***
--> remote IP address **.**.**.**
--> primary DNS address ***.***.***.** (first DNS address)
--> secondary DNS address ***.***.***.*** (Second DNS number)

Step 5 : Find the DNS address and notedown it. Typically two numbers. Not local IP address and
remote IP address.
Step 6 : press ctrl + c.
Step 7 : Edit or create (in case not available) /etc/resolv.conf and add below lines.

nameserver first DNS address
nameserver second DNS address

Step 8 : {sudo wvdial} and enter. (Terminal must not be closed until browsing completed)

Step 9 : In another terminal type {ping www.google.com} and enter. Wait for reply.

Step 10:If GPRS connection is availabl, But, still there is no response. Then add below lines in /etc/ppp/peers/options.
noauth (Usually This will be there)
replacedefaultroute (Add it before end of the file. Required only if Firefox / browser not responding after GPRS got connected)

Step 11: Press ctrl+c to disconnect the connection.
By,
KK

---

### Post by kumarkrishnan on 2008-06-15
Hi,
  I got gprs connected with UBUNTU and I was using it for past one month. Suddenly from past two days it is not working. I tried 1. GPRS settings change. 2. DNS number verified and changed. 3. Wvdial.conf creation from "wvdialconf". 4. Fire fox settings checked. 5. Checked in vista and working there. 6. Ubuntu, reinstalled and followed all the procedure as early.

The main problem is, GPRS is getting connected. But, could not able to browse in fire fox or ping [www.google.com](www.google.com) in terminal.

Please provide me some solution.
With advanced Thanks,
Kumar

---

### Post by kumarkrishnan on 2008-06-16
Hi,
   Now it is working. After trial and error method I found that one of the control string in wvdial.conf was missing.
KK

---

### Post by prabath_fun on 2008-06-18
Thanks. Works well in Ubuntu 8.04.
Prabath

---

