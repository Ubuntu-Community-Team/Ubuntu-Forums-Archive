---
title: "OTR plugin with Pidgin -- Anybody got this to work??"
date: 2007-07-13
forum: General Help
---

### Post by kevdog on 2007-07-13
Found a backported Gusty version of pidgin for feisty:
[http://howto.landure.fr/gnu-linux/ubuntu-feisty-fawn-1/software-for-ubuntu-feisty-fawn/pidgin-previously-gaim-on-ubuntu-feisty-fawn](http://howto.landure.fr/gnu-linux/ubuntu-feisty-fawn-1/software-for-ubuntu-feisty-fawn/pidgin-previously-gaim-on-ubuntu-feisty-fawn)

Just cant get the OTR plugin to work.  When I go to generate the keys, nothing happens.

Anybody have any ideas???

---

### Post by schallstrom on 2007-08-27
Maybe I got the same problem. When pidgin tries to generate the keys, a window pops up saying "Please wait - Generating private key for [email]foo@bar.com[/email] (Jabber)..." and the application seems to hang there. Nothing happens anymore. When I try to close the windows pidgin crashes.

I just started pidgin with strace and this is what I see:
```

gettimeofday({1188206392, 943306}, NULL) = 0
getrusage(RUSAGE_SELF, {ru_utime={3, 240202}, ru_stime={0, 240015}, ...}) = 0
time(NULL)                              = 1188206392
times({tms_utime=324, tms_stime=24, tms_cutime=8, tms_cstime=1}) = 1890528631
gettimeofday({1188206392, 951186}, NULL) = 0
getrusage(RUSAGE_SELF, {ru_utime={3, 248203}, ru_stime={0, 240015}, ...}) = 0
time(NULL)                              = 1188206393
times({tms_utime=324, tms_stime=24, tms_cutime=8, tms_cstime=1}) = 1890528642
gettimeofday({1188206393, 61470}, NULL) = 0
getrusage(RUSAGE_SELF, {ru_utime={3, 252203}, ru_stime={0, 240015}, ...}) = 0
time(NULL)                              = 1188206393
times({tms_utime=325, tms_stime=24, tms_cutime=8, tms_cstime=1}) = 1890528642
gettimeofday({1188206393, 64310}, NULL) = 0
getrusage(RUSAGE_SELF, {ru_utime={3, 256203}, ru_stime={0, 240015}, ...}) = 0
time(NULL)                              = 1188206393
times({tms_utime=325, tms_stime=24, tms_cutime=8, tms_cstime=1}) = 1890528643
open("/dev/random", O_RDONLY)           = 16
select(17, [16], NULL, NULL, {3, 0})    = 1 (in [16], left {3, 0})
read(16, "a\35[\16;\2\377v\332\221\235-\34\313Xx\215\311", 300) = 18
select(17, [16], NULL, NULL, {3, 0})    = 0 (Timeout)
select(17, [16], NULL, NULL, {3, 0})    = 0 (Timeout)
select(17, [16], NULL, NULL, {3, 0})    = 0 (Timeout)
select(17, [16], NULL, NULL, {3, 0})    = 0 (Timeout)
select(17, [16], NULL, NULL, {3, 0})    = 0 (Timeout)
select(17, [16], NULL, NULL, {3, 0})    = 0 (Timeout)

```

This last line gets repeated to infinity. Unfortunately I'm not elite enough to make much sense out of this...

---

### Post by schallstrom on 2007-08-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gaim-otr/+bug/97010](https://bugs.launchpad.net/ubuntu/+source/gaim-otr/+bug/97010) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There's also a launchpad bug report where someone is stating that it works if you just wait long enough. I can't confirm this so far.

Edit: It really works if you wait very long. On my Thinkpad T30 it took about 30 minutes.

---

### Post by kevdog on 2007-08-27
I think I got this to work, however I had to compile the module from source.  Why I said I think is that Ive never tried it with anyone.  I did manage to generate the keys, and it didnt take 30 minutes, maybe a minute or two. Im also not getting any errors when I try to configure the plugin or any delays.

I obtained the source from:
[http://www.cypherpunks.ca/otr/](http://www.cypherpunks.ca/otr/)
(From same people that brought you MixMaster -- so you know its good!)

I also found a bunch of other plugins here that I really like, I had to compile them from source, and all of them do not work (as noted on the web page).
[http://plugins.guifications.org/trac/wiki/PluginPack](http://plugins.guifications.org/trac/wiki/PluginPack)

I dont know if you have ever compiled form source code before, but you will be impressed if you manage to get everything working.  It works great, much better than any deb file I downloaded before.  

Good luck!

---

