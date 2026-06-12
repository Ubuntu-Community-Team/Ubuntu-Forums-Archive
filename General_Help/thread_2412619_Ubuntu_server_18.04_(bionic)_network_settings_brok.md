---
title: "Ubuntu server 18.04 (bionic) network settings broken after power cycle"
date: 2019-02-15
forum: General Help
---

### Post by slafazan on 2019-02-15
[COLOR=#242729][FONT=Arial]Networking was fine before reboot. After reboot, the system and all network settings are incorrect.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Notes:[/FONT][/COLOR]

[LIST]
[*]Ubuntu Server 18.04 (Bionic)
[*]Canonical livepatch was set up a few days ago.
[*]The new network thingy, netplan, doesn't seem to be installed (however there is a file /etc/netplan/50-cloud-init.yaml)
[*]The machine does seem to acquire a DHCP lease with the router (will connect over ethernet, with ip address 192.168.1.29).
[*]The enp7s0 interface (which I believe is the desired connecting device) is DOWN on boot. Manually bringing up the enp7s0 interface allows connection to router:
[*]/etc/resolv.conf is symlinked to a /run/systemd/resolve/stub-resolv.conf file. When I update it manually with nameserver 192.168.1.1 it works.
[/LIST]
ping 192.168.1.1
connect: Network is unreachable

ping google.com
ping: google.com: System error

dig google.com
connection timed out ...
...

ipconfig enp7s0 192.168.1.29 netmask 255.255.255.0 broadcast 192.168.1.255
ipconfig enp7s0 up
ping 192.168.1.1
64 bytes from 192.168.1.1: ...
64 bytes from 192.168.1.1: ...
64 bytes from 192.168.1.1: ...

nslookup google.com
Server:   192.168.1.1
Address:  192.168.1.1#53

Non-authoritative answer:
Name google.com
Address 172.217.164.110


systemd-resolve google.com
google.com: 216.58.195.238


-- Information acquired via protocol DNS in 3.0494s.
-- Data is authenticated: no

...

ping google.com
ping: google.com: System error # ... still network issue, most tools do not resolve hosts

[COLOR=#242729][FONT=Arial]I've also tried configuring /etc/resolv.conf /etc/nsswitch.conf to no avail.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]And on reboot, it seems that the network managers, maybe systemd-networkd and systemd-resolved reset some of the /etc files to settings that don't work.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Does anyone have a thought for what happened? I can post logs or whatever can help diagnose.[/FONT][/COLOR]

---

### Post by wildtiger23 on 2019-02-18
Same for me, no matter what I tried... my dns refuse to read my hosts table andd has a consequences I can't configured I nginx test environment.

---

### Post by slafazan on 2019-02-20
I investigated the issue on my own -- it seems that a Canonical Livepatch failed on my machine (I haven't found the root cause yet). When it failed, it had only partially applied updates to cloud-init, and while netplan was not installed, many network settings had been changed to assume it was. This left multiple network configurations in a partially migrated state. While I was able to restore some network connectivity by manually changing settings, the work involved with finding and configuring them was astronomical, and many changes were not persistent without a boot script. The most reasonable solution I found was to reinstall the operating system and disable Canonical Livepatch.


If it is indeed a network configuration patch for 18.04 that caused this, @Canonical should remember that 18.04 is designated LTS -- the live patching should NOT under any circumstances apply updates that risk loss of network settings for LTS servers. If this is the case, it is extremely careless behavior. If anyone from Canonical reads this, I would appreciate any comment from someone with more knowledge of the Livepatch internals to confirm and assess root cause.

---

