---
title: "No Networking, Odd NTPD Messages"
date: 2018-08-13
forum: General Help
---

### Post by jrajra on 2018-08-13
Hello all,

Had a UPS fail during a powercut. NAGIOS VM here seems upset following. As per title, it's not got any networking, can only ping loopback but can't ping anything else and isn't ping-able.

fsck-ed it from a boot disk for good measure, found nothing to fix.

I randomly see "Starting NTP Server ntpd" messages on it, which is about my only clue and now I'm stumped.

Anyone have any ideas what I might do? Thanks everyone for reading. :)

---

### Post by wyliecoyoteuk on 2018-08-13
the ntp deamon will fail if there is no network.

What is the output from:

ifconfig

---

### Post by jrajra on 2018-08-13
Hi! Just a few minutes ago solved it; it was as you say not NTP at all. Fiddled with some settings in KVM (virtual NIC type) and it's up and happy.

Thanks for the reply! :)

---

