---
title: "Ubuntu Port Scan Results?"
date: 2008-06-05
forum: General Help
---

### Post by ShinHadoken on 2008-06-05
What would you get if you ran nmap on a default, untouched installation of Ubuntu? I mean, I know Ubuntu doesn't open any ports by default, but do they show up as closed or filtered in nmap? and which one is more preferable? (<-- spelling?)
 
Thanks, 
 
SH

---

### Post by cariboo on 2008-06-05
Here is a scan of my fresh install of intrepid.

```
jimk@intrepid:~$ nmap localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-04 22:07 PDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1712 closed ports
PORT    STATE SERVICE
631/tcp open  ipp
902/tcp open  iss-realsecure-sensor

Nmap done: 1 IP address (1 host up) scanned in 0.073 seconds


```

Port 902 is setup when installing hddtemp. So the only port open is cups on 631.

Jim

---

