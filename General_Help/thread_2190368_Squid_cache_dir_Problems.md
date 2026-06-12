---
title: "Squid cache_dir Problems"
date: 2013-11-27
forum: General Help
---

### Post by secoonder on 2013-11-27
Hello.
I am using squid 3.1.14 on Ubuntu 12.04 LTS.
&#305; am using 75 MB size for cache_dir (cache_dir ufs /var/spool/squid3 75 16 256)
And &#305; am cache directory follows:
root@xxx:/var/spool/squid3# du -hs * 
62  MB 00           
1.1 MB 01
1.1 MB 02
1.1 MB 03
1.1 MB 04
1.1 MB 05
1.1 MB 06
1.1 MB 07
1.1 MB 08
1.1 MB 09
1.1 MB 0A
1.1 MB 0B
1.1 MB 0C
1.1 MB 0D
1.1 MB 0E
1.1 MB 0F
168k swap.state
--------------------------------------------------------------
My problem is that 00 directory size is 62 MB.But other directories are 1.1 MB.
Why not equal to the size of the cache folders.??
is this situation important ? is my configuration errors ?
King Regards

---

### Post by Lars Noodén on 2013-11-27
75MB is kind of small.  I'm more used to seeing configurations with 100's of MB or even GB.  You could easily fill a 75MB cache up with a noisy web page or two if they're cluttered with big graphics.  The configuration looks fine otherwise.  Have you looked inside 00 to see what's there taking up space?  If you have used squid already then it could be actual cache data.

---

### Post by secoonder on 2013-11-27
Thank a lot Lars Nooden.
 Cache_dir size is 75 mb for using a trial.Yes &#305; have looked inside 00. 62 Mb is used.But other directories is free :( :(

---

### Post by Lars Noodén on 2013-11-27
Right but there are sub-directories under 00 and they contain the cache objects.  It is very easy for them to contain 62MB worth of cache objects in those subdirectories.  How about checking the directories under 00?

---

### Post by secoonder on 2013-11-27
Lars Nooden thank you.
i saw directories under 00.it is 256 directories under 00...&#305; check one directory.&#305; saw the cache content.i cant problem this section.

---

### Post by Lars Noodén on 2013-11-27
Have you tried seeing what's in there and the subirectories?

```

ls -Rlh /var/spool/squid3/00/

```

They might add up to 62MB

---

### Post by secoonder on 2013-11-27
Yes i saw subdirectories.And &#305; calculate the size.total 62 Mb.

---

### Post by secoonder on 2013-11-27
But ,This situation is same.it is not equal to the size of the cache folders.??
root@xxx:/var/spool/squid3# du -hs * 
62  MB 00           
1.1 MB 01
1.1 MB 02
1.1 MB 03
1.1 MB 04
1.1 MB 05
1.1 MB 06
1.1 MB 07
1.1 MB 08
1.1 MB 09
1.1 MB 0A
1.1 MB 0B
1.1 MB 0C
1.1 MB 0D
1.1 MB 0E
1.1 MB 0F
168k swap.state

---

### Post by tad1073 on 2013-11-27
Below is my squid.conf, it works well.

