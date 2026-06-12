---
title: "dnsmasq, systemd-resolved etc"
date: 2020-07-04
forum: General Help
---

### Post by apg6xswhjc on 2020-07-04
I'm running 20.04 (up to date) on my laptop. Initial install was 19.04, and have upgraded at each release since then.

While everything seems to be running fine, I've found some log errors from dnsmasq.

systemctl status dnsmasq shows:

```

 dnsmasq.service - dnsmasq - A lightweight DHCP and caching DNS server
     Loaded: loaded (/lib/systemd/system/dnsmasq.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Sun 2020-07-05 10:01:42 AEST; 1h 37min ago
    Process: 1395 ExecStartPre=/usr/sbin/dnsmasq --test (code=exited, status=0/SUCCESS)
    Process: 1427 ExecStart=/etc/init.d/dnsmasq systemd-exec (code=exited, status=2)

Jul 05 10:01:41 dbUbuntu systemd[1]: Starting dnsmasq - A lightweight DHCP and caching DNS server...
Jul 05 10:01:41 dbUbuntu dnsmasq[1395]: dnsmasq: syntax check OK.
Jul 05 10:01:42 dbUbuntu dnsmasq[1427]: dnsmasq: failed to create listening socket for port 53: Address already in use
Jul 05 10:01:42 dbUbuntu dnsmasq[1427]: failed to create listening socket for port 53: Address already in use
Jul 05 10:01:42 dbUbuntu dnsmasq[1427]: FAILED to start up
Jul 05 10:01:42 dbUbuntu systemd[1]: dnsmasq.service: Control process exited, code=exited, status=2/INVALIDARGUMENT
Jul 05 10:01:42 dbUbuntu systemd[1]: dnsmasq.service: Failed with result 'exit-code'.
Jul 05 10:01:42 dbUbuntu systemd[1]: Failed to start dnsmasq - A lightweight DHCP and caching DNS server.

```

sudo netstat -ntlp | grep LISTEN shows that systemd-resolved is using port 53.

But searching around, I found different information from various Ubuntu versions etc about whether dnsmasq is required or not - even some saying it was required by NetworkManager, mention of resolvconf etc.

So, I'm confused about what the correct setup *should* be for 20.04? And to get to that correct setup, should I just disable the dnsmasq service?

---

### Post by &amp;KyT$0P# on 2020-07-04
> **apg6xswhjc said:**
>  whether dnsmasq is required or not - even some saying it was required by NetworkManager, 

That is no longer true.

> what the correct setup should be for 20.04? And to get to that correct setup, 

The answer to this question is "whatever works for you".

20.04 stock setup has NetworkManager using [FONT=Courier New]systemd-resolved[/FONT] .  Do you have a specific reason to need something else for DNS?

---

### Post by webaake on 2020-07-05
I ditched systemd-resolved a long time ago. It really slowed the DNS searches a lot and slowed down boot too. 

It is possible to disable systemd-resolved and go back to true and tested practices. How-to: [https://gist.github.com/zoilomora/f7d264cefbb589f3f1b1fc2cea2c844c](https://gist.github.com/zoilomora/f7d264cefbb589f3f1b1fc2cea2c844c)

In fact systemd-resolved was the last straw that made me look for distros completely without systemd. And I've found PCLinuxOS and converted several machines to that. My main machine will be migrated from Ubuntu to PCLOS in time too.

---

### Post by apg6xswhjc on 2020-07-07
> **halogen2 said:**
> 
20.04 stock setup has NetworkManager using [FONT=Courier New]systemd-resolved[/FONT] .  Do you have a specific reason to need something else for DNS?

Well, to be frank, I really don't know, as I may have installed something that requires it? I'd like to stick to stock as much as possible. I'm not interested in running a DNS server on this laptop, as it's just a client. It just gets it's DNS resolution from the router.  /etc/resolv.conf I understood. All this stuff now??? Meh....

When I do an apt-cache rdepends dnsmasq, it lists resolvconf and vpnc-scripts amongst others, and those rdepend to a bunch of stuff, including various VPN stuff. I do use the Network Manager OpenVPN. So I assume I can't just remove them.

So, how can I prevent these errors?

---

### Post by &amp;KyT$0P# on 2020-07-07
> **apg6xswhjc said:**
> Well, to be frank, I really don't know, as I may have installed something that requires it? 

This should tell you what would happen if you removed it -
```
apt-get -s purge dnsmasq
```

> how can I prevent these errors?

If you're OK with what you see with the above command, can you just purge that package for real?  I use dnsmasq for DNS in 20.04, and I don't even have that service.

---

### Post by apg6xswhjc on 2020-07-07
```
$ apt-get -s purge dnsmasq
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dnsmasq*
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
Purg dnsmasq [2.80-1.1ubuntu1]

```

But:

```
$ sudo apt-cache rdepends dnsmasq
[sudo] password for dburt: 
dnsmasq
Reverse Depends:
  dnsmasq-utils
 |x2gothinclient-management
  vpnc-scripts
  resolvconf
  netscript-2.4
  ltsp
  dnsmasq-base-lua
  dnsmasq-base-lua
 |di-netboot-assistant
  di-netboot-assistant
  dbab
  dnsmasq-base
  dnsmasq-base

```

:S

---

### Post by &amp;KyT$0P# on 2020-07-07
That rdepends command isn't maximally helpful in these situations.  Try these instead -
```
apt-mark showmanual | grep -F dnsmasq
apt-cache rdepends --installed dnsmasq
```

---

### Post by apg6xswhjc on 2020-07-07
```
$apt-mark showmanual | grep -F dnsmasq
dnsmasq
```


```
$apt-cache rdepends --installed dnsmasq
dnsmasq
Reverse Depends:
  dnsmasq-base
  dnsmasq-base

```

---

### Post by &amp;KyT$0P# on 2020-07-07
If you don't know why you have that package, it's safe to remove.

---

### Post by SeijiSensei on 2020-07-08
I'd learn to live with systemd-resolved. It's going to be with us for years to come. You don't need dnsmasq, nor will it work properly on a system running systemd-resolved since that service will claim the DNS port 53.

You can specify static DNS servers by adding their IP addresses to the "DNS" and "FallbackDNS" lines in /etc/systemd/resolved.conf.  Works like a charm here. You'll need to restart the service after making the changes with "sudo systemctl restart systemd-resolved".

See "[man resolved.conf]("https://manpages.debian.org/testing/systemd/resolved.conf.5.en.html")" for more details.

---

### Post by apg6xswhjc on 2020-07-08
Bit the bullet and purged dnsmasq. Haven't run through everything, but I'm typing this on the internet, so at least ubuntuforums.org is being resolved :)

Thanks for your help! Feels so much better to ask and learn some more than blindly removing packages and crossing my fingers!

---

