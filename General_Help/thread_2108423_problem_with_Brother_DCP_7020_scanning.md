---
title: "problem with Brother DCP 7020 scanning"
date: 2013-01-24
forum: General Help
---

### Post by lunarsurface on 2013-01-24
I've been trying to get this thing working with no luck.

lsusb shows:

```
Bus 001 Device 005: ID 04f9:0183 Brother Industries, Ltd DCP-7020
```And it will print fine

I have brscan2 installed:

```
dpkg -l | grep Brother
ii  brscan-skey                            0.2.4-0                                             Brother Linux scanner S-KEY tool
ii  brscan2:i386                           0.2.5-1                                             Brother Scanner Driver
rc  brscan3                                0.2.11-5                                            Brother Scanner Driver
```I tried with the 64 bit package and it didn't work then ether

Added this to /lib/udev/rules.d/40-libsane.rules

```
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="0183", ENV{libsane_matched}="yes"
```


```
brscan-skey -l

 DCP-7020          : brother2:bus7;dev1  : USB                  Active

```


Any suggestions?

---

### Post by gifford on 2013-01-24
Does Xsane recognize the device?

---

### Post by lunarsurface on 2013-01-24
no, xsane, and scanimage both do not recognise a scanner is connected. They will work with my other scanner without issue.

---

### Post by gifford on 2013-01-24
I'm stumped! It seems like you are doing what Brother recommends. My only question now would be about the scan-key-tool install. Have you done all of the required set up? I have never used the driver before so am not familiar with how to set it up. It does appear that the scan tool recognizes your scanner.

Did you do the following from the Brother site?

5-2. Check if the scan-key-tool detect your scanner device
Command  :  brscan-skey  -l
Example
5-3. Press the scan button, select user, select destination, press START.
Example (console message of scan-to-img)

---

