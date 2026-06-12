---
title: "Using custom DNS servers"
date: 2012-11-02
forum: General Help
---

### Post by jsvidyad on 2012-11-02
Hello,

  For security reasons, I'd like to use custom DNS servers specified by me on ubuntu rather than using my router IP address as the DNS server as is set up right now(that's how it is by default; I believe the IP of DNS server is got from the DHCP server in the router; that is what /etc/resolv.conf shows). The router then forwards the DNS requests to other DNS servers specified in its settings. I have heard that it is more secure to use DNS servers specified by you on ubuntu rather than using the ones specified by the router(which a malicious attacker can change).

   So, can someone please suggest DNS server IP addresses that I can use?

Also, can you tell me how I can set up my computer to use these custom IP addresses every time instead of relying on the router. I'd like to get this info for both kubuntu 10.04 and ubuntu 12.04.

    Thank you in advance for your help.

---

### Post by papibe on 2012-11-02
Hi jsvidyad.

Your router is probable using your IPS' DNS. Alternatives would be to use [Google Public DNS]("https://developers.google.com/speed/public-dns/") or [OpenDNS]("http://www.opendns.com/").

It may be possible to set a custom DNS by setting it in your router itself (check if it possible). That would solve the problem for all your home network.

As for per machine solution, take a look at this [tutorial]("http://www.omgubuntu.co.uk/2010/09/how-to-switch-to-opendns-in-ubuntu-for-faster-browsing").

Let us know how it goes.
Regards.

---

### Post by gerowen on 2012-11-02
Did a quick video on it if you haven't already gotten it taken care of.  Personally I flashed my Linksys router with DD-WRT and have it set to use Google's public DNS servers, so unless a device has other DNS servers explicitly specified, everything uses Google's public DNS servers instead of the ones from my ISP.

Video: [http://youtu.be/xIOpfBooCvw](http://youtu.be/xIOpfBooCvw)

---

### Post by jsvidyad on 2012-11-03
Hello, 

  I am not looking to change the DNS server settings on my router. I know how to do that. The DNS servers on the router can be changed by someone who gets access to my router. So, I want to have the option of specifying some other trusted DNS servers on my computer and use that instead of the ones in the router.

---

### Post by gerowen on 2012-11-03
> **jsvidyad said:**
> Hello, 

  I am not looking to change the DNS server settings on my router. I know how to do that. The DNS servers on the router can be changed by someone who gets access to my router. So, I want to have the option of specifying some other trusted DNS servers on my computer and use that instead of the ones in the router.

My video demonstrates how to do it.

Scroll up to my previous post.
```


           ^
          / \
         /   \
           |
           |
           |
           |

```

---

### Post by dcstar on 2012-11-03
> **jsvidyad said:**
> 
..........
I have heard that it is more secure to use DNS servers specified by you on Ubuntu rather than using the ones specified by the router **(which a malicious attacker can change)**.
.........

Absolute tosh.

The DNS settings in your router are supplied by your ISP when your router authenticates. Unless **you** have opened up your router to external administration these will not change.

If **you** want to use different DNS settings then **you** go into your router and change the relevant settings in the DHCP setup, or simply set up Static IP settings inside Ubuntu with whatever DNS servers you want.

---

### Post by jsvidyad on 2012-11-03
> The DNS settings in your router are supplied by your ISP when your router authenticates. Unless you have opened up your router to external administration these will not change.

If you want to use different DNS settings then you go into your router and change the relevant settings in the DHCP setup, or simply set up Static IP settings inside Ubuntu with whatever DNS servers you want.

Hello, in this case the DNS servers for my ISP had to be manually entered into the router.  I am talking about a hypothetical case when someone managed to get remote access to my router and changed the DNS server settings to something he owns. Then, he can re-direct queries to his websites where he can steal info from us and do other malicious stuff. I want to specify the DNS servers in my computer in order to protect against this.

---

### Post by SeijiSensei on 2012-11-03
> **jsvidyad said:**
> I want to specify the DNS servers in my computer in order to protect against this.

Then you need to specify them in the Network Configuration for each computer on the network.  If you use static addressing, you need to add a "dns-nameservers" directive in /etc/network/interfaces.  If you use DHCP, you can tell the DHCP client to override the DNS server IPs it gets from the router with another set you specify.  This is easy to do in KDE; I suspect the other major desktop environments offer a similar alternative.

I will say, though, that the problem you are concerned about is extremely unlikely to happen in practice.

Another option is to disable DHCP on the router and set up dhcpd on a server on the network instead.  Then your DHCP server will not be exposed to the Internet at all.  If you already have a working DNS server running bind9, just install the dhcp-server package on that machine as well.  Configure dhcpd.conf to your liking, then turn off the router's DHCP server.

---

