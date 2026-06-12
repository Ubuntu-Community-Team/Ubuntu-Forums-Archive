---
title: "Problems with running a server from desktop?"
date: 2023-04-01
forum: General Help
---

### Post by zoomiest2 on 2023-04-01
I was planning on running a Nextcloud server - but I can't run it from my shared host (just tried).

Is there a known way to safely set up a webserver, and cordon it off, so you can also use the machine as a desktop?

I have just heard people discourage it, but I was hoping to benefit from the massive HDD sizes that can be purchased, the control of the local command line, and the cost savings, of not having to pay for hosting.

Any thoughts or specific warnings, that I should be aware of?

---

### Post by TheFu on 2023-04-01
Not without a virtual machine to my knowledge.  Running a network service that can be accessed over the internet on the same OS instance as is performing as a desktop is a terrible idea.

But if you want to run nextcloud just for use on your LAN (or use with a VPN or ssh-tunnel from the internet), then you could mitigate most risks by forcing a security network connection BEFORE any access to nextcloud would be possible.  

A few months ago, someone else asked about something similar and their was a long thread with pros/cons for allowing nextcloud to be accessed directly from the internet. There were different opinions on this.  I say, never allow a network service/website like that which could contain sensitive information to be accessed without a good VPN. The risks just aren't worth it.

