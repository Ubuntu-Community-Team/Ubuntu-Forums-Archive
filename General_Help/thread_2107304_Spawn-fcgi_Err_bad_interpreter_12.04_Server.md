---
title: "Spawn-fcgi Err: bad interpreter 12.04 Server"
date: 2013-01-21
forum: General Help
---

### Post by UclaGeek on 2013-01-21
Hi, 

I'm having an issue with launching spawn-fcgi. When I run:
```

service fcgiwrap start
 * Starting FastCGI wrapper fcgiwrap                           
    /etc/init.d/fcgiwrap: 1: eval: /usr/bin/spawn-fcgi: not found

```

I know it's installed so I ran:
```

locate spawn-fcgi

```

and as you can see it's there:

```

/etc/alternatives/spawn-fcgi
/etc/alternatives/spawn-fcgi.1.gz
/etc/init.d/spawn-fcgi
/etc/rc0.d/K20spawn-fcgi
/etc/rc1.d/K20spawn-fcgi
/etc/rc2.d/S20spawn-fcgi
/etc/rc3.d/S20spawn-fcgi
/etc/rc4.d/S20spawn-fcgi
/etc/rc5.d/S20spawn-fcgi
/etc/rc6.d/K20spawn-fcgi
/usr/bin/spawn-fcgi
/usr/bin/spawn-fcgi.standalone
/usr/share/doc/spawn-fcgi
/usr/share/doc/spawn-fcgi/NEWS.gz
/usr/share/doc/spawn-fcgi/README.Debian
/usr/share/doc/spawn-fcgi/changelog.Debian.gz
/usr/share/doc/spawn-fcgi/copyright
/usr/share/doc/spawn-fcgi/run-generic
/usr/share/doc/spawn-fcgi/run-php
/usr/share/doc/spawn-fcgi/run-rails
/usr/share/man/man1/spawn-fcgi.1.gz
/usr/share/man/man1/spawn-fcgi.standalone.1.gz
/var/lib/dpkg/alternatives/spawn-fcgi
/var/lib/dpkg/info/spawn-fcgi.list
/var/lib/dpkg/info/spawn-fcgi.md5sums
/var/lib/dpkg/info/spawn-fcgi.postinst
/var/lib/dpkg/info/spawn-fcgi.prerm
/var/lib/update-rc.d/spawn-fcgi

```

So then I try to start it up manually:

```

/usr/bin/spawn-fcgi -a 127.0.0.1 -p 9000 -u www-data -g www-data -f /usr/bin/php5-cgi -P /var/run/fastcgi-php.pid
use: bad interpreter: No such file or directory

```

The bad interpreter is confusing spawn-fcgi is perl 
```

#!/usr/bin/perl

use strict;
use warnings FATAL => qw( all );

use IO::Socket::UNIX;

my $bin_path = '/usr/bin/fcgiwrap';
my $socket_path = $ARGV[0] || '/tmp/cgi.sock';
my $num_children = $ARGV[1] || 1;


```

I have perl install. 

```

perl -v

This is perl 5, version 14, subversion 2 (v5.14.2) built for x86_64-linux-gnu-thread-multi
(with 55 registered patches, see perl -V for more detail)

```

I'm just really confused. Any help you can provide is very much appreciated.

---

