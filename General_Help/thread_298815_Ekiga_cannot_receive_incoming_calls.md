---
title: "Ekiga cannot receive incoming calls"
date: 2006-11-13
forum: General Help
---

### Post by kitsos on 2006-11-13
Hi,
I've been using ekiga to connect to my SIP provider voipbuster.com. I have successfully configured it with proxy/domain/username/pwd. At the moment i am behind CONE NAT and have tried using a few different STUN servers. I can successfully make outgoing calls. However, i cannot accept any incoming calls. Actually if I unregister and register my voipbuster account through ekiga i can accept **one** incoming call only (the first one). All attempts to accept incoming calls after that fail.](*,) 

It looks as if ekiga does not register correctly after the first call or sth blocks the routing of the call to my PC. Does anybody have any clue as to what might be causing this behaviour and how it can be corrected?

NOTE: I can use SJPhone to accept and receive calls with the same settings, however I'd rather use ekiga since it is OS and SJPhone has sound issues since it requires dsp. aoss (or the dsp redirection to ALSA) doesn't provide even remotely acceptable sound quality or interoparability with other applications that use the sound system at the same time.

---

### Post by frecon on 2008-06-18
Try setting the refresh registration limit (for your account) to 180 seconds.


[QUOTE=http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router#I_can_make_calls.2C_but_if_I_let_Ekiga_running_after_some_time_I_can.27t_receive_any_calls] I can make calls, but if I let Ekiga running after some time I can't receive any calls

    * The problem 

If your host isn't behind NAT and is behind a firewall that behaves like NAT except for the address translation magic, this may happend to you:

 I've got a simple setup, Linux (Fedora 6), no NAT,
 a direct connection to the net, but I've got a strict firewall
 (iptables, stateful). Concerning UDP, only ESTABLISHED,RELATED packets
 are allowed in, all packets are allowed out. Pretty simple, pretty
 common, I suppose. The problem is, with this setup Ekiga (as configured
 by the wizard, with STUN) only receives calls just after connecting to
 ekiga.net (or any other SIP provider). I can make calls, but if I let
 Ekiga running after some time I can't receive any calls.

    * Why this ? 

Ekiga registers with a service using UDP and the service expects to find Ekiga at the port it sent the registration. Well, in Linux with IP iptables, this port is only accessible for 180 seconds after the registration. After this time, the firewall will block the packets coming from the SIP service, as it considers the "session" to be over.

    * There are two ways of coping with that:
          o If you don't have control of your host, you can configure each account to refresh the registration every 180 seconds.
          o If you can control your host (root), you can set the UDP iptables timeout to one hour: 

# echo 3600 > /proc/sys/net/ipv4/netfilter/ip_conntrack_udp_timeout
# echo 3600 > /proc/sys/net/ipv4/netfilter/ip_conntrack_udp_timeout_stream

See [http://ipsysctl-tutorial.frozentux.net/ipsysctl-tutorial.html#AEN730](http://ipsysctl-tutorial.frozentux.net/ipsysctl-tutorial.html#AEN730) for more details. You can use the sysctl utility to set kernel variables more easily. [/QUOTE]

---

