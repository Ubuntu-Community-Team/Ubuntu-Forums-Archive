---
title: "Need help with routing table after connecting cellphone as modem (PPP)"
date: 2008-02-08
forum: General Help
---

### Post by weblordpepe on 2008-02-08
Hello there. I need help. I am trying to set up my Nokia 3220 cellphone to act as a modem for my EEE. Hardware/drivers are all perfect. Configuring for ISP is not. 

I have tried two different methods, GUI (using KDE) and wvdial -however both are stuck. I would gladly accept any suggestions for either method:


**GUI METHOD (KDE):**
Using the GUI, its very straight forward to set up a regular dial-up modem. However there is one big problem: The prefix and suffix is requested in the wizard/menus, and added to the dial-string. 

Example:
Entering **1** as suffix, **2** as ISP number and **3** as suffix produces:[b]
ATD1,2,3[/b]
Now that presents a problem when I only want it to dial ***99#** because entering nothing as the prefix and suffix produces this crap:
**ATD,*99#,**

My phone won't connect to GPRS with those commas in there.

Question: Is there any way to make a dial-up ISP entry using the GUI which doesn't require the prefix/suffix?



**WVDIAL / TERMINAL METHOD:**
Ok so wvdial has found my modem, used it to dial, given me my IP and DNS address. The problem? The routing table. Whilst the PPP session is active, I cannot get Xandros to use the PPP session because I dont think its created the correct routing table entry.

Here's my routing table:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.6.6.6        0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
11.0.0.0        0.0.0.0         255.0.0.0       U     10     0        0 ath0
0.0.0.0         11.1.1.1        0.0.0.0         UG    10     0        0 ath0
```
The last two lines (ath0) are my EEE's wifi. Turning off the WIFI connection removes those two entries however it doesn't have any effect on getting my PPP to go.

The 10.6.6.6 is the PPP server on the other end of the connection.

Can anyone give me any pointers? I don't know how to use the 'route add' very well so I'm kinda stuck. I assume I need to add the PPP0 as the default route? I do not know how.

Contents of my /etc/wvdial.conf:[b]
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
; Modem Type = Analog Modem
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Username = fone
Stupid Mode = yes
Password = vod
Baud = 230400
Check Def Route = yes[/b]

Dislcaimer: I'm using Xandros with the EEE, not Ubuntu. It should be roughly the same tho.

---

### Post by georgevaccaro on 2008-02-15
I had the same problem, and your post partially helped me to solve it.  I didn't realize that the commas were the problem until I read your post.

Using the UI (not wvdial) go back to the connection settings and simply move the *99# to the prefix field from the number field.  This will dial it before the "," which worked for me like a champ.

I hope it works for you - I'm using an eee too (just got it today) so you should be good to go.

---

