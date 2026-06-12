---
title: "firestarter issue"
date: 2005-05-23
forum: General Help
---

### Post by dresnu on 2005-05-23
I messed up with firestarter :-(. I deleted by mistake two ip hosts in the whitelist that i presume were the eth0 and my isp(?). Well I don't know, but after that my connection was useless(firefox said connection refused, ecc) even though the ligths on the ethernet modem showed that I was connected. I tried to add the rules for those ips but nothing changed. At last I reinstalled the firewall and now when I try to start it I get this: 

"External network device eth0 is not ready. Aborting..
Failed to start the firewall
The device eth0 is not ready.

Please check your network device settings and make sure your
Internet connection is active."

Though my connection is perfectly running and I can use firefox and everything.
Any ideas?

---

### Post by dekoi on 2005-05-23
Have you tried running the Wizard to reconfigure your settings?

Firestarter > Firewall > Run Wizard

It should re-detect eth0 and make sure:

"IP address is assigned via DHCP" is checked.

In KDE, Control Center > Internet & Network > Network Settings should tell you your IP#, don't know what it is in Gnome... anyone?

Not that you *need* a firewall with (K)Ubuntu, but if paranoid-level security is important, I'd suggest running Bastille (system hardener) as well.

---

### Post by dresnu on 2005-05-23
ooo shi... I checked the internet settings and it says "disabled ethernet network device"... :-/. How could have messed up my eth0 connection only by changing something in the firewall? my ifconfig says:
"eth0      Link encap:Ethernet  HWaddr 00:02:A5:BC:E3:EB
          inet6 addr: fe80::202:a5ff:febc:e3eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:38031085 (36.2 MiB)  TX bytes:3227206 (3.0 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:280 (280.0 b)  TX bytes:280 (280.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:82.54.86.21  P-t-P:192.168.100.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:39150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:37159201 (35.4 MiB)  TX bytes:2533548 (2.4 MiB)
"

But my connection is running ok.

---

### Post by dekoi on 2005-05-23
> How could have messed up my eth0 connection only by changing something in the firewall?

Firestarter is a frontend/GUI for your computer's IPtables--the premise behind the function of a firewall. When you fiddle with the firewall, you're fiddling with the system's IP settings. But as I'm not an expert in their program (and at the risk of passing the buck), my best suggestion is to email them and ask them what to do: 

[email]tomas@fs-security.com[/email]

That's the addy they give @ Firestarter. Sorry I couldn't do more; I'm hardly an expert in this arena. But glad you're able to get online until the specifics are resolved.

---

### Post by dresnu on 2005-05-24
Ok, fixed it. I put the firewall on ppp0. Thx anyway

---

