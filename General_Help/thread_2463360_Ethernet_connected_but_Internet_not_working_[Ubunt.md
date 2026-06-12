---
title: "Ethernet connected but Internet not working [Ubuntu 20.04.2]"
date: 2021-06-09
forum: General Help
---

### Post by djpicard on 2021-06-09
Hello all, 

Very much a linux noob so bear with me. My ssd with windows recently failed and I don't have a flash drive large enough to install windows on my second drive so I figured I would use linux instead since everything I needed could be done natively on linux or through wine. Slight problem however, internet has not worked on any of the distros I have tried. At first I tried Pop! os and the ethernet wouldn't even connect with that one, same story with manjaro. Now I am using ubuntu 20.04.2 LTS and my ethernet works now just not the internet so I can't really do anything on my computer. It's also important to note that my computer does not have Wi-Fi capabilities, only ethernet. Is this just a thing with xfinity or is there something I have to put into the terminal to get this to work. The ethernet and internet worked fine last time I tried manjaro but I had the same problem on pop os last time i tried a few months back.

Hardware if it's needed

Ryzen 5 1600 af

Radeon Rx 5600xt

Gigabyte b450 ds3h (ver 2 i think)

32 gb ddr4 3200 ram

Western Digital 320 gb hard drive

---

### Post by grahammechanical on 2021-06-09
You say

> my ethernet works now

Does that mean that Ubuntu is connected to the route/hub? You also say

> just not the internet

Does that mean the router is not connecting to an Internet Service Provider (ISP)? The router should have come with a small manual that explains how to use a web browser to access the router's settings utility. From there you should be able to test the connection to the ISP and onwards to the Internet. The manual should give you the http address of the router to enter into the browser address to go to panel, also the Username of the router and then the password of the router. These are the default settings. They are user changeable. You may have changed them and that would make some of my instructions invalid.

Regards

---

### Post by SeijiSensei on 2021-06-10
There are usually two likely sources of this problem. One is that traffic is not being correctly sent upstream by the router. Another is that you cannot resolve names like ubuntuforums.org.

Let's try the first issue. Open a terminal with Ctrl+Alt+T and type in the command "route -n".  You should see something like this:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    601    0        0 wlx9848275ed127
192.168.100.0   0.0.0.0         255.255.255.0   U     601    0        0 wlx9848275ed127

```
The second line tells Linux where to send traffic for the local network, in my case 192.168.100.0/24. The line that begins with 0.0.0.0 is called the "default" route and tells Linux where to send any traffic not intended for the local network. In my case it sends it to the "gateway" 192.168.100.1, which is the address of my router.

Once you've determined the gateway address, make sure you can reach it by typing "ping ip.addr.of.gateway" like "ping 192.168.100.1".

---

### Post by ActionParsnip on 2021-06-10
Can you ping your router's internal IP (usually 192.168.0.1 on home grade stuff)?
Can you ping 8.8.8.8?
Can you ping [www.bbc.co.uk](www.bbc.co.uk) and do you get an IP back (showing DNS is working)?
Have you rebooted your router?

---

### Post by djpicard on 2021-06-14
I typed that in but is says "Command 'route' not found, but can be installed with: sudo apt install net-tools. I tried this but it did not work. It says Temporary failure resolving 'us.archive.ubuntu.com'

---

### Post by djpicard on 2021-06-14
> Does that mean that Ubuntu is connected to the route/hub?

According to xfinity it is connected under the name ubuntu although for some reason it still identifies as a windows 10 machine.

> Does that mean the router is not connecting to an Internet Service Provider (ISP)? 

The router is connected to the internet because everything else works with the router just fine, it's only been the various linux distros that haven't worked.

---

### Post by djpicard on 2021-06-14
> Can you ping your router's internal IP (usually 192.168.0.1 on home grade stuff)?
I can ping the Local IP, the IPv4 one, but the one you mentioned did not work and pinging WAN IP address did not work either.
> Can you ping 8.8.8.8?
No I cannot
> Can you ping [www.bbc.co.uk]("http://www.bbc.co.uk") and do you get an IP back (showing DNS is working)?
I cannot ping it: It says Temporary failure in name resolution
> Have you rebooted your router?
 Yes

---