Some light reading [https://ubuntu.com//blog/containerization-vs-virtualization](https://ubuntu.com//blog/containerization-vs-virtualization)

---

### Post by zoomiest2 on 2023-04-12
Thanks.
I picked up two 6TB drives to run my VMs on.

---

### Post by TheFu on 2023-04-13
> **zoomiest2 said:**
> Thanks.
I picked up two 6TB drives to run my VMs on.

Completely off topic, but many 6TB sized HDDs have poor reliability according to industry statistics.  Don't know why, but 4TB and 8TB disks have 50% fewer failures over time.  May want to consider this before you've gotten too tied to the storage.  There are also certain well-known brands that have statistically significantly worse reliability.  For me, if I can avoid issues that would take even 2 hrs of my time, it is worth spending $50 more for a more reliable device that I'll have for 5 - 10 yrs. All HDDs fail, eventually, but I'd rather they fail 2x+ longer than whatever warranty states.

---

### Post by ActionParsnip on 2023-04-13
The only difference between desktop and server is a graphical UI. You can run server services (like a web server) on a desktop OS. No problem

---

### Post by TheFu on 2023-04-13
> **ActionParsnip said:**
> The only difference between desktop and server is a graphical UI. You can run server services (like a web server) on a desktop OS. No problem

Mostly true. It is the integration between some services and the desktop that are involved too.  For example, servers don't usually have network-manager at all. They use netplan files to configure networking.  There are a few other things like that.

---

### Post by ActionParsnip on 2023-04-13
> **TheFu said:**
> Mostly true. It is the integration between some services and the desktop that are involved too.  For example, servers don't usually have network-manager at all. They use netplan files to configure networking.  There are a few other things like that.

You can use nmcli if you like

---

### Post by TheFu on 2023-04-13
> **ActionParsnip said:**
> You can use nmcli if you like

Very true.  Nearly any desktop program can be installed onto the server, assuming the admin knows about it.
OTOH, I purge everything related to network-manager from my systems after being burned by it about 10 yrs ago.  I purge and disable a number of "standard" services and either do without or replace them with better alternatives.  

For example, systemd-timed can't seem to keep time on my systems, so I use chrony instead.  msec accurate system clocks is a solved problem for 30 yrs, yet some people put up with having incorrect time on their computers for some reason. I've been fighting this since 1993 and I'm still shocked that MS-Windows can't keep time.

There are about 5 services with little issues like that in core Ubuntu.  Don't get me started about systemd-resolved/resolvconf.

---

### Post by SeijiSensei on 2023-04-13
If you want to put the server into a VM, I recommend using the built-in virtual machine provision in the Linux kernel rather than a separate application like VirtualBox.

[https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)

---

### Post by zoomiest2 on 2023-04-13
:( Oh, no. thank you. I haven't configured any systems on them yet. Thanks for letting me know. 
I will search up some reliability stats on what I purchased....

---

### Post by SeijiSensei on 2023-04-16
> **SeijiSensei said:**
> If you want to put the server into a VM, I recommend using the built-in virtual machine provision in the Linux kernel rather than a separate application like VirtualBox.

[https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)
I'm rescinding this piece of advice. Based on trying to create a 22.04 server as a KVM, I would choose VirtualBox. If you want to set up a server in a VM to support clients on your network, then you need to use "bridged networking." That networking mode gives the VM an IP address on the same network as its host. That enables the rest of the machines on your network to see it.

I tried following the steps to [set up bridged networking with KVM]("https://linuxconfig.org/how-to-use-bridged-networking-with-libvirt-and-kvm"). It isn't easy because it requires a lot of command-line steps to create the bridge on the host machine and connect to it from the guest. I've spent many, many hours typing commands into Linux boxes but decided building a KVM bridge wasn't worth the trouble. In the end I chose VirtualBox because you can specify bridged networking from a drop-down box when installing the VM.

---

### Post by Doug S on 2023-04-16
With apologies to the OP for pursuing this off topic item:

> **TheFu said:**
> Completely off topic, but many 6TB sized HDDs have poor reliability according to industry statistics.  Don't know why, but 4TB and 8TB disks have 50% fewer failures over time.

Hi TheFu,
Do you have a reference you can point us to? I was surprised by your comment, and could only find [this]("https://www.backblaze.com/blog/backblaze-drive-stats-for-2022/") really good article.

---

### Post by aljames2 on 2023-04-16
I host KVM from a Xubuntu desktop without any trouble.  It wasn't  that hard to set up the bridge (br0).  Once the bridge is in place, you  can select (br0) in the dropdown within Virt-Manager when installing a  new VM.  Since my host doesn't accept wireless connections and only  hosts VMs with static addresses, I took the approach of replacing  NetworkManager with networkd (YAML) file on my Xubuntu desktop.

I used this resource back when I set mine up which was helpful with replacing Network Manager on my desktop.  Relatively few steps if you want to go this route.  [https://www.configserverfirewall.com/ubuntu-linux/ubuntu-network-manager/](https://www.configserverfirewall.com/ubuntu-linux/ubuntu-network-manager/)

I suggest first
```
ip a
```
and make note of your ethernet/interface name.  Mine is (eno1)

Also, the example YAML file at /etc/netplan/ is inadequate.  Mine looks like this, but yours will be different of course:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: false
      dhcp6: false
  bridges:
    br0:
      interfaces: [eno1]
      addresses: [192.168.10.247/24]
      # gateway4 is deprecated, use routes instead
      routes:
      - to: default
        via: 192.168.10.1
        metric: 100
        on-link: true
      mtu: 1500
      nameservers:
        addresses: [192.168.10.1]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no

```

Make sure KVM and related packages are installed.  I also include virt-manager which is a gui that can be used to easily set up VMs.

Reboot & launch virt-manager.  When installing a new VM, you should see the bridge option in your network dropdown.

If you want to stick with NetworkManager on your KVM host desktop, I have my process somewhere for that which also works, at least in my case, but I don't use Network Manager on my kvm host anymore.

---

### Post by dragonfly41 on 2023-04-16
I throw ngrok into the ideas arena.
Or even launch Heroku instance.

---

### Post by TheFu on 2023-04-16
> **Doug S said:**
> With apologies to the OP for pursuing this off topic item:

Hi TheFu,
Do you have a reference you can point us to? I was surprised by your comment, and could only find [this]("https://www.backblaze.com/blog/backblaze-drive-stats-for-2022/") really good article.

Not anymore. I used to read the backblaze quarterly results.  There have been others.

It first came to light years ago and I haven't seen anything that says it is fixed.  I've been avoiding 3, 6, 9, 11, 13TB HDDs.  I buy only 4T and 8T HDDs, usually "Gold" (datacenter) or "Black" at this point for non-SSDs. 5+ warranty or better on a HDD is my minimal standard the last few years.

Additionally, I've been avoiding Seagate a few times after feeling "burned" by the company management due to lies.  I remember when the last Seagate 2TB died just short of the 1yr warranty period. I didn't bother getting a replacement and was just happy that ordeal was over.  I never, ever, plan to buy anything from Seagate again. There are a few companies on my "never again" list and fortunately, I'm in a position to follow those plans.  We each have different levels of hassles/lies we are willing to put up with.  

Some of the 14-16TB Seagate HDDs have been really tempting, but not enough that I'd get one.

---

### Post by SeijiSensei on 2023-04-19
I'm not interested in having to learn netplan just for one virtual server. I understand the steps involved. I'm just uninterested in going through all of that  to launch one server. 

My experience with Seagate drives has been better than that with drives from Western Digital. I have a 2 TB external about the size of a cigarette pack to which I have backed up my remote sites for years. I've even dropped the device a few times over the years. Nary a blip.

---

### Post by TheFu on 2023-04-19
I put off using netplan by staying on 18.04 for as long as possible.  Initially, netplan didn't handle some non-trivial setups that I needed, so I really didn't have much choice. By the fall of 2020, it finally did support those things.  Netplan is an Ubuntu Server thing, so the easiest way to avoid it is by using debian servers, which still use the "interfaces" file.

Another example of Canonical's "NIH" problem, I suppose.  Part of my likes YAML over the alternatives (xml/json), but time has proven that the format of the interfaces file did handle everything we needed AND lacked the stupid space sensitive aspect of YAML.

As for seagate - I used to seek them out and had good luck with their drives.  I still have a few 320GB and 300GB Seagates spinning today. They are 15-20 yrs old at this point.  Many people don't recall, but Seagate management lied for over a year about an engineering flaw in the 750G and larger HDDs.  They were failing at 4x the rate of all the other competition. Basically, those lies kept me away from Seagate for nearly a decade.  I broke down and bought 2 2TB Seagate SATA drives around 2010 because they were significantly cheaper than the competition.  Both of those drives failed  - one at 11 months and the other at 13 months.  I swore I'd never, ever, give seagate any money if I could help it.  When the 2nd HDD failed, I had a no-more-seagate party with my LUG.

I've been disappointed by a few other "quality" brands when their drives failed just after the 3 yr warranty ended.  For a HDD to be a "value" so me, it needs to last at least 5 yrs or 2x the warranty if it is shorter than 5 yrs.  

I've had Toshiba, Hitachi, Seagate, Maxtor, WD and a few other other HDDs here over many decades.  What I've learned is this. 
The drive makers really know their failure rates and set the warranty to reflect their confidence in the engineering. A drive with a 3 yr warranty is unlikely to make it 5 yrs, for example.  My "value" idea would dictate at least 6 yrs of use to avoid disappointment.  It is a low bar, in reality.
The hassle factor of a head HDD is greater than $50 to me, so if a HDD with a 5 yr warranty costs $50 more, it is well worth the expense, to me.  That means buying "data center" or true "WD Black" HDDs.  I've never had any "Black" HDD w/ a 5 yr warranty fail.  I have a 1TB WD-Black that is just starting to show failed sectors after 13 yrs of 24/7/365 use.  I have a few DC/Gold Hitachi/WD HDDs in service which are doing extremely well after 5 yrs of service life.  Got them used and the ones I didn't immediately return have no SMART data issues at all.  I've had them for 2 yrs now - still going great.

A few WD USB3 external drives are showing their issues recently.  I think it is the USB interface failing, not the actual HDDs inside.  Every few months, they will get an I/O error that can only be fixed by a full system reboot.  A power cycle of the drives themselves doesn't work, sadly.  The next time they fail, it will be time to "shuck" the HDDs from the USB enclosures. I expect to find some WD-Red NAS drives inside and have 2 slots in an external array waiting for them.  They are only for backups. I don't risk primary data on USB storage.

---

### Post by zoomiest2 on 2023-04-24
Do you think that VirtualBox is faster than KVM? (I was using KVM because I heard it was faster)

---

### Post by TheFu on 2023-04-24
> **zoomiest2 said:**
> Do you think that VirtualBox is faster than KVM? (I was using KVM because I heard it was faster)

KVM/QEMU is definitely faster for server workloads than Virtualbox.  It supports many more backend storage management methods, more complex networking, and allows failover (live migrations) if the storage is setup correctly).  

For someone really new to Linux and virtualbox makes setting up the most useful network modes easier. KVM doesn't really do network stuff. It is expected that the admin will setup any required networking outside the kvm/libvirt environment. For people unfamiliar with using network config files on Ubuntu (GUIs can't do it, to my knowledge), this could be a large hurdle.

Virtualbox is "easier", at least from the network setup perspective.  That's what I'm seeing in SeijiSensei's posts. I agree.  OTOH, here's an iperf3 test between 2 VMs on the same host:
```
$ iperf3 -s
warning: this system does not seem to support IPv6 - trying IPv4
-----------------------------------------------------------
Server listening on 5201
-----------------------------------------------------------
Accepted connection from 172.22.22.44, port 60926
[  5] local 172.22.22.3 port 5201 connected to 172.22.22.44 port 60930
[ ID] Interval           Transfer     Bitrate
[  5]   0.00-1.00   sec  5.69 GBytes  48.9 Gbits/sec                  
[  5]   1.00-2.00   sec  5.55 GBytes  47.7 Gbits/sec                  
[  5]   2.00-3.00   sec  5.73 GBytes  49.2 Gbits/sec                  
[  5]   3.00-4.00   sec  5.45 GBytes  46.8 Gbits/sec                  
[  5]   4.00-5.00   sec  5.50 GBytes  47.3 Gbits/sec                  
[  5]   5.00-6.00   sec  5.84 GBytes  50.1 Gbits/sec                  
[  5]   6.00-7.00   sec  6.25 GBytes  53.7 Gbits/sec                  
[  5]   7.00-8.00   sec  6.19 GBytes  53.2 Gbits/sec                  
[  5]   8.00-9.00   sec  6.46 GBytes  55.5 Gbits/sec                  
[  5]   9.00-10.00  sec  6.06 GBytes  52.1 Gbits/sec                  
[  5]  10.00-10.00  sec  1.93 MBytes  50.8 Gbits/sec                  
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate
[  5]   0.00-10.00  sec  58.7 GBytes  **50.5 Gbits/sec**                  receiver

```
So, 50 Gbps.  Not bad.  Would be interesting to see what virtualbox can achieve.  Typical numbers that I see for LAN traffic (going over wires) with GigE NICs is 920 Mbps - so about 50x faster.

---

