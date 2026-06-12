---
title: "[SOLVED] gutsy apache2  no longer starts"
date: 2008-05-16
forum: General Help
---

### Post by DantePasquale on 2008-05-16
Hi All,

I've got a weird problem. I'm running gutsy on my laptop and using it for web development. I could always connect using [http://localhost](http://localhost), but today I couldn't. I checked and no http processes are running. So I tried to start apache using ```
/etc/init.d/apache2 start
```. Here's what I see in the process list:

```
root      5970     1  0 22:33 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5971  5970  0 22:33 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5972  5970  0 22:33 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5973  5970  0 22:33 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5977  5970  0 22:33 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5978  5970  0 22:33 ?        00:00:00 /usr/sbin/apache2 -k start
```

netstat -tapn shows no listen on port :80
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -
```

I checked the config and see:

```
dante@dexter:/etc/init.d$ sudo apache2ctl -t
apache2: apr_sockaddr_info_get() failed for dexter
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
Syntax OK
```

I tried to uninstall using synaptics package manager and then re-install, but still the same results.

As usual with apache there is absolutely nothing logged, nothing in apache logs, nothing in syslog, in fact, nothing at all to disk!

gdb output of one of the processes:

```

Reading symbols from /usr/lib/apache2/modules/mod_cgi.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_cgi.so
Reading symbols from /usr/lib/apache2/modules/mod_dir.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_dir.so
Reading symbols from /usr/lib/apache2/modules/mod_env.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_env.so
Reading symbols from /usr/lib/apache2/modules/mod_mime.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_mime.so
Reading symbols from /usr/lib/apache2/modules/mod_negotiation.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_negotiation.so
Reading symbols from /usr/lib/apache2/modules/mod_setenvif.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_setenvif.so
Reading symbols from /usr/lib/apache2/modules/mod_status.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/apache2/modules/mod_status.so
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
```



Help!

---

### Post by rubicon on 2008-05-16
> **DantePasquale said:**
> 
netstat -tapn shows no listen on port :80
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     -                   
tcp        0      0 **0.0.0.0:80**              0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -
```

Oh really? ;)

> **DantePasquale said:**
> 
```
dante@dexter:/etc/init.d$ sudo apache2ctl -t
apache2: apr_sockaddr_info_get() failed for dexter
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
Syntax OK
```
Then google for "apr_sockaddr_info_get() failed", it will give you a lot of info, I promise.

---

### Post by DantePasquale on 2008-05-17
No Luck on the fixes found under google for the above. All have to do with setting fqdn of the server your are on and I did go about this, with the same results.

Besides, this worked for months and for some reason on May 16th was the last time it worked.

No changes were made to the server except to install wicd which *should* have nothing to do with this, but you never know.

Any other suggestions???

---

### Post by DantePasquale on 2008-05-18
More information ....

For some reason I can't ping localhost or ping the assigned IP address, 72.1.64.14X

I have no idea whats going on here. Something with routing possibly? I tried to ssh from another box to this one and get connection refused. I also tried ssh localhost and that timed out.

Assistance Needed as I can't figure out what's f'd up???

Thanks!!

/etc/hosts
```

127.0.0.1 localhost
#127.0.1.1 dexter.cocoanet.us dexter
74.1.46.173 dexter.cocoanet.us dexter

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback 
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

hostname output:

```
dante@dexter:~/Desktop$ hostname
dexter.cocoanet.us
dante@dexter:~/Desktop$ cat /etc/hostname
dexter.cocoanet.us
dante@dexter:~/Desktop$
```

---

### Post by DantePasquale on 2008-05-19
Well I found the problem, but don't know why this happened. The loopback interface was marked down somehow and running ifconfig lo up is all that it took to fix the apache issue. Now I have to figure out how/why this is happening and it happens after every reboot. Anyone know what circumstances cause lo to be marked down?

---

### Post by rubicon on 2008-05-19
> **DantePasquale said:**
> Well I found the problem, but don't know why this happened. The loopback interface was marked down somehow and running ifconfig lo up is all that it took to fix the apache issue. Now I have to figure out how/why this is happening and it happens after every reboot. Anyone know what circumstances cause lo to be marked down?
Yep, check your /etc/network/interfaces. Here's mine (important part highlighted):
```

# The loopback network interface
**auto lo**
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

[COLOR="Silver"]BTW, iface lo **inet** means protocol family and not that the interface would be used for internet access :P[/COLOR]

---

### Post by DantePasquale on 2008-05-20
Yeah, that's the problem. To get wicd to work, I had to delete the /etc/networking/interfaces file. Maybe I need to just put entries for loopback in and use wicd to setup the wireless. I'll give that a try and post the results.

---

