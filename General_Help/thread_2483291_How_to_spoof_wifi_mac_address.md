---
title: "How to spoof wifi mac address?"
date: 2023-01-25
forum: General Help
---

### Post by jayblue2 on 2023-01-25
I want to connect to a public wifi but I don't want them to know this laptop has connected to their wifi before. I am following the instructions here on how to spoof my mac address:
[https://www.linuxfordevices.com/tutorials/ubuntu/spoof-mac-address](https://www.linuxfordevices.com/tutorials/ubuntu/spoof-mac-address)

I make it to step 3 

but on that screen, I don't see wifi
My screen looks exactly like their screenshot, I see wired, vpn, network proxy. 
But I think if I edit Wired, then my ethernet port mac address is spoofed, not my wifi mac address, correct?

How come there is no wifi card listed in that screenshot or on my screen?

---

### Post by #&amp;thj^% on 2023-01-25
totally different approach here, use it or ignore it 
I usually don't reply to threads like this, and Granted this a CLI utility.
```
apt policy macchanger
macchanger:
  Installed: 1.7.0-5.4
  Candidate: 1.7.0-5.4
  Version table:
 *** 1.7.0-5.4 500
        500 http://deb.debian.org/debian bullseye/main amd64 Packages
        500 https://deb.kaisenlinux.org kaisen-rolling/main amd64 Packages
        100 /var/lib/dpkg/status

```
Help:
```
 macchanger --help
GNU MAC Changer
Usage: macchanger [options] device

  -h,  --help                   Print this help
  -V,  --version                Print version and exit
  -s,  --show                   Print the MAC address and exit
  -e,  --ending                 Don't change the vendor bytes
  -a,  --another                Set random vendor MAC of the same kind
  -A                            Set random vendor MAC of any kind
  -p,  --permanent              Reset to original, permanent hardware MAC
  -r,  --random                 Set fully random MAC
  -l,  --list[=keyword]         Print known vendors
  -b,  --bia                    Pretend to be a burned-in-address
  -m,  --mac=XX:XX:XX:XX:XX:XX
       --mac XX:XX:XX:XX:XX:XX  Set the MAC XX:XX:XX:XX:XX:XX

Report bugs to https://github.com/alobbs/macchanger/issues

```
I will offer this much for you though, you will need to stop your network-manager first. My Wifi is listed as "wlp4s0"
Make your changes and restart network-manager.
And you can make it use a udev rule,  and have it run every time the network connects by using your udev rule.
EDIT:
Or just for a one off, without requiring ifconfig or ip a, or even macchanger:
```

sudo ip link set dev [interface_name] down
sudo ip link set dev [interface_name] address XX:XX:XX:XX:XX:XX
sudo ip link set dev [interface_name] up
```
I'm taking you in good faith, right???

---

