---
title: "ip6tables match state"
date: 2005-07-28
forum: General Help
---

### Post by Azog on 2005-07-28
Hi,
As I was creating a firewall-script for ipv6 I found that

ip6tables -t filter -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

gives the error

ip6tables v1.2.11: Couldn't load match `state':/lib/iptables/libip6t_state.so: cannot open shared object file: No such file or directory

The problem is, that I want the default policy for the INPUT chain to be DROP, because I  want control over my services and without the state match I get troubles over troubles... With ipv4 this works.
I found several iptables rpms for redhat,... with this file, but the debian/ubuntu package doesn't has it. It would be nice if this could be fixed, or someone can help me with that.
Greets

---

