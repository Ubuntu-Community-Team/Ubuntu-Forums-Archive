---
title: "New hostname doesn't get applied"
date: 2015-08-11
forum: General Help
---

### Post by Mohonri on 2015-08-11
I'm trying to get a 14.04 box working, but I cannot get it to recognize the hostname I give it.  For example, when I SSH in, the prompt says 
```
root@(none):~#
```
/etc/hostname: (edited)
```
monitor.example.com
```

/etc/hosts: (again, edited)
```
127.0.0.1       localhost
127.0.1.1       monitor.example.com monitor

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Using the *hostname* command gives me no output (empty string).  Here are a few other things I've tried:
```
root@(none):~# hostname monitor
root@(none):~# hostname
root@(none):~#
```
```
root@(none):~# hostnamectl set-hostname monitor
root@(none):~# hostname
root@(none):~#
```
Rebooting, service hostname start, etc all have the same (lack of) effect.

Am I missing something here?  This is the one box (out of dozens that I administer) that has this problem.

---

### Post by ajgreeny on 2015-08-11
Does ```
cat /etc/hostname
``` in terminal show what you expect?

It may well be worth telling us what your hostname is, or what you have set it to be, just in case you have used any non-allowable characters such as an underscore.

I have also moved this thread to General as it is not specifically a Networking and Wireless problem.

---

### Post by Mohonri on 2015-08-11
Thanks for the move.   ```
root@(none):~# cat /etc/hostname
monitor
root@(none):~#
```I've also tried it with these contents:
```
root@(none):~# cat /etc/hostname
monitor.example.com
root@(none):~#
```

There's nothing unusual with the domain name itself--it's all letters, no numbers or other characters.

Actually, I just tried setting it to actually use "monitor.example.com", rather than our actual domain, and it didn't work.  So I switched it back to our own domain, and voila, it works.  Weird.

---

### Post by efflandt on 2015-08-11
As far as I know /etc/hostname should only contain your hostname, not a domain. Although, you can include a domain when using whitespace separated aliases in /etc/hosts. And you likely need to reboot for it to take effect.

See **man hostname** for more info.

Ubuntu typically runs avahi-daemon which automatically resolves a domain called .local using Apple zeroconfig technique (somewhat similar to Windows netbios names). For example **avahi-browse -art** will list everything that finds. My network printer shows up as lexmark-c543.local.```
efflandt@XPS-8100-1404:~$ wget -S -O /dev/null http://lexmark-c543.local/
--2015-08-11 15:29:59--  http://lexmark-c543.local/
Resolving lexmark-c543.local (lexmark-c543.local)... 172.16.0.69
Connecting to lexmark-c543.local (lexmark-c543.local)|172.16.0.69|:80... connected.
HTTP request sent, awaiting response... 
  HTTP/1.1 200 OK
  Connection: close
  Expires: Sun, 27 Feb 1972 08:00:00 GMT
  Pragma: no-cache
  Cache-Control: no-cache
  Content-Type: text/html
Length: unspecified [text/html]
Saving to: &#8216;/dev/null&#8217;

    [ <=>                                                                                       ] 1,067       --.-K/s   in 0.02s   

2015-08-11 15:29:59 (48.7 KB/s) - &#8216;/dev/null&#8217; saved [1067]
```Or I can ssh to another Ubuntu box on my LAN even if it has a dynamic IP by ssh to its hostname.local.

---

