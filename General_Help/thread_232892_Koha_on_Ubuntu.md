---
title: "Koha on Ubuntu"
date: 2006-08-09
forum: General Help
---

### Post by ramuja on 2006-08-09
[B]Hi everybody,
Is there any one who uses Koha software which is a library software on Ubuntu 6.06 LTS? please help me i tried to install it but i can't do it because I have the following problem.[/B]

__
checking perl modules ...
The Net::Z3950 module is missing. This module is necessary if you want to
use Koha's Z39.50 client to download bibliographic records from other
libraries.

To install this module, you will need the yaz client installed from
[http://www.indexdata.dk/yaz/](http://www.indexdata.dk/yaz/) and then you can install the perl module with
the command:

perl -MCPAN -e 'install Net::Z3950'

...or by installing packages for your distribution, if available.

IMPORTANT NOTE : If you use Perl 5.8.0, you might need to edit NET::Z3950's
Makefile.PL and yazwrap/Makefile.PL to include:

'DEFINE' => '-D_GNU_SOURCE',

Also note that some installations of Perl on Red Hat will generate a lot of
"'my_perl' undeclared" errors when running make in Net-Z3950. This is fixed
by inserting in yazwrap/ywpriv.h a line saying #include "XSUB.h"

Press the <ENTER> key to continue:




 MISSING PERL MODULES

You are missing some Perl modules required by Koha. Please run this again
after installing them. They may be installed by finding packages from your
operating system supplier, or running (as root) the following commands:

export LC_ALL=C

perl -MCPAN -e 'install "Date::Manip"'

perl -MCPAN -e 'install "HTML::Template"'

perl -MCPAN -e 'install "MARC::Record"'

perl -MCPAN -e 'install "Mail::Sendmail"'

perl -MCPAN -e 'install "You will need PDF::API2 for barcode generator"'

perl -MCPAN -e 'install "Net::LDAP"'

perl -MCPAN -e 'install "Event"'

perl -MCPAN -e 'install "Net::Z3950"'
                                                                                                               
___[U][U][U][U][U][U][U]_[/U][/U][/U][/U][/U][/U][/U]__

**when i trying to install each perl module i have got the following problem**
                                                                                                                  
_[U][U][U][U][U][U][U]_[/U][/U][/U][/U][/U][/U][/U]_[U]_[/U]

CPAN: Storable loaded ok
Going to read /home/user/.cpan/Metadata
  Database was generated on Tue, 08 Aug 2006 22:29:55 GMT
Running install for module MARC::Record
Running make for P/PE/PETDANCE/MARC-Record-1.38.tar.gz
CPAN: Digest::MD5 loaded ok
Checksum for /home/user/.cpan/sources/authors/id/P/PE/PETDANCE/MARC-Record-1.38. tar.gz ok
Scanning cache /home/user/.cpan/build for sizes
MARC-Record-1.38/
MARC-Record-1.38/.releaserc
MARC-Record-1.38/bin/
MARC-Record-1.38/bin/marcdump
MARC-Record-1.38/bin/marclint
MARC-Record-1.38/Changes
MARC-Record-1.38/etc/
MARC-Record-1.38/etc/ecbdlist.html
MARC-Record-1.38/etc/specs
MARC-Record-1.38/lib/
MARC-Record-1.38/lib/MARC/
MARC-Record-1.38/lib/MARC/Batch.pm
MARC-Record-1.38/lib/MARC/Doc/
MARC-Record-1.38/lib/MARC/Doc/Tutorial.pod
MARC-Record-1.38/lib/MARC/Field.pm
MARC-Record-1.38/lib/MARC/File/
MARC-Record-1.38/lib/MARC/File/MicroLIF.pm
MARC-Record-1.38/lib/MARC/File/USMARC.pm
MARC-Record-1.38/lib/MARC/File.pm
MARC-Record-1.38/lib/MARC/Lint.pm
MARC-Record-1.38/lib/MARC/Record.pm
MARC-Record-1.38/Makefile.PL
MARC-Record-1.38/MANIFEST
MARC-Record-1.38/META.yml
MARC-Record-1.38/README
MARC-Record-1.38/t/
MARC-Record-1.38/t/00.load.t
MARC-Record-1.38/t/01.version.t
MARC-Record-1.38/t/10.camel.t
MARC-Record-1.38/t/11.astring.t
MARC-Record-1.38/t/12.ldr.t
MARC-Record-1.38/t/20.clone.t
MARC-Record-1.38/t/50.batch.t
MARC-Record-1.38/t/60.insert.t
MARC-Record-1.38/t/60.update.t
MARC-Record-1.38/t/61.append.t
MARC-Record-1.38/t/61.replace.t
MARC-Record-1.38/t/62.before.t
MARC-Record-1.38/t/63.after.t
MARC-Record-1.38/t/64.create.t
MARC-Record-1.38/t/66.grouped.t
MARC-Record-1.38/t/66.ordered.t
MARC-Record-1.38/t/70.croak.t
MARC-Record-1.38/t/75.warnings.t
MARC-Record-1.38/t/80.alphatag.t
MARC-Record-1.38/t/81.decode.t
MARC-Record-1.38/t/82.baddir.t
MARC-Record-1.38/t/83.indicators.t
MARC-Record-1.38/t/85.fh.t
MARC-Record-1.38/t/alphatag.lif
MARC-Record-1.38/t/baddir.usmarc
MARC-Record-1.38/t/badind.usmarc
MARC-Record-1.38/t/badldr.usmarc
MARC-Record-1.38/t/batch-filter.t
MARC-Record-1.38/t/camel.usmarc
MARC-Record-1.38/t/convenience.t
MARC-Record-1.38/t/decode-filter.t
MARC-Record-1.38/t/file-filter.t
MARC-Record-1.38/t/file-header.t
MARC-Record-1.38/t/lineendings-0a.lif
MARC-Record-1.38/t/lineendings-0d.lif
MARC-Record-1.38/t/lineendings-0d0a.lif
MARC-Record-1.38/t/lineendings.t
MARC-Record-1.38/t/lint.t
MARC-Record-1.38/t/pod-coverage.t
MARC-Record-1.38/t/pod.t
MARC-Record-1.38/t/sample1.lif
MARC-Record-1.38/t/sample1.usmarc
MARC-Record-1.38/t/sample100.lif
MARC-Record-1.38/t/sample20.lif
MARC-Record-1.38/t/title_proper.t
MARC-Record-1.38/t/title_proper.usmarc
MARC-Record-1.38/t/utf8.t
Removing previously used /home/user/.cpan/build/MARC-Record-1.38

  CPAN.pm: Going to build P/PE/PETDANCE/MARC-Record-1.38.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for MARC::Record
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
                                                                                                                     

**please if there is anyone who knows about this thing help  me.**

---

### Post by beefsprocket on 2006-08-28
I had problems with Koha install too. I found that installing only the required modules alog with libyaz-devel or whatever it was helped. I got as far as a working catalogue page, but I can't figure out how to access the administrative area.

---

### Post by sk72 on 2008-03-06
Hi..I am also trying to install koha on Ubuntu Server 7.10..how do you install MARC:Record module?

what does cvs mean?

Thanks.

Sk

---

### Post by sk72 on 2008-03-07
oops...forgot to install cvs.....

---

### Post by laonux on 2008-04-22
> **sk72 said:**
> oops...forgot to install cvs.....

Hi sk72 and all,


I am, too, preparing to install Koha on Ubuntu server 7.10. Please help me out as what I would really to get started. There are not too many help there..

Thanks in advance.
Anousak

---

### Post by namdung on 2008-05-05
Need help to install KOHA 3 in Ubuntu 8.04 using XAMPP or otherwise. Been trying for sometime but have failed miserably. I'm a newbee and any help will be greatly appreciated. Thanks.

---

### Post by N00B-Tube on 2008-07-24
Kia ora from NZ,

I second namdung's request!!

---

