---
title: "Starting Apps CPU at 100%, slow (not ipv6 or network problem)"
date: 2007-08-25
forum: General Help
---

### Post by sexus6 on 2007-08-25
Hi

I have a problem when I start my apps. I have installed Ubuntu Feisty 32 in a Atlhon 1700 Xp with 700 mb ram.

When I start one app (whatever) the top (or gnome system monitor) marks 100% CPU usage in the app process. This makes the system that freezes for a seconds, and the apps startup are very slow. This is the times that I get:

GIMP
real 36.135 seconds
FIREFOX
real 17.153 seconds
GEDIT
real 14.017 seconds
GCALTOOL (calculator)
real 13,023 seconds

I read some posts here and in google, and I make this tries:

Disable ipv6 => nothing happens
Adjuts /etc/hosts file (to put 127.0.0.1 localgost hostname, etc) => nothing
Install preload => nothing happens
Disable unused services (bluetooth, etc) => nothing happens
dma => the dma is active in the two HD. I am sure.

I make some tests about the HD speed, and I see that was normal:
/dev/hda1:
 Timing cached reads:   400 MB in  2.01 seconds = 199.42 MB/sec
 Timing buffered disk reads:  100 MB in  3.02 seconds =  33.14 MB/sec

/dev/hdb1:
 Timing cached reads:   358 MB in  2.00 seconds = 178.77 MB/sec
 Timing buffered disk reads:  124 MB in  3.04 seconds =  40.86 MB/sec

If I use the ubuntu livecd, I think that the times are normal.... for example, gedit startup time is 6 seconds...

What's wrong?

---

