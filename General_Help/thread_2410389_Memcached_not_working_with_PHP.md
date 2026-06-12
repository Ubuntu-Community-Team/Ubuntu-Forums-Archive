---
title: "Memcached not working with PHP"
date: 2019-01-14
forum: General Help
---

### Post by alexf40 on 2019-01-14
Hi,

Finally moved to Ubuntu and am setting up my server, still trying to get to grips vs Centos.

Looking forward to meeting the new community and would really appreciate some help.

All appears to be going well so far, but I got stuck wtih trying to get memcached to work.

When I check my php.ini file it doesn't show memcached at all, but when I check the server it says it's running and all seems ok to me.

Thanks for your help in advance.

Cheers
Alex

PHP Version 7.2.14

```
root@localhost:~# lsb_release -aNo LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:        16.04
Codename:       xenial




memcached is already the newest version (1.4.25-2ubuntu1.4).




root@localhost:~# sudo netstat -nap | grep memcached
tcp        0      0 127.0.0.1:11211         0.0.0.0:*               LISTEN      1200/memcached
unix  3      [ ]         STREAM     CONNECTED     16692    1200/memcached
unix  3      [ ]         STREAM     CONNECTED     16693    1200/memcached
unix  3      [ ]         STREAM     CONNECTED     16686    1200/memcached
unix  3      [ ]         STREAM     CONNECTED     16690    1200/memcached
unix  3      [ ]         STREAM     CONNECTED     16684    1200/memcached
unix  3      [ ]         STREAM     CONNECTED     16687    1200/memcached
unix  3      [ ]         STREAM     CONNECTED     16683    1200/memcached
unix  3      [ ]         STREAM     CONNECTED     16689    1200/memcached
unix  3      [ ]         STREAM     CONNECTED     14333    1200/memcached
unix  3      [ ]         STREAM     CONNECTED     16680    1200/memcached
unix  3      [ ]         STREAM     CONNECTED     16681    1200/memcached
root@localhost:~#








root@localhost:~# vim /etc/memcached.conf
# memcached default config file
# 2003 - Jay Bonci <jaybonci@debian.org>
# This configuration file is read by the start-memcached script provided as
# part of the Debian GNU/Linux distribution.


# Run memcached as a daemon. This command is implied, and is not needed for the
# daemon to run. See the README.Debian that comes with this package for more
# information.
-d


# Log memcached's output to /var/log/memcached
logfile /var/log/memcached.log


# Be verbose
# -v


# Be even more verbose (print client commands as well)
# -vv


# Start with a cap of 64 megs of memory. It's reasonable, and the daemon default
# Note that the daemon will grow to this size, but does not start out holding this much
# memory
-m 64


# Default connection port is 11211
-p 11211


# Run the daemon as root. The start-memcached will default to running as root if no
# -u command is present in this config file
-u memcache




# Specify which IP address to listen on. The default is to listen on all IP addresses
# This parameter is one of the only security measures that memcached has, so make sure
# it's listening on a firewalled interface.
-l 127.0.0.1


# Limit the number of simultaneous incoming connections. The daemon default is 1024
# -c 1024


# Lock down all paged memory. Consult with the README and homepage before you do this
# -k


# Return error when memory is exhausted (rather than removing items)
# -M


# Maximize core file limit
# -r

```

---

### Post by alexf40 on 2019-01-15
[COLOR=#2B2E2F][FONT=&quot]memcached cannot be installed because popen() had been disabled for security reasons.[/FONT][/COLOR]
[COLOR=#2B2E2F][FONT=&quot]So, I edited /opt/plesk/php/7.2/etc/php.ini and excluded "popen" from disable_functions list. [/FONT][/COLOR]
[COLOR=#2B2E2F][FONT=&quot]Original file /opt/plesk/php/7.2/etc/php.ini I saved as "/opt/plesk/php/7.2/etc/php.ini_back"[/FONT][/COLOR]
[COLOR=#2B2E2F][FONT=&quot]After that, I was able to install memcached using [/FONT][/COLOR]# /opt/plesk/php/7.2/bin/pecl install memcached [COLOR=#2B2E2F][FONT=&quot]&#8203; with no issues. [/FONT][/COLOR]

---

