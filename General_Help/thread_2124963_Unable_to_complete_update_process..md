---
title: "Unable to complete update process."
date: 2013-03-12
forum: General Help
---

### Post by arroy_0209 on 2013-03-12
My usual procedure to update fails now a days. I rum the update manager and select the necessary packages for updatation and start. But I promptly receive a message stating (assuming I chose firefox for updatation):
 [PHP]
failed to download package filters: check your internet connections:
  Details:       
         Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_19.0+build1-0ubuntu0.12.04.2_i386.deb 404  Not Found [IP: 31.065.17.801 80]
[/PHP]
The fact is that there is no problem with internet connection. I have always done updatation successfully following the same procedure but now this is failing. Where is the problem?

---

### Post by schragge on 2013-03-12
> **arroy_0209 said:**
> IP: 31.065.17.801This IP address has nothing to do with *security.ubuntu.com*. I guess it's 31.65.17.80 as .801 is impossible, then it belongs to Orange UK.

I wonder what would *ping -c3 security.ubuntu.com* show on your system?

---

### Post by arroy_0209 on 2013-03-12
The IP address I wrote was wrong. 
The result of *ping -c3 security.ubuntu.com* gives[I]:
> 
PING security.ubuntu.com (91.189.92.200) 56(84) bytes of data.
64 bytes from obake.canonical.com (91.189.92.200): icmp_req=1 ttl=55 time=293 ms
64 bytes from obake.canonical.com (91.189.92.200): icmp_req=2 ttl=55 time=298 ms
64 bytes from obake.canonical.com (91.189.92.200): icmp_req=3 ttl=55 time=298 ms

--- security.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10957ms
rtt min/avg/max/mdev = 293.758/296.826/298.439/2.170 ms

[/I]Also ping to security.ubuntu.com seems to reach different IP addresses, like 91.189.91.13 etc. But my problem still remains.

---

### Post by schragge on 2013-03-13
Are you behind a proxy?

---

### Post by arroy_0209 on 2013-03-13
I have never set any proxy myself. I checked the network connection setting from firefox and it says: "use system proxy settings". I am not sure how to detect details of this system proxy settings.

---

