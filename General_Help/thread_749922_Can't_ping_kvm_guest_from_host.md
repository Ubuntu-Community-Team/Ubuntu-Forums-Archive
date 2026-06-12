---
title: "Can't ping kvm guest from host"
date: 2008-04-08
forum: General Help
---

### Post by mgoldsby on 2008-04-08
Host is Ubuntu Gutsy, guest is Windows XP SP2.  
Host ip is 192.168.0.200.
I have tun device qtap0 with ip 10.111.111.254.
I'm running vde:  'vde_switch -tap qtap0 -daemon'.
Guest ip is 10.111.111.140 with gateway 10.111.111.254.
I start guest with 'vdeq kvm -hda windows.img -net nic -net vde -m 512'.
I can ping the host from the guest.  (In fact, if I set up ip forwarding and masquerading, I can reach the internet from the guest.)
However, I can't ping the guest from the host.
What have I left out?
Thanks for any suggestions.

--Mike

---

### Post by mgoldsby on 2008-04-09
I'm moving this post to the Networking forum, where I probably should have put it in the first place.

--Mike

---

