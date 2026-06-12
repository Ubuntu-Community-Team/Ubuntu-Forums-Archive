---
title: "libapache2-mod-mono AND libapache2-mod-php5 (again)"
date: 2008-04-25
forum: General Help
---

### Post by xixsixxix on 2008-04-25
I suppose you could consider this a reopening of a previous unacceptably ended 8.04 Hardy development thread here:

[http://ubuntuforums.org/showthread.php?t=734987]("http://ubuntuforums.org/showthread.php?t=734987")

> I'm trying to run both mod-mono and mod-php5 on my apache2 server.
I have mod-php5 installed, but when I try to install mod-mono it wants to remove mod-php5.

I guess it's got something to do with mono requiring apache2-worker and php5 requiring apache2-prefork.

Anyone got a clue on how to fix this?
> No, because both modules are build against different workers of Apache you can't run them together.

PHP5 is not thread-safe, that is why it is build against the slower prefork worker.

I just upgraded from 7.10 Gutsy to 8.04 Hardy yesterday with the expected complications (initial mesa/GL errors, reworking WPA wifi support, having to reinstall development libraries, etc.)

The upgrade also removed apache2 and php5, which were a simple reinstall, but I generally run the Mono Apache plugin as well(ASP.NET support).

It appears that now libapache2-mod-php5 depends on apache2-mpm-prefork where as libapache2-mod-mono depends on [conflicting] apache2-mpm-worker. 

I understand the obvious prefork/worker incompatibility, but under Gutsy I was able to run mono and php5 side by side. I don't recall at this point whether they were running off prefork or worker, but they **did** both run on whichever of the shared lib it was.

It's hardly acceptable at this point to have to stop running either PHP or ASP because of an upgrade.

Anyone had any luck running both libapache2-mod-php5 and libapache2-mod-mono together under Hardy?

---

