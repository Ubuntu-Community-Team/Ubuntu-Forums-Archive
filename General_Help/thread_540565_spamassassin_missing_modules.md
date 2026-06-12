---
title: "spamassassin missing modules"
date: 2007-09-01
forum: General Help
---

### Post by posterboy on 2007-09-01
Ubuntu 7.0.4

I have SA working, but it's missing a lot of pm's that are listed as required. Look:

 module not installed: Mail::SPF::Query ('require' failed)
[9445] dbg: diag: module not installed: IP::Country::Fast ('require' failed)
[9445] dbg: diag: module not installed: Razor2::Client::Agent ('require' failed)
[9445] dbg: diag: module not installed: Net::Ident ('require' failed)
[9445] dbg: diag: module not installed: IO::Socket::INET6 ('require' failed)
[9445] dbg: diag: module not installed: IO::Socket::SSL ('require' failed)
[9445] dbg: diag: module installed: Compress::Zlib, version 1.42
[9445] dbg: diag: module installed: Time::HiRes, version 1.86
ALL of this is important for functioning, although it "works" without them.
I can't find any place to get these. I haven't tried CPAN, as that has proven troublesome to me in the past. Any suggestions?

---

### Post by PaulFr on 2007-09-01
I assume you mean the **perl -MCPAN -e shell** way caused you problems. I had a problem with Net::Server some time in the past, but for that I used the following manual procedure and once amavisd-new could handle the new Net::Server version, I reverted to using CPAN.

You could actually download the appropriate .tar compressed file from **[http://search.cpan.org/](http://search.cpan.org/)**  (the download link is at the top right of the individual package page) and install it using instructions given at **[http://www.cpan.org/modules/INSTALL.html](http://www.cpan.org/modules/INSTALL.html)**. This means that you will have to download all the dependencies yourself, so I would urge you to consider CPAN itself.

---

### Post by posterboy on 2007-09-02
Thank you. CPAN did result in getting a few modules. On the one's I really need, it either can't find it, ie. razor2::client::agent, or it bombs during install with pages of error information. My usual experience with cpan. I just installed ubuntu last week, a search at search cpan does not find razor2... Bummer. Anyway, I got a few, so thanks, for that.
Ray

---

