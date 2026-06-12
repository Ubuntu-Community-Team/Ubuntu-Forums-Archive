---
title: "Apache2 PAM authentication not working??"
date: 2006-10-12
forum: General Help
---

### Post by Skoude on 2006-10-12
Greetings!

I upgraded from breezy to dapper and now apache2 using pam authentication against kerberos is not working anymore.. So now  our salesoffices cannot connect to reports server using their own AD usernames and password.. Samba + krb is working, because I can login by using ssh with my AD username and password... 

Apache's error log only says: 
[Thu Oct 12 15:05:21 2006] [error] Re-negotiation handshake failed: Not accepted by client!?
[Thu Oct 12 15:05:22 2006] [error] [client 10.26.10.21] access to /cgi-bin/salesreport.pl failed, reason: user kosnet\\test.user not allowed access
[Thu Oct 12 15:05:30 2006] [error] [client 10.26.10.21] PAM: user 'test.user' - not authenticated: Authentication failure


The username is correct and password is correct, and it worked like hour ago before I upgraded it to  Dapper.. Anybody any idea?

---

### Post by Skoude on 2006-10-12
I almost solved the problem according to this post:
[http://lists.debian.org/debian-apache/2006/07/msg00059.html](http://lists.debian.org/debian-apache/2006/07/msg00059.html)
Package: Apache2-common
Version: 2.0.55-4


Description: In current version of Etch: the pam_auth module in
             Apache2 doesn't work unless


		1) www-data can read /etc/shadow (e.g. by
		   adding www-data to shadow group). Suggest
		   documenting?


		2) /etc/pam.d/apache2 exists but the Apache2 w/ pam_module
		   is looking for /etc/pam.d/httpd. A softlink solved
		   my problem but it took awhile to figure that one out.


now the authentication with PAM is working with local server username and password, but it won't work if I try to login using the Active directory accounts.. klist and kinit is working correctly... There has to be some sort of problem with the www-data user that it cannot access kerberos system... this is weird..

---

