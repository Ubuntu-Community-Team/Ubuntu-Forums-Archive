---
title: "Unable to connect using Citrix Receiver"
date: 2013-12-25
forum: General Help
---

### Post by susja on 2013-12-25
Hello,
I'm using Ubuntu 12.04 32bit
I have to connect to my desktop in the office. My company is using Citrix Receiver for VPN. I tried to use version 13,0, 12.1 and 11.1. I tried to use Chrome, FF and Opera. None of the combination gave me stable result. Initially it worked using FF + 12.1 for ~ 1 week but then it started to fail to connect and either throws an error (see attachment) or some pop-up window starts and disappears resulting in no connection.
Could someone please try to help me to understand what could be the issue?
Thanks in advance.[ATTACH=CONFIG]248887[/ATTACH][ATTACH=CONFIG]248888[/ATTACH]

---

### Post by jtzero on 2014-01-01
try 
**5. Add more SSL certificates**

 Some sites can give an SSL error. Firefox has many more certificates than does Citrix, so add them: e.g. 

sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
sudo c_rehash /opt/Citrix/ICAClient/keystore/cacerts

---

### Post by susja on 2014-01-01
- jtzero
Thanks for suggestion. I  tried but it didn't make a difference.
I'm wondering if some of the latest OS update made the impact because before I was able to connect.
Thanks anyway.

---

### Post by richardcoates on 2014-01-27
After days of struggling I solved this......tested on ubuntu 13.10 (*32bit), Mint16 (*32bit)
install openmotif2.3.1-2.deb ( rpm file repackaged with "alien", or google.. )
install icaclient13

I had  "SSL error 61 " ...  missing..  "VeriSign Class 3 International Server CA - G3"
copy SVRIntIG3.crt (google) to  cacerts/  directory
# sudo cp SVRIntlG3.crt  /opt/Citrix/ICAClient/keystore/cacerts/

convert certificates to  " ,pem"  format
# sudo c_rehash /opt/Citrix/ICAClient/keystore/cacerts

I did not need this but for other "SSL errors" you could try...
#  ln -s  /etc/ssl/certs  /opt/Citrix/ICAClient/keystore/cacerts/

best regards, Richard.

---

### Post by susja on 2014-01-27
Thanks Richard
My problem was solved not by changing something from my side :) but after they did some upgrade on server side I have no problem to connect anymore 
Thanks anyway

---

