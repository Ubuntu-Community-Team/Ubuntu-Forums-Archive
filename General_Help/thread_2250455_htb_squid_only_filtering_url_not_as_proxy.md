---
title: "htb squid only filtering url not as proxy"
date: 2014-10-28
forum: General Help
---

### Post by dozycat on 2014-10-28
I have a server with htb in eth0 and eth1, upload and download. the quos work perfect.

But I need to do url filtering, I know squid is the way to go but if we do proxy the ip source and destiny changes so htb stops working.

It is anyway to do filtering with squid but not do the proxy? we want to implement porn control but must be over the full url not the domain.

---

### Post by SeijiSensei on 2014-10-29
First, I at least have no idea what "htb" means, and I'm sure I'm not alone.

Squid resends all the requests it proxies out its publicly-facing address.  You would need to configure whatever htb is to accept traffic from that address.  For added security, just allow the squid proxy to send requests on ports 80 and 443.

---

### Post by dozycat on 2014-10-29
First htb is a tool to handle bandwith.

But what I am really looking is a way to use squid that will allow the packets to pass without change when the url is allowed and when denied to show a message in the explorer of the client.
I already tried:
[COLOR=#000000][FONT=Times New Roman]always_direct allow all

the squid is in transparent mode.

I am thinking of using an external squid before  the router server, but if thats the case still we don't want to do proxy because some service fails when using a proxy.[/FONT][/COLOR]

---

