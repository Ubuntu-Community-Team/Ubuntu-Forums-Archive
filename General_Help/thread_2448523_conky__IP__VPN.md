---
title: "conky / IP / VPN"
date: 2020-08-09
forum: General Help
---

### Post by T6&amp;sfpER35% on 2020-08-09
just curious,my conky shows my local and external IP ,but when i jump on a VPN ,the external IP on conky doesn't change.
nothing serious ,doesn't bother me , just thinking why IP doesn't change.
thanks!

---

### Post by CelticWarrior on 2020-08-09
That is because your external IP didn't change. What changes with a VPN is the IP seen by the sites you're visiting.

---

### Post by ajgreeny on 2020-08-09
I can't imagine why but then I don't know very much about VPNs and have never used one.

However the VPN is "virtual," so perhaps it still uses the Public IP that is from your ISP, even when you're using the VPN?

What command do you use in the conky configuration file?
Mine uses ```
PUBLIC IP: ${alignr}${execi 3600 curl  ipinfo.io/ip}
```

EDIT:
There you are; ninja'd by CW.

---

### Post by T6&amp;sfpER35% on 2020-08-09
> [COLOR=#000000]That is because your external IP didn't change. What changes with a VPN is the IP seen by the sites you're visiting[/COLOR]

ok that sort of makes sense
i just thought  VPN changes YOUR IP ,not even your ISP can see what you doing?

> [COLOR=#000000]What command do you use in the conky configuration file?[/COLOR]

```
${execi 1000 ip a | grep inet | grep -vw lo | grep -v inet6 | cut -d \/ -f1 | sed 's/[^0-9\.]*//g'}  ${alignr}${execi 1000  wget -q -O- http://ipecho.net/plain; echo}
```

---

### Post by CelticWarrior on 2020-08-09
> [COLOR=#000000]i just thought VPN changes YOUR IP ,not even your ISP can see what you doing?[/COLOR]


Please note I'm no expert, you should wait for answers from the actual experts.

A VPN is a sort of tunnel between you and the VPN provider, typically encrypted. So, your ISP probably won't be able to see what you're doing except that you're connecting to the VPN's IP and the amount of traffic. Your ISP can see that you're sending and receiving packages and how big or small they are to a "mail forwarder" but not what's inside. Your house address is the still the same but known by the "mail forwarder" only. The site sending you back the packets only knows (and logs) the forwarder's address.

---

### Post by T6&amp;sfpER35% on 2020-09-01
i dont think so

[https://nordvpn.com/blog/vpn-vs-proxy/#:~:text=VPNs%20encrypt%20your%20traffic%20while,used%20to%20handle%20sensitive%20information%3B&text=A%20VPN%20connection%20is%20more,server%20connections%20drop%20more%20frequently.](https://nordvpn.com/blog/vpn-vs-proxy/#:~:text=VPNs%20encrypt%20your%20traffic%20while,used%20to%20handle%20sensitive%20information%3B&text=A%20VPN%20connection%20is%20more,server%20connections%20drop%20more%20frequently.)

---

