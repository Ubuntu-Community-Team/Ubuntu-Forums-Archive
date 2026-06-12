---
title: "libc6 issues PLEASE HELP!!!"
date: 2005-05-19
forum: General Help
---

### Post by ringding on 2005-05-19
it seems I may have buggered my system.

I was getting: Depends: libc6 (>= 2.3.2.ds1-21) quite a bit.

So I installed using **dpkg -i libc6_2.3.2.ds1-21_i386.deb** (I know now not the right thing to do) yeah yeah I know i am an idiot.

My question is simple: Can I revert back to the original libc6 config, if so, how?  OR am I hosed completly?

My system is running but I get 3 Broken packages when starting Synaptic. And now I cannot install any new packages.
Go for a remove and tons of packages come up to be removed. NOT GOOD.

HELP!!!!

---

### Post by jcooper on 2005-05-19
Do you still have the .deb you used? If so, a dpkg uninstall should remove just that package, meaning you can then apt-get dist-upgrade to make sure everything else is "fixed".

---

### Post by ringding on 2005-05-19
Yes I still have the .deb package! 

Tried:
# dpkg -r libc6_2.3.2.ds1-21_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

So then:
# dpkg -L libc6_2.3.2.ds1-21_i386.deb
Package `libc6_2.3.2.ds1-21_i386.deb' is not installed.

# dpkg -l libc6_2.3.2.ds1-21_i386.deb
No packages found matching libc6_2.3.2.ds1-21_i386.deb.

# dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libc6-dev            GNU C Library: Development Libraries and Header Files

 # dpkg --configure libc6-dev
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.3.2.ds1-20ubuntu13); however:
  Version of libc6 on system is 2.3.2.ds1-21.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev




is this because it is considered a broken install by Synaptic?

---

### Post by ringding on 2005-05-19
Well it seems I may have fixed my issue with installing 
**libc6_2.3.2.ds1-21_i386.deb**

I installed:
**libc6_2.3.2.ds1-20ubuntu13_i386.deb**

 # dpkg -i libc6_2.3.2.ds1-20ubuntu13_i386.deb
dpkg - warning: downgrading libc6 from 2.3.2.ds1-21 to 2.3.2.ds1-20ubuntu13.
(Reading database ... 129505 files and directories currently installed.)
Preparing to replace libc6 2.3.2.ds1-21 (using libc6_2.3.2.ds1-20ubuntu13_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.3.2.ds1-20ubuntu13) ...
Current default timezone: 'America/New_York'.
Local time is now:      Thu May 19 11:48:59 EDT 2005.
Universal Time is now:  Thu May 19 15:48:59 UTC 2005.
Run 'tzconfig' if you wish to change it.


I run synaptic and no more broken packages.......so far so good! :grin:

---

