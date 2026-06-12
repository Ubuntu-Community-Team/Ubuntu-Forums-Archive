---
title: "[tcpdump] how to find which PID sent a UDP datagram"
date: 2019-10-01
forum: General Help
---

### Post by Skaperen on 2019-10-01
i am running [COLOR=#0000cd][FONT=courier new]**tcpdump**[/FONT][/COLOR], watching the traffic on port 53.  there are some interesting queries.  i'd like to know which process ID sent each.  does anyone know a way to find out?

---

### Post by HermanAB on 2019-10-01
I have done something like that in the past with the help of iptables.

You can launch a process with a different GID using sg.  Iptables can do filtering of packets on the GID.  So you can then make rules that will filter or log data based on the GID.

---

### Post by Skaperen on 2019-10-03
> You can launch a process with a different GID.

can non-root users do that for files they don't own?

---

### Post by HermanAB on 2019-10-04
Well, its been more than 10 years - so you got to read the sg man page and try it.  The hard part is getting the iptables rules to work.

---

### Post by The Cog on 2019-10-04
My guess is that you will find that the program sending the packets is dnsmasq : the domain name resolver process. Figuring out which process is trying to resolve the name into an IP address will likely be more difficult. I don't know how I would go about that.

---

### Post by Skaperen on 2019-10-04
[COLOR=#006400][FONT=courier new]**dnsmasq**[/FONT][/COLOR] is not running, yet.  if i can figure out how to make it forward all queries to 3 specific IP addresses in rotation or fallback, that's when i run it.  for now /etc/resolv.conf lists those 3 IPs.  i suspect [COLOR=#006400][FONT=courier new]**firefox**[/FONT][/COLOR] is the one.  the queries are for [COLOR=#800080][FONT=courier new]**s3**[/FONT][/COLOR][COLOR=#808080]**(various)**[/COLOR][COLOR=#800080][FONT=courier new]**.amazonaws.com**[/FONT][/COLOR].

---

