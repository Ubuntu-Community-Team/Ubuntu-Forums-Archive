---
title: "How can I check the security logs of my server?"
date: 2008-03-08
forum: General Help
---

### Post by miju on 2008-03-08
I operate a standard LAMP server with Tor and Freenet services and a partially configured mixmaster/postfix service - every few days the server will freeze and I don't know why. My network is behind a router that is detect and number of attacks as SYN floods, unknown packets and pings of death - which it is dropping. Each of my individual computers are firewalled and antivirus and antirookit and spyware and spam protected.

Is someone attacking directly  me? or is this common to all servers?

How and where are the system admin logs so I can determine what's happening? thank you

---

### Post by dcstar on 2008-03-08
> **miju said:**
> I operate a standard LAMP server with Tor and Freenet services and a partially configured mixmaster/postfix service - every few days the server will freeze and I don't know why. My network is behind a router that is detect and number of attacks as SYN floods, unknown packets and pings of death - which it is dropping. Each of my individual computers are firewalled and antivirus and antirookit and spyware and spam protected.

Is someone attacking directly  me? or is this common to all servers?

How and where are the system admin logs so I can determine what's happening? thank you

/var/log

---

### Post by miju on 2008-03-08
there are many logs there for different processes - which should I check for hacking? I examined syslog but it  is very technical and much of it appears to be standard.

---

