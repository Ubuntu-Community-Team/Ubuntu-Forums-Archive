---
title: "Perl mysql.pm not found error"
date: 2012-11-09
forum: General Help
---

### Post by bigmatlem on 2012-11-09
Here is my problem.  A client has given me this grief I mean system to move from a 90's FREEBSD server to a new Ubuntu 12.04 amd64 server.  All is well with the server except for...

Can't locate Mysql.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at collect.cgi line 14.
BEGIN failed--compilation aborted at collect.cgi line 14.

Now mysql.pm is installed.  

/usr/lib/perl5/DBD/mysql.pm
/usr/share/perl5/Class/DBI/mysql.pm

I've changed the code to lowercase and still it crashes.  It worked allegedly on the old server.  Don't know for sure.  

Here is a snipit of the code:

#!/usr/bin/perl5
# -----------------------------------------------------------

  $verbose               = '1';
  $html_mode             = '0';

  require 'timelocal.pl';
  use Mysql;
  $HOST                  = "localhost";
  $DATABASE              = "blahblah";
  $BILLING_TABLE         = "billing";
  $MEMBER_TABLE          = "members";
  $SALES_TABLE           = "sales";
  $USER_MAIL_TABLE       = "jobs_mail_list";
  $COLLECT_TABLE         = "collections";
  $ACCESS_NAME           = "blah";
  $ACCESS_PASS           = "xxxxxxx";

yet I run a test script and it works.  I'm completely stumped and am willing to pay to get this fixed.   GRRR!

---

### Post by drmrgd on 2012-11-09
I think the issue is that you're calling for 'Mysql.pm' instead of 'mysql.pm'.  On Ubuntu systems, filenames are case sensitive.  Try that, and if it doesn't work, you may also have to make the call a little differently:

```
use DBD::mysql;
```

---

### Post by Habitual on 2012-11-09
[http://cpansearch.perl.org/src/RUDY/DBD-mysql-2.9008/INSTALL.html#cpan_installation](http://cpansearch.perl.org/src/RUDY/DBD-mysql-2.9008/INSTALL.html#cpan_installation)

---

### Post by Lars Noodén on 2012-11-09
> **Habitual said:**
> [http://cpansearch.perl.org/src/RUDY/DBD-mysql-2.9008/INSTALL.html#cpan_installation](http://cpansearch.perl.org/src/RUDY/DBD-mysql-2.9008/INSTALL.html#cpan_installation)

Those instructions are missing the easiest way.  The easy way to install the modules in Ubuntu is to use the repositories.  [DBD::mysql](http://search.cpan.org/~capttofu/DBD-mysql-4.022/lib/DBD/mysql.pm) is available as [libdbd-mysql-perl](apt:libdbd-mysql-perl) and [DBI](http://search.cpan.org/dist/DBI/DBI.pm) is available as [libclass-dbi-perl](apt:libclass-dbi-perl).  The modules are quite mature and unlikely to be updated but the package manager will help with dependencies.

---

