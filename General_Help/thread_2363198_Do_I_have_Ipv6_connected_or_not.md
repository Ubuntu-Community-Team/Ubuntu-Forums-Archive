---
title: "Do I have Ipv6 connected or not"
date: 2017-06-07
forum: General Help
---

### Post by s9032g@comcast.net on 2017-06-07
If I have Ipv6 connected, then how do I shut it off. Not obvious in Xubuntu

steven@steven-Latitude-E7240:~$ lsmod | grep ip6
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
ip6t_rt                16384  3
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
x_tables               36864  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
steven@steven-Latitude-E7240:~$ 


Thanks

---

### Post by deadflowr on 2017-06-07
This should still work on 16.04:
[https://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04]("https://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04")

---

### Post by s9032g@comcast.net on 2017-06-07
When I run sudo sysctl -p  this is all i get    
vm.swappiness = 10



I think that Xubuntu may not use Grub?? So again Do I have ipv6 or not. If so how di I shut it off?

---

### Post by cariboo on 2017-06-07
> **s9032g@comcast.net said:**
> When I run sudo sysctl -p  this is all i get    
vm.swappiness = 10



I think that Xubuntu may not use Grub?? So again Do I have ipv6 or not. If so how di I shut it off?

Using Xubuntu here, and it certainly does use grub. If you need to edit /etc/sysctl.conf you need to use the following command:

```
sudo nano /etc/sysctl.conf
```

---

### Post by s9032g@comcast.net on 2017-06-09
OK. I saw discussions about adding Grub to Xubuntu - so I assumed.

Heres my output:      Now, Do I have ipv6? How can I disable it?                                          f                                                                                                         


```
#  File: /etc/sysctl.con
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See [http://lwn.net/Articles/277146/](http://lwn.net/Articles/277146/)
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)

^G Get Help      ^O Write Out     ^W Where Is      ^K Cut Text      ^J Justify       ^C Cur Pos       ^Y Prev Page     M-\ First Line   M-W WhereIs Next ^^ Mark Text     M-} Indent Text
^X Exit          ^R Read File     ^\ Replace       ^U Uncut Text    ^T To Spell      ^_ Go To Line    ^V Next Page     M-/ Last Line    M-] To Bracket   M-^ Copy Text    M-{ Unindent Text
```
my output from the suggestion:

---

### Post by deadflowr on 2017-06-09
From your output of the /etc/sysctl.conf file it seems you never added the three lines from the link.
Basically re-open the file as suggested by cariboo and paste in the following three lines
```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```
(It's usually best to place these lines at the bottom of the file, so they will be easy to find if you need to later on, imo)

then click on ctrl + x to save and exit.
(typically just click ctrl +x then hit enter and then enter.
the first enter press accepts that you want to change the file and the second enter press asks where and what to save it as; unless you've accidentally hit a button or two the location will be whatever it was when you opened the file)

---

### Post by s9032g@comcast.net on 2017-06-10
Ok I did the above. I see the lines suggested by deadflowr in my terminal. However I think that I still have ipv6 active based on this output from ifconfig
steven@steven-Latitude-E7240:~$ sudo ifconfig
[sudo] password for steven: 
eno1      Link encap:Ethernet  HWaddr ec:f4:bb:3a:3f:4e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7e00000-f7e20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:63566 (63.5 KB)  TX bytes:63566 (63.5 KB)

wlp2s0    Link encap:Ethernet  HWaddr 7c:5c:f8:e4:ce:1a  
          inet addr:10.0.0.9  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:402:502:afb0:3c48:58d5:5284:fb64/64 Scope:Global
          inet6 addr: 2601:402:502:7ed0:7e5c:f8ff:fee4:ce1a/128 Scope:Global
          inet6 addr: 2601:402:502:afb0:5178:6131:7517:647/64 Scope:Global
          inet6 addr: fe80::6cd7:5277:d55f:dadc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1716750 (1.7 MB)  TX bytes:359103 (359.1 KB)

THE inet 6 and Scope are in the same line.

---

### Post by cariboo on 2017-06-10
Did you restart the system after the changes were made? You could also try:

```
sudo systemctl restart networking.service
```

---

### Post by wildmanne39 on 2017-06-10
If you continue to have trouble the easy way is to go into network manager and set IPV6 to ignore as shown in the screenshot.

In dmesg you will still see messages about IPV6 but it is turned off by doing what I stated in network manager.

---

### Post by s9032g@comcast.net on 2017-06-12
cariboo & wildmanne39,

Thanks for sticking with me on this.

Yes I did a restart. Also tried the terminal command just now with no change in the output of ifconfig.

Xubuntu does not have a network manager that offers a simple uncheck of IPV6. Therein is the problem.

---

### Post by s9032g@comcast.net on 2017-06-15
I give up

---

### Post by oldos2er on 2017-06-15
Why is this thread marked solved?

Xubuntu's network manager icon is in the panel; either right- or left-click on it to bring it up.

---

