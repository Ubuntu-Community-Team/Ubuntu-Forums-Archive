---
title: "apt-get not downloading after ISP change"
date: 2008-01-30
forum: General Help
---

### Post by VolvoPunch on 2008-01-30
Well I recently changed ISP's from ComCrap to BellSouth DSL. I had some problems getting my web server to work though them but managed to log into the model and disable to firewall so ssh and apache are good now. But after changing isp I can no longer download new software of get updates using apt-get. It just hangs on the connection and never connects. I know the box has internet because I can view the site over the net so why would this be happening? I have rebooted the system but nothing seems to have help. Any ideas on why apt-get is not working?

---

### Post by VolvoPunch on 2008-01-31
I have not gotten a response yet. Did I put this in the right section of the forum?

---

### Post by seventhc on 2008-01-31
Do you get any errors?

---

### Post by linksolo74 on 2008-01-31
I would call you ISP if i were you.

---

### Post by dcstar on 2008-01-31
> **VolvoPunch said:**
> Well I recently changed ISP's from ComCrap to BellSouth DSL. I had some problems getting my web server to work though them but managed to log into the model and disable to firewall so ssh and apache are good now. But after changing isp I can no longer download new software of get updates using apt-get. It just hangs on the connection and never connects. I know the box has internet because I can view the site over the net so why would this be happening? I have rebooted the system but nothing seems to have help. Any ideas on why apt-get is not working?

Has there been a Proxy setting change?, if so you have to have the correct settings in Synaptic to be able to fetch packages.

---

### Post by VolvoPunch on 2008-01-31
Alright here is a little print out of my problem

```

root@atlbricks:/home/systemadmin# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:9D:49:09:46
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe49:946/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20204475 (19.2 MB)  TX bytes:70858123 (67.5 MB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:946604 (924.4 KB)  TX bytes:946604 (924.4 KB)

root@atlbricks:/home/systemadmin# apt-get install php5-gd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpcap0.7
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgd2-xpm
Suggested packages:
  libgd-tools
The following NEW packages will be installed:
  libgd2-xpm php5-gd
0 upgraded, 2 newly installed, 0 to remove and 11 not upgraded.
Need to get 353kB of archives.
After unpacking 938kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libgd2-xpm php5-gd
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com gutsy-updates/main libgd2-xpm 2.0.34-1ubuntu1.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy-updates/main php5-gd 5.2.3-1ubuntu6.3
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/main libgd2-xpm 2.0.34-1ubuntu1.1
  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.34-1ubuntu1.1_i386.deb  Could not resolve 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.3-1ubuntu6.3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@atlbricks:/home/systemadmin# apt-get update
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Err http://security.ubuntu.com gutsy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com gutsy/main Translation-en_US

```

