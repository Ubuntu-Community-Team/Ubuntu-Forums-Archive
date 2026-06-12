---
title: "Host not found:"
date: 2007-08-14
forum: General Help
---

### Post by oldnerd on 2007-08-14
I am setting up squid and came across an error indicating the application was not happy with the host name. I tried the terminal command "host <computer_name>" on the terminal and received the following error.

Host <computer_name> not found: 3(NXDOMAIN)

localhost is okay but the computer_name is not, email and web are fine... I noticed that the computer name is listed under the IP address of 127.0.1.1, separately to localhost.

Does anyone have a suggestion?


Thanks

oldnerd

---

### Post by woorzel on 2007-08-14
add it to /etc/hosts next to its IP ?

---

### Post by oldnerd on 2007-08-15
Yep, my first port of call, looks okay, though. I have set up squid in a server before and had no problems. This machine is running Ubuntu 7.0.4 and receives its ip from a router.

I might give it a couple of days and reinstall the system, being careful with the networking.

Thanks

---

