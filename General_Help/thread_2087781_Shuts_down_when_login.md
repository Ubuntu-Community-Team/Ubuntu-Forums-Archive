---
title: "Shuts down when login"
date: 2012-11-24
forum: General Help
---

### Post by AvengerX9 on 2012-11-24
My Ubuntu now shuts down immediately after login. Or if I don't login it shuts down too after a few minutes.


Please help!

---

### Post by AvengerX9 on 2012-11-24
I press Ctrl+Alt+F2 and tries to login with my username and password and I get a message you have mail and something more then it shuts down.


Hope someone can help me, right now I don't seem to get inside the computer at all!

---

### Post by AvengerX9 on 2012-11-24
UPDATE!

Im able to login now after I removed the internet connection to the server. Now it works as normal until I reconnect it to the internet. Then it shuts down!

I also upgraded webmin to the latest edition today. Could this cause the problems I got ? Its the only thing I did to the computer today!

Help

---

### Post by AvengerX9 on 2012-11-24
in the apache error log I get a message telling me to consider increasing the MaxClients. I also run netstat and got a big list of connections. ??

---

### Post by AvengerX9 on 2012-11-25
A few hours later, no changes done I reconnect the server to the internet and it seems to work as I write this, but I would love to know what happend

---

### Post by rnerwein on 2012-11-25
> **AvengerX9 said:**
> A few hours later, no changes done I reconnect the server to the internet and it seems to work as I write this, but I would love to know what happend
hello
try a "netstat -lpunt" to see where sytem is going.
netstat -lnput gives you:
 2678/ubuntu-geoip-ptcp    0      0 192.168.2.138:36313     91.189.89.76:443     VERBUNDEN  

may be this information will show you the bad boy who will permanently connect to your
apache.

---

