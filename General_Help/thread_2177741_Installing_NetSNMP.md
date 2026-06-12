---
title: "Installing Net::SNMP"
date: 2013-09-30
forum: General Help
---

### Post by ivan17 on 2013-09-30
I was trying to use the check_ifoperstatus, but have the folowing error 


> root@mpnagios:/usr/local/nagios/libexec# ./check_ifoperstatus -h
Can't locate Net/SNMP.pm in @INC (@INC contains: /usr/local/nagios/libexec /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at ./check_ifoperstatus line 40.
BEGIN failed--compilation aborted at ./check_ifoperstatus line 40.
root@mpnagios:/usr/local/nagios/libexec#


And that line is use Net::SNMP;


Im trying to install Net::SNMP on Ubuntu Server 12.04 with the following command: 
```
perl -MCPAN -e 'install Net::SNMP'
```


Also i was trying this 


"cpan> install Net::SNMP" and "install Bundle::CPAN"
And have the following errors:


> Going to read '/root/.cpan/sources/authors/01mailrc.txt.gz'
DONE
Fetching with HTTP::Tiny:
[http://artfiles.org/cpan.org/modules/02packages.details.txt.gz](http://artfiles.org/cpan.org/modules/02packages.details.txt.gz)
Going to read '/root/.cpan/sources/modules/02packages.details.txt.gz'
Warning: Your /root/.cpan/sources/modules/02packages.details.txt.gz does not contain a Line-Count header.
Please check the validity of the index file by comparing it to more
than one CPAN mirror. I'll continue but problems seem likely to
happen.
Warning: Your /root/.cpan/sources/modules/02packages.details.txt.gz does not contain a Last-Updated header.
Please check the validity of the index file by comparing it to more
than one CPAN mirror. I'll continue but problems seem likely to
happen.
Could not split line["<html>"]
Could not split line["\cI<head>"]
.Could not split line["\cI\cI"]
Could not split line[""]
Giving up parsing your /root/.cpan/sources/modules/02packages.details.txt.gz, too many errors
root@start:/usr/local/nagios/libexec# aptitude -y install snmp
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.


---

### Post by Lars Noodén on 2013-09-30
It would be preferable to install from Ubuntu's package repository, if the package is at all available there in the right version.  Mixing repository and non-repository packages tends not to end very well.

The package I think you are looking for is [libnet-snmp-perl](apt://libnet-snmp-perl)

Is that the right version for you?  You should be able to get it with apt-get or Synaptic or the Software Center.

---

### Post by ivan17 on 2013-10-01
Nop that not helping too. But after searching through the net i found the solution that works for me, i suppose that this problem is on the New Ubuntu Server 12.04.3 version LTS with the perl default installation. Im not sure about that but thats how i think it is. And here it is the solution ...

1.) mv /root/.cpan /root/.cpanbackup
2.) perl -MCPAN -e shell
3.) cpan > install Bundle::CPAN

and that it is all i hope we can close and sorry that i open this error post but i really need fast help

---

### Post by Lars Noodén on 2013-10-01
What error message did you get when you tried to install libnet-snmp-perl?  It should give you Net::SNMP

```

$ **perl  -e 'use Net::SNMP;'**
Can't locate Net/SNMP.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at -e line 1.
BEGIN failed--compilation aborted at -e line 1.
$ **sudo apt-get install libnet-snmp-perl**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libcrypt-des-perl libdigest-hmac-perl libio-socket-inet6-perl
The following NEW packages will be installed:
  libnet-snmp-perl
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 107 kB of archives.
After this operation, 464 kB of additional disk space will be used.
Get:1 http://fi.archive.ubuntu.com/ubuntu/ saucy/main libnet-snmp-perl all 6.0.1-2 [107 kB]
Fetched 107 kB in 0s (127 kB/s)            
Selecting previously unselected package libnet-snmp-perl.
(Reading database ... 112518 files and directories currently installed.)
Unpacking libnet-snmp-perl (from .../libnet-snmp-perl_6.0.1-2_all.deb) ...
Processing triggers for man-db ...
Setting up libnet-snmp-perl (6.0.1-2) ...
$ **perl  -e 'use Net::SNMP;'**
$ 

```

I get that both on 13.10-beta and 12.04.3 Server.  Even the manual page gets installed.

---

