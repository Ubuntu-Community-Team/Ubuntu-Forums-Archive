---
title: "Port Forwarding Problem &gt; Ubuntu v7.10"
date: 2008-04-27
forum: General Help
---

### Post by kj6eo on 2008-04-27
Hello All and thanks for reading my post.  I'm running a standard distro of Ubuntu v7.10 with a 2.6.22-14 kernel.  For some odd reason I can't get port forwarding (DNATTING) working.  I wrote a simple iptables firewall script <attached> to insure that DNAT was working correctly before writing the entire script.  I've got ipv4 enabled in /etc/sysctl.conf i.e:

net.ipv4.conf.default.forwarding=1

However I cannot establish a connection with the audio streamer on my LAN at 192.168.1.13:8080.  I'm trying to establish a connection to the stream from outside <internet> of course.

What is really strange is that I can take the same script and load it on my RHv9.0 box and it works perfectly (only change is public IP on SNAT rule).  Here is a description of some additional files I've attached:

1)  output_1.txt     "iptables -L"
2)  output_2.txt     "iptables -L -t nat"
3)  output_3.txt     "iptables -L -t mangle"

IN CLOSING:

I've got weeks of hard work getting Ubuntu configured for other things.  However If I can't crack this DNAT problem I'll have no other alternative but to dump Ubuntu and load up something else like FC8.  The bottom line is that I really like UBUNTU and I'd like to stick with it.

Any advice you might have would be appreciated!

Regards,

KJ6EO

---

### Post by ghost_ryder35 on 2008-04-27
is your router configured for port forwarding?  When you say it works on the Red Hat box it makes me think that you have the port forwarded on the router to that box and thats why it is not working on the Ubuntu box because the Red Hat box has that port forwarded to it so Ubuntu cant have access to that port...

---

### Post by kj6eo on 2008-04-28
Hello -

Thanks for your suggestion but the router is not the problem.  By doing a "tcpdump -i eth0" on the Ubuntu box I can see the connect request coming in (downstream of the router of course).  This DNAT problem is one of the hardest problems I've ran into so far with Ubuntu.

Regards,

Bill - KJ6EO

---

