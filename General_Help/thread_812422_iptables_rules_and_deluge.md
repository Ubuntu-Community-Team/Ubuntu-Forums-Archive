---
title: "iptables rules and deluge"
date: 2008-05-29
forum: General Help
---

### Post by Locutus_of_Borg on 2008-05-29
oh hai

i have set up iptables as such:
```
Collective borg # iptables -L -v
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1449  134K ACCEPT     all  --  lo     any     anywhere             anywhere            
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:domain 
   31  1860 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:http 
 775K  519M ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:aol 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            state NEW tcp dpts:6881:6889 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:irc 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:rsync 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpts:2234:2239 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:2240 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:gnutella-rtr 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:5050 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpts:1024:1030 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:9050 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:6881 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:6969 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN multiport ports 6881:6889 
   35  5683 ACCEPT     udp  --  any    any     anywhere             anywhere            udp multiport ports 6881:6889 
    0     0 DROP       icmp --  any    any     anywhere             anywhere            icmp echo-request 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy DROP 393 packets, 23760 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 709K  553M ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
  483 31188 ACCEPT     all  --  any    lo      anywhere             anywhere            
 2335  152K ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:domain state NEW 
 4109  247K ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:http state NEW 
    7   420 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:https state NEW 
 1634 98040 ACCEPT     tcp  --  any    any     anywhere             anywhere            state NEW tcp dpts:6881:6889 
   66  3960 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:5050 
   16   960 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:aol 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ircd 
    2   120 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:rsync 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:git 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:9050 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:6881 
   19  1140 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:6969 
 4497  522K ACCEPT     udp  --  any    any     anywhere             anywhere            udp multiport ports 6881:6889 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN multiport ports 6881:6889 
    0     0 DROP       icmp --  any    any     anywhere             anywhere            icmp echo-request 

```

yet I am never able to connect to any seeders or peers when i run deluge.  it does show that there are several hundred available connections, but something obviously is blocking the port.

i have set deluge to use ports 6881-6889

if I change the output policy to ACCEPT instead of DROP, then it connects

What am I doing wrong?

Thanks.

---

### Post by latna on 2008-05-29
The problem with deluge, or any bittorrent program, or any file sharing program for that matter, is that you don't know what port the remote clients are using. Since ISPs often try to limit traffic for bittorrent, people rarely use the default ports anymore. Your firewall won't let you make a connection to my pc running azureus for example.

I think you're stuck setting the output policy to connect if you want to use bittorrent.

---

### Post by Locutus_of_Borg on 2008-05-29
i was thinking that although the server is using ### port that i would still be able to use my specific port to receive and transmit that information on

but i have to use the same port number that the person i'm downloading from is using?


also, is it really any security risk to have output accept like that?

if so, what ports would you suggest I drop, while keeping the rest open?

thanks

---

### Post by latna on 2008-05-29
OK here's a more detailed explanation. The output connection are originating from your own machine. You have all the outbound connections blocked and then you're making specific exceptions based on the destination port. For example if you make a connection to a web server that's listening on port 80, your firewall will let that through because you've made a connection in that case.

When deluge tries to make a connection to another bittorrent client, it will be let through if the remote client is listening on port 6881. The problem is that most client programs don't listen on that port anymore because people are told to use a different port to avoid their ISPs filters. So if deluge tries to connect to a client listening on port 4062, you firewall won't let it through because you haven't made that exception. It's not deluge that's the problem it's your firewall that's blocking the traffic.

I don't know any way to find out what port a bittorrent client is listening on and automagically add an iptables rule for it.

As for is it safe? Well, I allow all outbound traffic. It's safe for my setup. The only reason you would want to block outgoing traffic is if you had servers running that were broadcasting on the internet advertising that they're there, like windows netbios does. I'm not aware of any linux servers that do that. It would also stop viruses from propagating on the internet like what happens with windows.

---

### Post by unutbu on 2008-05-29
Where can I find good documentation to learn more about iptables?

---

### Post by Locutus_of_Borg on 2008-05-29
ok thanks latna, ill just leave outbound open for the time being, and if the need arises, block any individual ports there

unubtu, i used the ubuntu wiki to set up iptables even though im running gentoo, its easy to understand

---

