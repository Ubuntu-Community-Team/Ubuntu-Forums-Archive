---
title: "apt-get update gives &quot;E: Method gave invalid 103 Redirect message&quot;"
date: 2014-11-20
forum: General Help
---

### Post by victorhooi on 2014-11-20
I'm running Ubuntu 14.04 (x64) Server:
```

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.10
Release:        14.10
Codename:       utopic
uname -a
Linux ensign-primary 3.16.0-24-generic #32-Ubuntu SMP Tue Oct 28 13:07:32 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

When I try to run either apt-get update or aptitude update, I get an error message about "E: Method gave invalid 103 Redirect message". It seems to occur at different points each time:
```

sudo apt-get update
Ign http://www.ubnt.com trusty InRelease
Ign http://ppa.launchpad.net utopic InRelease
Ign http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic InRelease
Ign http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-updates InRelease
Ign http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-backports InRelease
Ign http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-security InRelease
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic Release.gpg
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-updates Release.gpg
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-backports Release.gpg
Hit http://www.ubnt.com trusty Release.gpg
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-security Release.gpg
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic Release
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-updates Release
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-backports Release
Ign http://ppa.launchpad.net trusty InRelease
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-security Release
E: Method gave invalid 103 Redirect message

```
```

sudo apt-get update
Ign http://ppa.launchpad.net utopic InRelease
Ign http://ppa.launchpad.net trusty InRelease
Ign http://ppa.launchpad.net utopic InRelease
Ign http://ppa.launchpad.net trusty InRelease
Ign http://ppa.launchpad.net saucy InRelease
Get:1 http://ppa.launchpad.net utopic Release.gpg [316 B]
Get:2 http://ppa.launchpad.net trusty Release.gpg [316 B]
Get:3 http://ppa.launchpad.net utopic Release.gpg [316 B]
Get:4 http://ppa.launchpad.net trusty Release.gpg [316 B]
Get:5 http://ppa.launchpad.net saucy Release.gpg [316 B]
Hit http://ppa.launchpad.net utopic Release
Hit http://ppa.launchpad.net trusty Release
Get:6 http://ppa.launchpad.net utopic Release [15.1 kB]
Hit http://ppa.launchpad.net trusty Release
Hit http://ppa.launchpad.net saucy Release
Ign http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic InRelease
Ign http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-updates InRelease
Ign http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-backports InRelease
Ign http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-security InRelease
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic Release.gpg
Ign http://www.ubnt.com trusty InRelease
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-updates Release.gpg
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-backports Release.gpg
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-security Release.gpg
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic Release
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-updates Release
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-backports Release
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic-security Release
Get:7 http://www.ubnt.com trusty Release.gpg [490 B]
Get:8 http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic/main amd64 Packages [1,330 kB]
Hit http://www.ubnt.com trusty Release
Get:9 http://www.ubnt.com trusty/ubiquiti amd64 Packages [570 B]
Get:10 http://ppa.launchpad.net utopic/main Sources [687 B]
Hit http://ubuntu.mirror.serversaustralia.com.au/ubuntu/ utopic/restricted amd64 Packages
E: Method gave invalid 103 Redirect message

```
This is the output of "wget -d [http://ppa.launchpad.net/](http://ppa.launchpad.net/) -o /tmp/outputfile.log" (suggestion from [http://askubuntu.com/questions/493180/method-gave-invalid-400-uri-failure-message-when-running-apt-get-update):](http://askubuntu.com/questions/493180/method-gave-invalid-400-uri-failure-message-when-running-apt-get-update):)
```

DEBUG output created by Wget 1.15 on linux-gnu.

URI encoding = 'UTF-8&#8217;
--2014-11-21 09:53:41--  http://ppa.launchpad.net/
Resolving ppa.launchpad.net (ppa.launchpad.net)... 91.189.95.83
Caching ppa.launchpad.net => 91.189.95.83
Connecting to ppa.launchpad.net (ppa.launchpad.net)|91.189.95.83|:80... connected.
Created socket 4.
Releasing 0x000000000176d9d0 (new refcount 1).