Well thats what  am dealing with, I am not running a proxy, I have not called the ISP because I think once I say Linux the will just give me the "We don't support that message" so I am stuck atm. :(

---

### Post by scizzo on 2008-01-31
Well they do support the fact that they are the ISP so the network itself they should support even if you are running Solaris.

Now to look at those errors it seems that the host "  Could not resolve 'us.archive.ubuntu.com'"

Have you tried other links also?

please check if you can go out with a browser as normal from the ISP also however you have posted here so I am guessing that is no problem.

My suggestion is to try another link to archives.

---

### Post by VolvoPunch on 2008-01-31
> **scizzo said:**
> Well they do support the fact that they are the ISP so the network itself they should support even if you are running Solaris.

Now to look at those errors it seems that the host "  Could not resolve 'us.archive.ubuntu.com'"

Have you tried other links also?

please check if you can go out with a browser as normal from the ISP also however you have posted here so I am guessing that is no problem.

My suggestion is to try another link to archives.

Do you have an alternative source link file? I don't have a running GUI at the moment, I use ssh to connect to the box. It basically runs as a web server. [http://www.atlbricks.com/](http://www.atlbricks.com/) is the box that I having problems with so if I can connect to it over the net I would think I should be able to download updates. This problem accrued right after switching ISP's.

---

### Post by VolvoPunch on 2008-02-02
Alright I have tried several sources changes, none of them will update.  What the heck is going on here? Please someone I need your advice and help on this because I have no idea. I change ips's and this happens. :confused:

---

### Post by seventhc on 2008-02-02
This may sound stupid, but I once had a similar problem, and it was b/c the date on my comp was wrong...off by 1 year so the certificates weren't read correctly, or not at all. can't hurt to double check your time/date settings.

---

### Post by Zack McCool on 2008-02-02
> **VolvoPunch said:**
> Do you have an alternative source link file? I don't have a running GUI at the moment, I use ssh to connect to the box. It basically runs as a web server. [http://www.atlbricks.com/](http://www.atlbricks.com/) is the box that I having problems with so if I can connect to it over the net I would think I should be able to download updates. This problem accrued right after switching ISP's.

After you switched ISP's, did you change the DNS servers you are using?  From the box, can you ping ubuntu.com?  Can you ping anything by name?

If you didn't change your DNS server entries, it would explain why you cannot resolve these hostnames...

---

### Post by dcstar on 2008-02-02
> **Zack McCool said:**
> After you switched ISP's, did you change the DNS servers you are using?  From the box, can you ping ubuntu.com?  Can you ping anything by name?

If you didn't change your DNS server entries, it would explain why you cannot resolve these hostnames...

Exactly, the web browser is probably caching DNS entries so that is why it still works ..... for the moment.......

---

### Post by Zack McCool on 2008-02-02
> **dcstar said:**
> Exactly, the web browser is probably caching DNS entries so that is why it still works ..... for the moment.......

I don't think there is a web browser.  It is a remote server that he is ssh-ing into.

---

### Post by dcstar on 2008-02-02
> **Zack McCool said:**
> I don't think there is a web browser.  It is a remote server that he is ssh-ing into.

You're right, he can get into it but it can't resolve DNS - and being a server it won't be using DHCP so a bad DNS server entry looks the most likely culprit.

---

### Post by VolvoPunch on 2008-02-04
Um I am still a bit in experience within the Linux world so if someone would guild be a bit more that would be great. I have Bell South DSL (192.168.0.254?) running into a D-Link WiFi router (192.168.0.1), the Linux box is hard wired to the router. I have setup for the Linux to have a static ip in the router and the Linux box. The router does not have a specified DNS server so I would expect that its automatically getting it from the DSL modem. I check the date and time and its correct also.


This is my current interfaces file setup, what should it look like? Is this correct? 
/etc/network/interfaces
```

auto lo
iface lo inet loopback


iface eth0 inet static
        address 192.168.0.110
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

auto eth0

```

Thanks again for all the helpful comments and advice! ):P

---

### Post by VolvoPunch on 2008-02-04
^Is that the correct file to change the DNS?

---

### Post by VolvoPunch on 2008-02-05
Could I get someone to help me out with this? :confused:

---

### Post by VolvoPunch on 2008-02-06
Where did everyone go? :(

---

### Post by Zack McCool on 2008-02-07
Nameservers are defined in /etc/resolv.conf

Most routers will pass DNS requests to the upstream provider, provided they are getting one in the DHCP response, so 192.168.0.1 should work.  If not, connect to your router, and check to see what it is getting as the DNS entries, and try using those.

nameserver 192.168.0.1

---

### Post by VolvoPunch on 2008-02-07
> **Zack McCool said:**
> Nameservers are defined in /etc/resolv.conf

Most routers will pass DNS requests to the upstream provider, provided they are getting one in the DHCP response, so 192.168.0.1 should work.  If not, connect to your router, and check to see what it is getting as the DNS entries, and try using those.

nameserver 192.168.0.1

:):guitar::KS THANK YOU! I was able to see that the server was still using the old DNS server at ComCrap, got the AT&T dns ip and now everything is fly. Thanks a buch!

---

### Post by Zack McCool on 2008-02-07
Glad I could help.  Now, if you could, it would be a good idea to mark the thread as solved, so that it may help others in the future...   ;)

---

