---
title: "Squid in win2000 AD"
date: 2006-07-06
forum: General Help
---

### Post by mc100 on 2006-07-06
Hi,
I have a little windows2000 domain.
I'm trying to configure squid to use active directory for autenticate my users.
I followed different howto's but something is wrong.

What I did:
- I configured Kerberos following this great tutorial: [http://www.ubuntuforums.org/showthread.php?t=91510&highlight=samba+active](http://www.ubuntuforums.org/showthread.php?t=91510&highlight=samba+active)
This part is working

- I created my squid.conf fille. Here it is:

> hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY
hosts_file /etc/hosts
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320
http_port 8080


         auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp
	auth_param ntlm children 5
	auth_param ntlm max_challenge_reuses 0
	auth_param ntlm max_challenge_lifetime 2 minutes
	auth_param basic program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-basic
	auth_param basic children 5
	auth_param basic realm Squid proxy-caching web server
	auth_param basic credentialsttl 2 hours

acl our_networks src 192.168.111.0/255.255.255.0
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563      # https, snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl purge method PURGE
acl CONNECT method CONNECT
acl AuthorizedUsers proxy_auth REQUIRED

http_access allow all AuthorizedUsers
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access allow our_networks
http_access deny all
http_reply_access allow all
icp_access allow all
coredump_dir /var/spool/squid



Now when I try to surf the web using the proxy, I get a login window even if I am a domain authenticated user. If I try to login using my credentials, the login fails.
The squid access.log reports this error:
1152197352.937      7 192.168.111.119 TCP_DENIED/407 1849 GET [http://toolbarqueries.google.com/search?](http://toolbarqueries.google.com/search?) - NONE/- text/html


Any ideas?
Thanks

---

