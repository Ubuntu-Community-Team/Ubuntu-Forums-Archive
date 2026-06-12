---
title: "Disabling IPv6...stuck with a couple of services"
date: 2014-12-18
forum: General Help
---

### Post by KillerKelvUK on 2014-12-18
I'm doing a little security hardening and am looking to disable IPv6 at the OS and service layers...

For the OS I've followed other posts and have completed the below...

```

cat /proc/sys/net/ipv6/conf/all/disable_ipv6 
1
```

However I still have services listening on IPv6 both TCP and UDP, I've managed to reconfigure most services to disable their IPv6 support however I'm stuck with _Samba_ and _Dnsmasq_.  I've seen some posts that suggest neither of these 2 services give the option to disable IPv6 but I'm seeking confirmation of this or a solution if anyone can help out?

Thanks

---

### Post by KillerKelvUK on 2014-12-18
Okay so think I've found the *proper* solution to the Samba question but not for Dnsmasq.

For Samba I had omitted the 'bind_interface_only=yes', when I corrected this it removed all IPv6 listeners.

For Dnsmasq I'm only using DHCP so the man pages advise to force the port= to zero which effectively disables DNS which was what was listening for IPv6.  However I plan to implement DNS at a later date so this isn't really a final solution.

---

