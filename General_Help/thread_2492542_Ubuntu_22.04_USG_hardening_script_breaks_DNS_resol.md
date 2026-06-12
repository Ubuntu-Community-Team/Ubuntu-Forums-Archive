---
title: "Ubuntu 22.04 USG hardening script breaks DNS resolution"
date: 2023-11-14
forum: General Help
---

### Post by jobet on 2023-11-14
[COLOR=#0C0D0E][FONT=-apple-system]Since a few days, I noticed that running USG hardening tool on a freshly installed Ubuntu 22.04 server, breaks DNS resolution. Running for example dig google.com throws out an error:[/FONT][/COLOR]
```
;; communications error to 127.0.0.53#53: timed out
;; communications error to 127.0.0.53#53: timed out
;; communications error to 127.0.0.53#53: timed out

; <<>> DiG 9.18.18-0ubuntu0.22.04.1-Ubuntu <<>> google.com
;; global options: +cmd
;; no servers could be reached

```[COLOR=#0C0D0E][FONT=-apple-system]I looked up almost every DNS setting in this server, and read several DNS troubleshoot tutorials, but haven't found a fix yet. I also compared this server to another one running the same configuration (22.04 and hardened with USG module), and the only difference I've noticed so far is that in the output of resolvectl the line Current DNS Server: 2a01:4ff:ff00::add:1 is missing:[/FONT][/COLOR]
```
Link 2 (eth0)
Current Scopes: DNS
     Protocols: +DefaultRoute +LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
   DNS Servers: 2a01:4ff:ff00::add:1 2a01:4ff:ff00::add:2 185.12.64.1 185.12.64.2

```[COLOR=#0C0D0E][FONT=-apple-system]

Any advice will be much appreciated.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2023-11-14
Does whatever you installed include a firewall? Is it blocking queries on TCP and UDP port 53?

---

### Post by MAFoElffen on 2023-11-14
Yes. The "USG CIS compliance" script breaks DNS.

This post is where I came up with instructions on how to fix that, that keeps within compliance:
[https://ubuntuforums.org/showthread.php?t=2491597&p=14161501#post14161501](https://ubuntuforums.org/showthread.php?t=2491597&p=14161501#post14161501)

---

### Post by jobet on 2023-11-15
> **MAFoElffen said:**
> Yes. The "USG CIS compliance" script breaks DNS.

This post is where I came up with instructions on how to fix that, that keeps within compliance:
[https://ubuntuforums.org/showthread.php?t=2491597&p=14161501#post14161501](https://ubuntuforums.org/showthread.php?t=2491597&p=14161501#post14161501)

Hi MAFoElffen,

Thanks for your help. In fact as mentioned by [COLOR=#000000]richard378, the issue is because nftables firewall is enabled by the USG script with the following rules
[/COLOR]```
table inet filter {
    chain input {
        type filter hook input priority filter; policy accept;
        ip saddr 127.0.0.0/8 counter packets 2414 bytes 173734 drop
        iif "lo" accept
        ip6 saddr ::1 counter packets 0 bytes 0 drop
    }


    chain forward {
        type filter hook forward priority filter; policy accept;
    }


    chain output {
        type filter hook output priority filter; policy accept;
    }
}

```[COLOR=#000000]

I must say not very clever, as it blocks traffic to port 127.0.0.1:53 where Ubuntu forwards its DNS resolution requests...

As I haven't learned yet how to use nftables, I ran ```
sudo systemctl disable nftables
``` stop the service and then uninstalled it.

Everything is working fine now!

Thanks again for pointing me to the right direction!

Cheers

[/COLOR]

---

### Post by MAFoElffen on 2023-11-16
In the USG CIS / DISA STIG script, it installed nftables, but it is not configured. Thank you for noticing that. You are right. But it installed "that" to comply with certain things... (See the quote from the STIG below) Uninstalling that, then you are running it without any firewall at all. Seems to me that would not be compliant again right? (No firewall or iptable rules...)
> 
**The firewall must deny network communications traffic by default and allow network communications traffic by exception**  (i.e., deny all, permit by exception). To prevent malicious or  accidental leakage of traffic, organizations must implement a  deny-by-default security posture at the network perimeter.

You got DNS going again, but then are not compliant to the STIG again.

I played with it a bit differently and came up with this:
```

mafoelffen@usg-cis-ws1-01:~$ grep . /etc/nftables.conf
#!/usr/sbin/nft -f
flush ruleset
table inet filter {
    chain input {
        type filter hook input priority 0;
    }
    chain forward {
        type filter hook forward priority 0;
    }
    chain output {
        type filter hook output priority 0;
    }
}
include "/etc/inet-filter.rules"

mafoelffen@usg-cis-ws1-01:~$ sudo grep . /etc/inet-filter.rules
table inet filter {
    chain input {
        type filter hook input priority filter; policy accept;
        ip saddr 127.0.0.0/8 counter packets 0 bytes 0 drop
        iif "lo" accept
        ip6 saddr ::1 counter packets 0 bytes 0 drop
                ip protocol tcp ct state established accept
                ip protocol udp ct state established accept
                ip protocol icmp ct state established accept
                tcp dport 53 accept
                udp dport 53 accept
    }
    chain forward {
        type filter hook forward priority filter; policy accept;
    }
    chain output {
        type filter hook output priority filter; policy accept;
        ip protocol tcp ct state established,related,new accept
        ip protocol udp ct state established,related,new accept
        ip protocol icmp ct state established,related,new accept
                tcp dport 80 accept
                tcp dport 443 accept
        udp dport 53 accept
        tcp dport 53 accept
    }
}

mafoelffen@usg-cis-ws1-01:~$ sudo ls -l /etc/resolv.conf
lrwxrwxrwx 1 root root 32 Nov 15 21:48 /etc/resolv.conf -> /run/systemd/resolve/resolv.conf

```
I did these rules, then save them to the nftables
```

sudo nft add rule inet filter input ip protocol udp ct state established accept
sudo nft add rule inet filter input ip protocol icmp ct state established accept
sudo nft add rule inet filter output ip protocol tcp ct state new,related,established accept
sudo nft add rule inet filter output ip protocol udp ct state new,related,established accept
sudo nft add rule inet filter output ip protocol icmp ct state new,related,established accept
sudo nft add rule inet filter input udp dport 53 accept
sudo nft add rule inet filter input tcp dport 53 accept
sudo nft add rule inet filter output udp dport 53 accept
sudo nft add rule inet filter output tcp dport 53 accept

```
It still didn't work until I updated the symlink for /etc/resolv.conf
```

sudo rm -f /etc/resolv.conf
sudo ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf

```
If that works for you, then I will submit a bug report (myself) to the security team to patch their script...

---

### Post by MAFoElffen on 2023-11-16
I reran the script after those changes. It meets STIG compliance and still has DNS.

Filed the Bug Report: [https://bugs.launchpad.net/ubuntu-pro/+bug/2043651](https://bugs.launchpad.net/ubuntu-pro/+bug/2043651)

---

