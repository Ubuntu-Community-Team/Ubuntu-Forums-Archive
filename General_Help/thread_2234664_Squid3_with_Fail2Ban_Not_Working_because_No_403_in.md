---
title: "Squid3 with Fail2Ban Not Working because No 403 in Log File [Ubuntu 12.04 Server]"
date: 2014-07-16
forum: General Help
---

### Post by EcoCollectivist on 2014-07-16
I am having trouble getting Fail2Ban to work with Squid3. Fail2Ban works fine with SSH. 

I have added the squid.conf file to "/etc/fail2ban/filter.d". I got the squid.conf from: [https://github.com/fail2ban/fail2ban/blob/master/config/filter.d/squid.conf](https://github.com/fail2ban/fail2ban/blob/master/config/filter.d/squid.conf)

# Fail2Ban filter for Squid attempted proxy bypasses
#
#


[Definition]


failregex = ^\s+\d\s<HOST>\s+[A-Z_]+_DENIED/403 .*$
            ^\s+\d\s<HOST>\s+NONE/405 .*$






# Author: Daniel Black





The thing is that my log file never logs a 403 or 405. For example, here is about 14 bad logins through Firefox:

[I][SIZE=2]1405488858.944      0 192.168.1.71 TCP_DENIED/407 4027 POST [http://clients1.google.com/ocsp](http://clients1.google.com/ocsp) - NONE/- text/html
1405488859.175      0 192.168.1.71 TCP_DENIED/407 4027 POST [http://clients1.google.com/ocsp](http://clients1.google.com/ocsp) - NONE/- text/html
1405488859.899      0 192.168.1.71 TCP_DENIED/407 4027 POST [http://clients1.google.com/ocsp](http://clients1.google.com/ocsp) - NONE/- text/html
1405488861.069      0 192.168.1.71 TCP_DENIED/407 4959 GET [http://www.google.ca/url?](http://www.google.ca/url?) - NONE/- text/html
1405488865.259      8 192.168.1.71 TCP_DENIED/407 5518 GET [http://www.google.ca/url?](http://www.google.ca/url?) baljf NONE/- text/html
1405488865.701      0 192.168.1.71 TCP_DENIED/407 4027 POST [http://clients1.google.com/ocsp](http://clients1.google.com/ocsp) - NONE/- text/html
1405488867.791      0 192.168.1.71 TCP_DENIED/407 5519 GET [http://www.google.ca/url?](http://www.google.ca/url?) sdlkfj NONE/- text/html
1405488871.052      1 192.168.1.71 TCP_DENIED/407 5517 GET [http://www.google.ca/url?](http://www.google.ca/url?) **** NONE/- text/html
1405488874.846      0 192.168.1.71 TCP_DENIED/407 5520 GET [http://www.google.ca/url?](http://www.google.ca/url?) ****you NONE/- text/html
1405488881.327      1 192.168.1.71 TCP_DENIED/407 5529 GET [http://www.google.ca/url?](http://www.google.ca/url?) why%20the%20**** NONE/- text/html
1405488885.167      1 192.168.1.71 TCP_DENIED/407 5531 GET [http://www.google.ca/url?](http://www.google.ca/url?) stop%20this%20shit NONE/- text/html
1405488889.535      0 192.168.1.71 TCP_DENIED/407 5516 GET [http://www.google.ca/url?](http://www.google.ca/url?) sto NONE/- text/html
1405488919.274      0 192.168.1.71 TCP_DENIED/407 5521 GET [http://www.google.ca/url?](http://www.google.ca/url?) kjdflkjs NONE/- text/html
1405488921.934      0 192.168.1.71 TCP_DENIED/407 5522 GET [http://www.google.ca/url?](http://www.google.ca/url?) sldfj NONE/- text/html
1405488925.498      0 192.168.1.71 TCP_DENIED/407 5521 GET [http://www.google.ca/url?](http://www.google.ca/url?) flcudk NONE/- text/html
1405488939.719      0 192.168.1.71 TCP_DENIED/407 5525 GET [http://www.google.ca/url?](http://www.google.ca/url?) asdfasdf NONE/- text/html
1405488943.879      1 192.168.1.71 TCP_DENIED/407 5524 GET [http://www.google.ca/url?](http://www.google.ca/url?) ****you NONE/- text/html
1405488948.304      0 192.168.1.71 TCP_DENIED/407 5524 GET [http://www.google.ca/url?](http://www.google.ca/url?) ****acunt NONE/- text/html[/SIZE][/I]

How do I get Squid3 to log 403 and 405 which is represented in Fail2Ban's squid.conf file?

Here is the configuration of my squid3 proxy:

*auth_param digest program /usr/lib/squid3/digest_pw_auth -c /etc/squid3/passwords*
*auth_param digest realm proxy*
*acl authenticated proxy_auth REQUIRED*
*http_access allow authenticated*
*http_access deny all*
*http_port 0.0.0.0:41483*
*forwarded_for off*
*access_log /var/log/squid3/access.log squid*
*request_header_access Allow allow all*
*request_header_access Authorization allow all*
*request_header_access WWW-Authenticate allow all*
*request_header_access Proxy-Authorization allow all*
*request_header_access Proxy-Authenticate allow all*
*request_header_access Cache-Control allow all*
*request_header_access Content-Encoding allow all*
*request_header_access Content-Length allow all*
*request_header_access Content-Type allow all*
*request_header_access Date allow all*
*request_header_access Expires allow all*
*request_header_access Host allow all*
*request_header_access If-Modified-Since allow all*
*request_header_access Last-Modified allow all*
*request_header_access Location allow all*
*request_header_access Pragma allow all*
*request_header_access Accept allow all*
*request_header_access Accept-Charset allow all*
*request_header_access Accept-Encoding allow all*
*request_header_access Accept-Language allow all*
*request_header_access Content-Language allow all*
*request_header_access Mime-Version allow all*
*request_header_access Retry-After allow all*
*request_header_access Title allow all*
*request_header_access Connection allow all*
*request_header_access Proxy-Connection allow all*
*request_header_access User-Agent allow all*
*request_header_access Cookie allow all*
*request_header_access All deny all*

---

### Post by thehousecat2 on 2014-09-29
Hi. You'll only get 403 if the client does not try to authenticate - i.e. matching the 'http_access deny all' rule. If the the user is trying to authenticate then that alway matches the 'http_access allow authenticated' rule. If the authentication fails then you'll get 407. I don't think there is any retry limit for Squid *proxy_auth *so that it eventually will return 403. I've no idea how you would get 405.

---

