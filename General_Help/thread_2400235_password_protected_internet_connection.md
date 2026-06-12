---
title: "password protected internet connection?"
date: 2018-09-04
forum: General Help
---

### Post by marchello_lippi2 on 2018-09-04
Hi all, 
How do I set password to access internet connection? 

Yes, I know I can create network connection that will be available only for particular ubuntu user. 
Also I can set squid with password protection. 

Anything else? 
Thanks ahead for any suggestion.

---

### Post by ajgreeny on 2018-09-04
You normally set the password in your router, not in the computer connecting to it so logon to your router's admin page and set it to use wpa2 encryption with a good password.

---

### Post by marchello_lippi2 on 2018-09-04
> **ajgreeny said:**
> You normally set the password in your router, not in the computer connecting to it so logon to your router's admin page and set it to use wpa2 encryption with a good password.
Way to go in general, would be nice solution for wifi clients. In my case, it is ethernet connection. Thx anyway.

---

### Post by ajgreeny on 2018-09-04
Ah! I did not even consider that you were using ethernet; strangely as that is how I connect.

---

### Post by SeijiSensei on 2018-09-05
I don't know of any way to require passwords to connect to the Internet as a whole.  For browsing, I'd use Squid.  If you want to manage SSL connections as well, you need to look into using "ssl_bump" which requires a certificate on the server and matching certs in all the clients.

---

### Post by marchello_lippi2 on 2018-09-05
Let's say, I would restrict access to the network for particular user in general. As it is the only pc at home, we do not need LAN at all. Maybe this would be easier to maintain? Any suggestions appreciated.

---

### Post by marchello_lippi2 on 2018-09-05
I believe it's worth trying link below: 
[https://unix.stackexchange.com/questions/21650/how-to-restrict-internet-access-for-a-particular-user-on-the-lan-using-iptables](https://unix.stackexchange.com/questions/21650/how-to-restrict-internet-access-for-a-particular-user-on-the-lan-using-iptables)
(will check it on weekend).

---

### Post by SeijiSensei on 2018-09-05
You could use iptables or the router's firewall to deny access to that PC based on its IP address.  A more robust alternative is to use iptables to [block by MAC address]("https://www.cyberciti.biz/tips/iptables-mac-address-filtering.html").

---

### Post by marchello_lippi2 on 2018-09-05
> **SeijiSensei said:**
> You could use iptables or the router's firewall to deny access to that PC based on its IP address.  A more robust alternative is to use iptables to [block by MAC address]("https://www.cyberciti.biz/tips/iptables-mac-address-filtering.html").
Worth trying, thx! Don't want to experiment on my own pc, should do it during weekend on the other pc.

---

