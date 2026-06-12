---
title: "can not use apt-get or cpan... proxy making trouble"
date: 2012-12-17
forum: General Help
---

### Post by Debasish Mukherjee on 2012-12-17
HI,
I am using UBUNTU 12.10
few days back I needed to change my proxy for connecting nternet at my institute. After that I cant access internet through terminal.... like can't install CPAN lib for perl or install using apt-get. 
I changed my proxy to http host '172.0.16.200'port 3128 
while I was back I used No Proxy using Firefox>Preferencs>Advanced>Network>Settings
and also from Network>NetworkProxy>None

but while I try to install something I get message to authinticate for proxy server. It asks me for user name and password.


debasish@debasish:~$ sudo cpan App::cpanminus
[sudo] password for debasish: 

Fetching with HTTP::Tiny:
[http://cpan.repo.unpas.ac.id/authors/01mailrc.txt.gz](http://cpan.repo.unpas.ac.id/authors/01mailrc.txt.gz)
HTTP::Tiny failed with an internal error: Could not connect to '172.16.0.200:3128': IO::Socket::INET: connect: timeout at /usr/share/perl/5.14/HTTP/Tiny.pm line 139


Proxy authentication needed!
 (Note: to permanently configure username and password run
   o conf proxy_user your_username
   o conf proxy_pass your_password
     )
Username:  debasish.mukherjee
Warning: Term::ReadKey seems not to be available, your password will be echoed to the terminal!
Password:  dert1234



Trying with
    /usr/bin/wget -O "/home/debasish/.cpan/sources/authors/01mailrc.txt.gz.tmp4734"
to get
    [http://cpan.repo.unpas.ac.id/authors/01mailrc.txt.gz](http://cpan.repo.unpas.ac.id/authors/01mailrc.txt.gz)
--2012-12-18 01:06:16--  [http://cpan.repo.unpas.ac.id/authors/01mailrc.txt.gz](http://cpan.repo.unpas.ac.id/authors/01mailrc.txt.gz)
Connecting to 172.16.0.200:3128...  failed: Connection timed out.
Retrying.

--2012-12-18 01:07:20--  (try: 2)  [http://cpan.repo.unpas.ac.id/authors/01mailrc.txt.gz](http://cpan.repo.unpas.ac.id/authors/01mailrc.txt.gz)
Connecting to 172.16.0.200:3128...



and it ultimately fails


I also can't install from "Ubuntu Software Centre" or update my os as it showing "Requires installation of untrusted packages"


please help
I am really in a trouble.

---

