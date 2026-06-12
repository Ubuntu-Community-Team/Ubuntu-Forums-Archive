---
title: "My Ubuntu in Vmware can not connect outside"
date: 2008-05-29
forum: General Help
---

### Post by kam1 on 2008-05-29
Dear guys,I am a new comer in Ubuntu world.I installed Ubuntu 8.04 on vmware6( which is green version),and set network as Bridged.
My laptop is in lan network and get ip from dhcp as 10.200.161.XXX
OS is WinXP .I have tried to set my network as automatic dhcp or static ip .But i still can not ping the gateway successfully .What shall i do then?
Could you help me with that?Please feel free to mail me at [email]kaiminmin@gmail.com[/email].  thanks

---

### Post by Monicker on 2008-05-29
When you set the guest to use dhcp, does it actually obtain an ip address?

If you run the following, does it show any errors with the services?
```

sudo /etc/init.d/vmware restart
```

---

### Post by bkortleven on 2008-05-29
Just an idea... or better, extra information could be useful, so:

- Are you connected through wireless or wired for internet access (the 10.x.x.x ip)
- Did you connect your VMWare virtual networks to you wired and/or your wireless adapters?
- Is the DHCP providing more addresses than you are using now? (dhcp pool might have run out? <- last resort)
- When doing (in the Guest) a 'sudo /etc/init.d/network restart' and looking at your /var/log/messages and /var/log/syslog, is either complaining on anything? (that info might be helpful too...)

Try that, and post your findings, we'll try to help you out...

---