---request begin---
GET / HTTP/1.1
User-Agent: Wget/1.15 (linux-gnu)
Accept: */*
Host: ppa.launchpad.net
Connection: Keep-Alive

---request end---
HTTP request sent, awaiting response...
---response begin---
HTTP/1.1 302 Found
Date: Thu, 20 Nov 2014 22:53:42 GMT
Server: Apache/2.2.22 (Ubuntu)
Location: https://launchpad.net
Vary: Accept-Encoding
Content-Length: 288
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=iso-8859-1

---response end---
302 Found
Registered socket 4 for persistent reuse.
URI content encoding = 'iso-8859-1&#8217;
Location: https://launchpad.net [following]
Skipping 288 bytes of body: [<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>302 Found</title>
</head><body>
<h1>Found</h1>
<p>The document has moved <a href="https://launchpad.net">here</a>.</p>
<hr>
<address>Apache/2.2.22 (Ubuntu) Server at ppa.launchpad.net Port 80</address>
</body></html>
] done.
URI content encoding = None
--2014-11-21 09:53:41--  https://launchpad.net/
Resolving launchpad.net (launchpad.net)... 91.189.89.223, 91.189.89.222
Caching launchpad.net => 91.189.89.223 91.189.89.222
Connecting to launchpad.net (launchpad.net)|91.189.89.223|:443... connected.
Created socket 5.
Releasing 0x000000000178bea0 (new refcount 1).
Initiating SSL handshake.
Handshake successful; connected socket 5 to SSL handle 0x000000000178c730
certificate:
  subject: /OU=Domain Control Validated/CN=launchpad.net
  issuer:  /C=US/ST=Arizona/L=Scottsdale/O=GoDaddy.com, Inc./OU=http://certs.godaddy.com/repository//CN=Go Daddy Secure Certificate Authority - G2
X509 certificate successfully verified and matches host launchpad.net

---request begin---
GET / HTTP/1.1
User-Agent: Wget/1.15 (linux-gnu)
Accept: */*
Host: launchpad.net
Connection: Keep-Alive

---request end---
HTTP request sent, awaiting response...
---response begin---
HTTP/1.1 200 OK
Date: Thu, 20 Nov 2014 22:34:47 GMT
Server: zope.server.http (HTTP)
X-Powered-By: Zope (www.zope.org), Python (www.python.org)
Content-Length: 23630
X-Xss-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Strict-Transport-Security: max-age=15552000
Vary: Cookie,Authorization,Accept-Encoding
X-Frame-Options: SAMEORIGIN
Content-Type: text/html;charset=utf-8
Age: 1136
X-Cache: HIT from banana.canonical.com
X-Cache-Lookup: HIT from banana.canonical.com:3128
Via: 1.0 banana.canonical.com:3128 (squid/2.7.STABLE7)
Keep-Alive: timeout=60, max=100
Connection: Keep-Alive

---response end---
200 OK
Disabling further reuse of socket 4.
Closed fd 4
Registered socket 5 for persistent reuse.
URI content encoding = 'utf-8&#8217;
Length: 23630 (23K) [text/html]
index.html: Permission denied
Disabling further reuse of socket 5.
Closed 5/SSL 0x000000000178c730

Cannot write to 'index.html&#8217; (Success).
(END)

```

Any thoughts on what's going on?

Cheers,
Victor

---

### Post by budde377 on 2014-11-24
I had the same problem. 
Since I am currently traveling I added the following in my `/etc/apt/sources.list` file: 

deb mirror://mirrors.ubuntu.com/mirrors.txt utopic main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt utopic-updates main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt utopic-backports main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt utopic-security main restricted universe multiverse

Out commenting these solved the problem.

---

### Post by William_Miller on 2015-07-20
I am having a similar issue. So budde377 are you saying that those mirrors were used, then you commented them out with ##, and that fixed the issue?

---

### Post by mancini2 on 2016-03-30
Try deleting the fetched header files```
sudo rm -rf /var/lib/apt/lists/*
```then launch another update```
sudo apt-get update
```

---

### Post by Bashing-om on 2016-03-30
victorhooi; Hello;

You are beating a dead horse !
 Ubuntu 14.10 (Utopic Unicorn) was the 21st release of Ubuntu.  Support ended on July 23rd, 2015. See !eol, !upgrade and [http://ubottu.com/y/utopic](http://ubottu.com/y/utopic)

Upgrade or clean fresh install a current release.

[INDENT][INDENT]when it ain't, it ain't
[/INDENT][/INDENT]

---

### Post by howefield on 2016-03-31
> **Bashing-om said:**
> victorhooi; Hello;

You are beating a dead horse !
 Ubuntu 14.10 (Utopic Unicorn) was the 21st release of Ubuntu.  Support ended on July 23rd, 2015. See !eol, !upgrade and [http://ubottu.com/y/utopic](http://ubottu.com/y/utopic)

It was fine when he posted... ;)

---

### Post by Bashing-om on 2016-03-31
> **howefield said:**
> It was fine when he posted... ;)

As I chuckle -- teach me to read and look !
I do apologize for my failure.

[INDENT][INDENT]moving faster than the speed of thought
[/INDENT][/INDENT]

---

### Post by slickymaster on 2016-03-31
> **howefield said:**
> It was fine when he posted... ;)

Exactly. :P

With this let's put this one to sleep.

---