```
# ACCESS CONTROLS OPTIONS
# ====================
#
acl QUERY urlpath_regex -i cgi-bin \? \.php$ \.asp$ \.shtml$ \.cfm$ \.cfml$ \.phtml$ \.php3$ localhost
acl all src
acl localnet src 192.168.1.0/27
acl thomthom src 127.0.1.1
acl safeports port 21 70 80 210 280 443 488 563 591 631 777 901 81 3128 1025-65535
acl sslports port 443 563 81 2087 10000
acl purge method PURGE
acl connect method CONNECT
acl ym dstdomain .messenger.yahoo.com .psq.yahoo.com
acl ym dstdomain .us.il.yimg.com .msg.yahoo.com .pager.yahoo.com
acl ym dstdomain .rareedge.com .ytunnelpro.com .chat.yahoo.com
acl ym dstdomain .voice.yahoo.com
acl ymregex url_regex yupdater.yim ymsgr myspaceim
#
http_access deny ym
http_access deny ymregex
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !safeports
http_access deny CONNECT !sslports
http_access allow localhost
http_access allow localnet
http_access allow thomthom
http_access deny all
#
# NETWORK OPTIONS
# &#8212;&#8212;&#8212;&#8212;&#8212;
#
http_port 3128
#
# OPTIONS WHICH AFFECT THE CACHE SIZE
# ==============================
#
cache_mem 1024 MB
maximum_object_size_in_memory 512 KB
cache_dir aufs /var/spool/squid3 40000 16 256 
memory_replacement_policy heap GDSF
cache_replacement_policy heap LFUDA
maximum_object_size 50 MB
cache_swap_low 90
cache_swap_high 95
#
# LOGFILE PATHNAMES AND CACHE DIRECTORIES
# ==================================
#
access_log /var/log/access.log
cache_log /var/log/cache.log
#cache_log /dev/null
cache_store_log none
logfile_rotate 10
log_icp_queries off
#
# OPTIONS FOR TUNING THE CACHE
# ========================
#
cache deny QUERY
refresh_pattern ^ftp: 1440 20% 10080 reload-into-ims
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern -i \.(gif|png|jp?g|ico|bmp|tiff?)$ 10080 95% 43200 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i \.(rpm|cab|deb|exe|msi|msu|zip|tar|xz|bz|bz2|lzma|gz|tgz|rar|bin|7z|doc?|xls?|ppt?|pdf|nth|psd|sis)$ 10080 90% 43200 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i \.(avi|iso|wav|mid|mp?|mpeg|mov|3gp|wm?|swf|flv|x-flv|axd)$ 43200 95% 432000 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i \.(html|htm|css|js)$ 1440 75% 40320
refresh_pattern -i \.index.(html|htm)$ 0 75% 10080
refresh_pattern -i (/cgi-bin/|\?) 0 0% 0
refresh_pattern . 1440 90% 10080
#
quick_abort_min 0 KB
quick_abort_max 0 KB
quick_abort_pct 100
store_avg_object_size 13 KB
#
# HTTP OPTIONS
# ===========
vary_ignore_expire on
#
# ANONIMITY OPTIONS
# ===============
#
request_header_access Allow allow all
request_header_access Authorization allow all
request_header_access WWW-Authenticate allow all
request_header_access Proxy-Authorization allow all
request_header_access Proxy-Authenticate allow all
request_header_access Cache-Control allow all
request_header_access Content-Encoding allow all
request_header_access Content-Length allow all
request_header_access Content-Type allow all
request_header_access Date allow all
request_header_access Expires allow all
request_header_access Host allow all
request_header_access If-Modified-Since allow all
request_header_access Last-Modified allow all
request_header_access Location allow all
request_header_access Pragma allow all
request_header_access Accept allow all
request_header_access Accept-Charset allow all
request_header_access Accept-Encoding allow all
request_header_access Accept-Language allow all
request_header_access Content-Language allow all
request_header_access Mime-Version allow all
request_header_access Retry-After allow all
request_header_access Title allow all
request_header_access Connection allow all
request_header_access Proxy-Connection allow all
request_header_access User-Agent allow all
request_header_access Cookie allow all
request_header_access All deny all
#
# TIMEOUTS
# =======
#
forward_timeout 240 second
connect_timeout 30 second
peer_connect_timeout 5 second
read_timeout 600 second
request_timeout 60 second
shutdown_lifetime 10 second
#
# ADMINISTRATIVE PARAMETERS
# =====================
#
cache_mgr thomas
cache_effective_user proxy
cache_effective_group proxy
httpd_suppress_version_string on
visible_hostname thomas
#
#ftp_list_width 32
#ftp_passive on
#ftp_sanitycheck on
#
# DNS OPTIONS
# ==========
#
dns_timeout 10 seconds
dns_nameservers 127.0.0.1
#
# MISCELLANEOUS
# ===========
#
memory_pools off
client_db off
reload_into_ims on
coredump_dir /cache
pipeline_prefetch on
offline_mode off
#
icp_port 0
ipcache_size 4096
```

---

### Post by secoonder on 2013-11-27
tad 1073 thank you.
can you compare my cache_dir with your cache_dir ?
are your cache_directories sizes distrubituon similar my cache_directories sizes distrubituon?? 

root@xxx:/var/spool/squid3# du -hs * 
62  MB 00           
1.1 MB 01
1.1 MB 02
1.1 MB 03
1.1 MB 04
1.1 MB 05
1.1 MB 06
1.1 MB 07
1.1 MB 08
1.1 MB 09
1.1 MB 0A
1.1 MB 0B
1.1 MB 0C
1.1 MB 0D
1.1 MB 0E
1.1 MB 0F
168k swap.state

my 00 directory is full ! ! !..But other directories size is more less.is there a mistake ??

Why do not share it with other folders ??
**for example:**
[B]6 MB 00           
6 MB 01
6 MB 03
6 MB 04
6 MB 05
6 MB 06
6 MB 07
6 MB 08
6 MB 09
6 MB 0A
6 MB 0B
6MB 0C
6 MB 0D
6 MB 0E
6MB 0F
168k swap.state)[/B] -->ALMOST TOTAL 75MB )))
Why do not share it with other folders. ?.

---

### Post by secoonder on 2013-12-16
The Problem is Solved ! 
After two week (Today) ,i looked cache_dir folders.first folder sizes is 900 MB.second directory size is 645 MB.

&#304; guess,when a folder almost size is 850-900 MB, squid pass second folder.
Thank you for your helps

---

