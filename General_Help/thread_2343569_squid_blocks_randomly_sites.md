---
title: "squid blocks randomly sites"
date: 2016-11-17
forum: General Help
---

### Post by seriousdark on 2016-11-17
squid blocks randomly sites blacklist for example, wrote &#1072; vk.com ex.ua and blocks Yandex, mail.ru ...[COLOR=#000000][FONT=&quot]


acl localnet src 192.168.0.0/16[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]#acl url_filtred src 192.168.0.0/16[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]#acl localnet src 10.0.0.0/8    # RFC1918 possible internal network[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]#acl localnet src 172.16.0.0/12 # RFC1918 possible internal network[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]#acl localnet src 192.168.0.0/16        # RFC1918 possible internal network[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]#acl localnet src fc00::/7    # RFC 4193 local private network range[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]#acl localnet src fe80::/10    # RFC 4291 link-local (directly plugged) machines[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]acl blacklist url_regex -i "/etc/squid/blacklist"[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]acl SSL_ports port 443[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]acl Safe_ports port 80          # http[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]acl Safe_ports port 21          # ftp[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]acl Safe_ports port 443         # https[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]acl Safe_ports port 70          # gopher[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]acl Safe_ports port 210         # wais[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]acl Safe_ports port 1025-65535  # unregistered ports[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]acl Safe_ports port 280         # http-mgmt[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]acl Safe_ports port 488         # gss-http[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]acl Safe_ports port 591         # filemaker[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]acl Safe_ports port 777         # multiling http[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]acl CONNECT method CONNECT[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]#[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]# Recommended minimum Access Permission configuration:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]#[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]# Deny requests to certain unsafe ports[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]http_access deny !Safe_ports[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]# Deny CONNECT to other than secure SSL ports[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]http_access deny CONNECT !SSL_ports[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]# Only allow cachemgr access from localhost[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]http_access allow localhost manager[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]http_access deny manager[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]# We strongly recommend the following be uncommented to protect innocent[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]# web applications running on the proxy server who think the only[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]# one who can access services on "localhost" is a local user[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]#http_access deny to_localhost[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]#[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]#[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]# from where browsing should be allowed[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]http_access deny blacklist localnet[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]http_access allow localnet[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]http_access allow localhost[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]# And finally deny all other access to this proxy[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]http_access deny all[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]# Squid normally listens to port 3128[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]http_port 3128[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]# Uncomment and adjust the following to add a disk cache directory.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]cache_dir ufs /var/spool/squid 3000 16 256[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]# Leave coredumps in the first cache dir[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]coredump_dir /var/spool/squid[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]#[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]# Add any of your own refresh_pattern entries above these.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]#[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]refresh_pattern ^ftp:           1440    20%     10080[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]refresh_pattern ^gopher:        1440    0%   1440[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]refresh_pattern -i (/cgi-bin/|\?) 0     0%   0[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]refresh_pattern .               0   20%     4320[/FONT][/COLOR]

---

### Post by kingneutron on 2016-12-01
--Please attach file [COLOR=#000000][FONT=&amp]/etc/squid/blacklist so it can be diagnosed further; I use squid and you need to be careful with regexps (regular expressions) in your ACLs.  Squid will block based on the URL if it finds anything that is in that blacklist file[/FONT][/COLOR], so if it's too general it will need to be tweaked.

---

