---
title: "Ubuntu Local Virtual Host Issues"
date: 2020-12-20
forum: General Help
---

### Post by sdsurfer on 2020-12-20
System 76 Gazelle
Ubuntu 18.04
WiFi connection 600 mbps DL NetGear C7000v2 5G
apache2 2.4.29 (Ubuntu built:  2020-08-12T21:33:25

**Synopsis: **I have set up and worked with localhost development for years, but in this case I will be working along, reloading pages, then out of nowhere "server cannot be reached" and I'm unable to get it back. No amount of reconfiguring, restarting, or rebooting seems to resolve it.What could I be doing wrong?

The odd thing is I have multiple sites in /var/www and when it breaks some of them are still working and some are not. Then out of the blue without explanation, it will begin working again (in direct proportion to the frustrated shouting at the computer? :-) )

I have multiple computers, this appears to be an issue just with this one computer (using it because it's the fastest.)  

For most of my local dev sites, I have used "sitename-dev" without an extension, has worked fine. Thinking that is the problem, I have reconfigured and added the .local extension as below. The details as of this moment:

/etc/hosts has 
```

127.0.0.1 sitename-dev.local
127.0.0.1 www.sitename-dev.local

```

I have the following config file in sites-available: sitename-dev.local.conf

Contents, comments removed:
```

<VirtualHost *:80>
        ServerAdmin admin@sitename-dev.local
        ServerName sitename-dev.local
        ServerAlias www.sitename-dev.local
        DocumentRoot /var/www/sitename.com
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```
I then run sudo a2ensite sitename-dev.local and restart apache. (also tried reload.)

I have a section in /etc/apache2/apache2.conf (that I know is unrelated, and I should probably just move into the sites-available conf)
```

<Directory /var/www/sitename.com/>
        Options Indexes FollowSymLinks
        AllowOverride AuthConfig FileInfo Indexes Limit Options=All,Multiviews
        Require all granted
</Directory>

```

I can ping the site.

```

ping sitename.local
(127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.063 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.081 ms

```

Any browser (tried multiple) "Server not Found."
Then, with one of the other localhost sites, it loads right up. 
I have tried clearing the network cache. Restarting network. Multiple browsers (FF and Chrome latest.) Released and refreshed the DNS cache. Changed IP in resolve.conf (I know, not supposed to.) Rebooted. Rebooted the router, run diagnostics on the router. Switched to the 2G connection in the WiFi.

What could I be missing? Thanks in advance.

---

### Post by TheFu on 2020-12-21
Doesn't apache require all site configuration files to end in .conf?

How is name resolution handled on your network?  Do you run DNS?
resolve.conf isn't the correct name of the file.  /etc/resolv.conf is, but it gets overwritten whenever resolvconf or systemd-resolved decides it is time.  If you want control over resolv.conf, you need to stop and "mask" both resolvconf and systemd-resolved.  Then you'll need to setup local name resolution or chrome, firefox won't pay attention.  Firefox has been rolling out DNS-over-HTTPS the last year, ignoring local OS settings.  They want to protect grandma, but this screws with people who run webapps on their LANs.  Android browers have ignored local /etc/hosts settings for years, only using DNS.  That is what finally got me to put a DNS server that I controlled onto my subnet.

.local stuff is using zeroconf, which can be great for people who don't know any better, but as a web-dev, you need real DNS.  I'm fairly confident this is the issue.

---

### Post by SeijiSensei on 2020-12-21
> **TheFu said:**
> Doesn't apache require all site configuration files to end in .conf?
I don't think so. The Include statement in httpd.conf tells Apache where to look for other configuration files. I have
```

Include sites.d/*.conf

```
at the end of my Apache configurations (on CentOS with a custom directory /etc/httpd/sites.d/, equivalent to /etc/apache2/sites-enabled/ on Ubuntu). I chose to use ".conf" in the file glob for consistency, but I could have used something else. From [https://httpd.apache.org/docs/2.4/mod/core.html#include](https://httpd.apache.org/docs/2.4/mod/core.html#include)
> we encourage you to use the wildcard syntax shown below, to include files that match a particular pattern, such as *.conf, for example.

---

### Post by TheFu on 2020-12-21
apache2.conf:
```
   IncludeOptional sites-enabled/*.conf
```
I vaguely remember when they made this change.  I barely use apache. Doubt the OP would have modified that setting, but we never know.

Plus, using wifi for a server can be flaky. Just depends on the local wifi interference.

In summary, 
[LIST]
[*]Using sites-available/sitename-dev.local.conf
[*]Using /etc/hosts for name resolution using the localhost IP address
[*]Using zeroconf hostnaming conventions - i.e. .local at the end, but it doesn't match what mDNS/avahi would broadcast (hostname.local)
[*]No local DNS used
[*]Firefox and Chrome browsers having issues, sometimes
[*]Wifi connection
[/LIST]

My thoughts:
a) don't use wifi. wifi is almost always a bad idea for any server.
b) change the /etc/hosts to use 127.0.1.1 and 127.0.2.2 for the different names - this is just a guess. I'd actually use the LAN IP if it was me, not any on the localhost subnet (127.0.0.0/8). Many programs treat 127.0.0.0/8 as special. [https://askubuntu.com/questions/1207293/browsers-cant-access-127-0-0-1-but-works-from-terminal](https://askubuntu.com/questions/1207293/browsers-cant-access-127-0-0-1-but-works-from-terminal)
c) disable mDNS/avahi/zeroconf, if it is installed and running.
d) setup a LAN DNS server to resolve all local systems on the LAN.  My pi-hole does this and more.
e) Check whether chrome/firefox are using internal DNS choices and ignoring /etc/hosts completely. 
[LIST]
[*][https://stackoverflow.com/questions/42636711/google-chrome-ignoring-hosts-file](https://stackoverflow.com/questions/42636711/google-chrome-ignoring-hosts-file)
[*][https://support.mozilla.org/en-US/questions/1286880](https://support.mozilla.org/en-US/questions/1286880)
[/LIST]

That's all I got.

---

### Post by sdsurfer on 2020-12-21
Thank you for your replies - yes that was a typo, it is resolv.conf. That (I believe?) is used differently than the sites-available .conf's. In any case, yes, all my sites-available files end in .conf. (siteone-dev.com.conf, sitetwo.com.conf, tests.com.conf)

Unfortunately I'm all out of ethernet ports, WiFi is the only choice on this one. Lot of info to digest and will chase all these down. First I'll try the hosts, I've got them all set to 127.0.0.1.

There is another **different** issue, probably related, I didn't bring up to avoid confusing the question but it may be relevant. In this case, it's accessing the live site - let's call it sitename-live.com. There are three sites hosted on a Godaddy VPS, of the three I only have issues with this one. It is a similar situation, on other computers in the house we can browse to it fine, but on this one computer, it comes and goes, after it was working fine yesterday. Browse and "server could not be reached," ping = temporary failure in name resolution. 

I know it's bad mojo but I modified resolv.conf again as follows and pings and it comes up fine.

```

sudo nano /etc/resolv.conf

```
```

#nameserver 127.0.0.53
nameserver 8.8.8.8

```

```

sudo systemctl restart systemd-resolved.service

```

I know this is wrong, but it works every. single. time. Can now ping and browse to the site. Of course, it gets overwritten on every reboot.

I haven't checked where the resolver gets 127.0.0.53, but this is the same value in resolv.conf on all my computers. Will look at that too.

**added:** forgot to mention I have another solved thread here that had an issue with FF and localhost servers. That was resolved by disabling DNS over HTTPS and the Cloudflare selection, it is set to no proxy. Kinda moot, because my first go-to is try Chrome and results are the same when it happens.

I think it's the WiFi, but that may just be my tin foil hat talking.

---

### Post by sdsurfer on 2021-01-26
Sorry, been away updating a site and it has been all-encompassing. During that time this has come up again and again, with a clarification: the local "dev" sites I have configured for apache are fine, it is always the external sites that cannot be reached. The above hack is the only thing that "fixes" it but of course is overwritten with every reboot.

**New information, it has now affected one of my hard-wired  ethernet machines.** The same fix resolves it. I'd thought it was  wifi, but no, this machine is hardwired with 1000mbps ethernet.

I suspect it is the nameserver generated by Network Manager, or something in the system identifies "itself" as a nameserver, I am clueless as to what that is. On both machines it's always 127.0.0.53.

---

### Post by SeijiSensei on 2021-01-27
Recent Ubuntu releases use systemd-resolved for name resolution. That listens on the address 127.0.0.53 which is why you see that address in /etc/resolv.conf.

You can configure static server addresses in /etc/systemd/resolved.conf.  Add them to the "DNS" line like this:

```

[Resolve]
DNS=192.168.100.100 
FallbackDNS=8.8.8.8

```

The first is the server on my local network; the second is Google's. After you add the IPs to this file, restart systemd-resolved as you did before.

---

### Post by sdsurfer on 2021-02-02
Awesome, thank you! Mine is empty and commented:
```

[Resolve]
#DNS=
#FallbackDNS=
#Domains=
#LLMNR=no
#MulticastDNS=no
#DNSSEC=no
#Cache=yes
#DNSStubListener=yes

```

Going to try just fallback DNS at first and see if it sticks. Still makes me wonder what's wrong with 127.0.0.53. I'll boot up, it's fine for a while, then out of nowhere "temporary failure in name resolution." The hack above fixes it consistently.

---

### Post by sdsurfer on 2021-02-02
Hope springs eternal, but it didn't work. I first tried 8.8.8.8 as the fallback, undid my change to resolv.conf, fail. Went back and added 127.0.0.53, then 192.168.100.100 for DNS, fail. This is the only thing that works but is overwritten with every reboot.

```

sudo nano /etc/resolv.conf

#nameserver 127.0.0.53
nameserver 8.8.8.8

sudo systemctl restart systemd-resolved.service

```

---

### Post by sdsurfer on 2021-02-02
I think I may have it! Still doesn't tell "what's wrong with the local name server" but found an article on tecmint outlined as below (no link in case it becomes outdated: )

```

sudo nano /etc/resolvconf/resolv.conf.d/head

```


add nameservers there. It has the same warning not to edit and will be overwritten, but so far it is not. Revert /etc/resolv.conf back to its original state or leave it empty, see note below.

```

nameserver 8.8.8.8
nameserver 127.0.0.53
 
```
 
The article says to run
```

sudo systemctl restart systemd-resolved.service

```

And it is supposed to permanently store the nameservers in /etc/resolv.conf but my case this had no effect. I had to reboot and it worked.

I had left 127.0.0.53 in my original /etc/resolv.conf, so now it has two lines for 127.0.0.53, I suspect leaving it blank and going through this process will just set one.

```

nameserver 8.8.8.8
nameserver 127.0.0.53
nameserver 127.0.0.53

```

I'll play with it over the rest of the week, but if this causes it to "stick," we can finally mark this (sorta) resolved. I say sorta because 127.0.0.53 should work, something is breaking it.

---

### Post by SeijiSensei on 2021-02-04
I don't know if systemd-resolved pays attention to the FallbackDNS directive without a primary server in the DNS line.

---

