---
title: "System wide proxy not working but firefox proxy is"
date: 2016-12-08
forum: General Help
---

### Post by Kerbi on 2016-12-08
I am trying to set proxy setting globally for my laptop.
I go to system setting -> network and set the proxy there.
However, it does not seem to work.

If use the same proxy and set it in firefox then it works for firefox.
I tested this on a windows global proxy setting and it works there as well. I am not sure what I am missing here.

---

### Post by SeijiSensei on 2016-12-08
You can't proxy entire networks, just specific services.  That's why it works with browsers.  The proxy you're using is presumably designed for HTTP traffic.

---

### Post by Kerbi on 2016-12-08
Hello SeijiSensei, I should have explained myself better. I have both Chrome and Firefox installed on my system. 
I would like 'global' setting so that it works for any browser on the system rather than just having tied to any one browser.
As it is right now, it only works for firefox through it's specific config and not for chrome.

---

### Post by SeijiSensei on 2016-12-08
Where is the proxy located?  Is it on your machine or somewhere upstream?

---

### Post by Kerbi on 2016-12-08
The proxy is in our Data Centre VLAN and my machine is connected to our office VLAN.

---

### Post by SeijiSensei on 2016-12-09
Well, if it's an HTTP proxy, you could try using iptables to direct the traffic to the proxy. 

```

sudo /sbin/iptables -t nat -A PREROUTING -p tcp -m tcp --dport 80 -j DNAT --to-destination PROXY_IP:PROXY_PORT

```

That rule intercepts outbound HTTP traffic and sends it to PROXY_PORT on PROXY_IP.  Replace those with the correct values for your situation.

I'm not making any guarantees here since I've not used iptables in this way, but I suspect it will work.

If this does solve your problem, add that command to the file /etc/rc.local above the "exit 0" line. Leave off the "sudo" at the beginning since everything in that file runs with root privileges by default.  You will need to use sudo to edit rc.local.

---

### Post by Kerbi on 2016-12-09
I was actually hoping that there be a simpler solution rather than using iptables.
I did try the rule but unfortunately, no luck.

There is a how to article I found with iptables [http://www.tldp.org/HOWTO/TransparentProxy-1.html](http://www.tldp.org/HOWTO/TransparentProxy-1.html) but I don't think I will have the time to try this soon.

---

### Post by SeijiSensei on 2016-12-09
That article concerns how to set up a transparent proxy with Squid and iptables.  It won't help in your case.  You don't need a proxy on your machine, you need to connect to the one already provided. Too bad the folks that manage the proxy you need to use didn't implement transparency.  Then it would all "just work" without any configuration on your part.

---

