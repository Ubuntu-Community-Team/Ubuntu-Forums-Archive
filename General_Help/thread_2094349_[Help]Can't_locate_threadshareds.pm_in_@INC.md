---
title: "[Help]Can't locate thread/shareds.pm in @INC"
date: 2012-12-13
forum: General Help
---

### Post by andreiusul on 2012-12-13
I'm using a older version of ubuntu on my dedicated server, before had running perl 5.8.8 and i THINK i've installed correctly ActivePerl 5.14 after comparing many tutorials so I'm sure I dont make mistakes. My hunch is that I need to do some manual configuration of wich I dont know. I'm trying to use a programs that requires 'shared::threads'. If anyone here would be willing to help me with this issue i'm willing even to pay as this thing costs me money and time. Thank you and I'm awaiting your answers.

---

### Post by Habitual on 2012-12-13
terminal >
```
sudo su -
cpan
install shared::thread
``` should do it.

---

### Post by andreiusul on 2012-12-13
> root@noc:~# sudo su -
root@noc:~# cpan
Terminal does not support AddHistory.

cpan shell -- CPAN exploration and modules installation (v1.9402)
Enter 'h' for help.

cpan[1]> install shared::thread
CPAN: Storable loaded ok (v2.20)
Going to read '/root/.cpan/Metadata'
  Database was generated on Wed, 12 Dec 2012 01:07:04 GMT
CPAN: Time::HiRes loaded ok (v1.9719)
Warning: no success downloading '/root/.cpan/sources/authors/01mailrc.txt.gz.tmp22514'. Giving up on it. at /usr/lib/perl5/5.10.1/CPAN/Index.pm line 225
  LWP not available

Trying with "/usr/bin/curl -L -f -s -S --netrc-optional" to get
    "http://www.perl.org/CPAN/authors/01mailrc.txt.gz"
CPAN: Compress::Zlib loaded ok (v2.02)
CPAN: YAML loaded ok (v0.84)
Going to read '/root/.cpan/sources/authors/01mailrc.txt.gz'
............................................................................DONE
Warning: no success downloading '/root/.cpan/sources/modules/02packages.details.txt.gz.tmp22514'. Giving up on it. at /usr/lib/perl5/5.10.1/CPAN/Index.pm line 225

Trying with "/usr/bin/curl -L -f -s -S --netrc-optional" to get
    "http://www.perl.org/CPAN/modules/02packages.details.txt.gz"
Going to read '/root/.cpan/sources/modules/02packages.details.txt.gz'
  Database was generated on Fri, 14 Dec 2012 01:07:03 GMT
  HTTP::Date not available
..............
  New CPAN.pm version (v1.9800) available.
  [Currently running version is v1.9402]
  You might want to try
    install CPAN
    reload cpan
  to both upgrade CPAN.pm and run the new version without leaving
  the current session.


..............................................................DONE
Warning: no success downloading '/root/.cpan/sources/modules/03modlist.data.gz.tmp22514'. Giving up on it. at /usr/lib/perl5/5.10.1/CPAN/Index.pm line 225

Trying with "/usr/bin/curl -L -f -s -S --netrc-optional" to get
    "http://www.perl.org/CPAN/modules/03modlist.data.gz"
Going to read '/root/.cpan/sources/modules/03modlist.data.gz'
............................................................................DONE
Going to write /root/.cpan/Metadata
Warning: Cannot install shared::thread, don't know what it is.
Try the command

    i /shared::thread/

to find objects with matching identifiers.

cpan[2]>


I've tried and that's what I got. What's the issue there? Not even my old buddy google could get me any info to solve that..

---

### Post by Habitual on 2012-12-14
my bad:
```
sudo 
cpan
install threads::shared
```

Sorry about that.
[[COLOR=Black][/COLOR]]("http://search.cpan.org/%7Ejdhedden/threads-shared-1.42/lib/threads/shared.pm")[[COLOR=Black][/COLOR]]("http://search.cpan.org/%7Ejdhedden/threads-shared-1.42/lib/threads/shared.pm")

---

### Post by Lars Noodén on 2012-12-14
You are likely to break things if you go outside the package management system.  At the very best it will be extra work.  Does the package "libthreads-shared-perl" not give you what you need?

```

sudo apt-get update
sudo apt-get install libthreads-shared-perl 

```

---

