---
title: "Apache crashes"
date: 2008-01-06
forum: General Help
---

### Post by jwag on 2008-01-06
Hello,

I'm having issues with Apache2 crashing.

This is what appears in our error_log file:

[Fri Jan 04 08:10:19 2008] [alert] (11)Resource temporarily unavailable: setuid: unable to change to uid: 30
[Fri Jan 04 08:10:19 2008] [alert] (11)Resource temporarily unavailable: setuid: unable to change to uid: 30
[Fri Jan 04 08:10:19 2008] [alert] (11)Resource temporarily unavailable: setuid: unable to change to uid: 30
[Fri Jan 04 08:10:19 2008] [alert] (11)Resource temporarily unavailable: setuid: unable to change to uid: 30
[Fri Jan 04 08:10:20 2008] [alert] Child 8727 returned a Fatal error... Apache is exiting!
[Fri Jan 04 08:10:20 2008] [emerg] (43)Identifier removed: couldn't grab the accept mutex
[Fri Jan 04 08:10:20 2008] [emerg] (43)Identifier removed: couldn't grab the accept mutex
[Fri Jan 04 08:10:20 2008] [emerg] (43)Identifier removed: couldn't grab the accept mutex
[Fri Jan 04 08:10:20 2008] [emerg] (43)Identifier removed: couldn't grab the accept mutex
[Fri Jan 04 08:10:20 2008] [emerg] (43)Identifier removed: couldn't grab the accept mutex
[Fri Jan 04 08:10:20 2008] [emerg] (43)Identifier removed: couldn't grab the accept mutex
[Fri Jan 04 08:10:20 2008] [emerg] (43)Identifier removed: couldn't grab the accept mutex
[Fri Jan 04 08:10:23 2008] [emerg] (22)Invalid argument: couldn't grab the accept mutex
(this error repeats about 50 times before this last one)
[Fri Jan 04 08:11:07 2008] [emerg] (22)Invalid argument: couldn't release the accept mutex

The error says it's unable to change to uid 30, but nothing besides the user for apache is set to have this uid, so I don't think that's the main issue.

Looking at the access_log file, it seems that immediately before this happening, somebody is visiting a webpage on our server that has 36 images on it.  None of the other access_log entries are anywhere near 36 images, just this one.  Perhaps there is a configuration setting with Apache that is limiting the number of processes Apache can have at once and causing this?  Any other ideas?

Thanks for your help,
Jason

---

### Post by sthurgood on 2008-01-19
I've got the same problem on a Debian Etch install, albeit with uid=33 rather than 30.

Something like: 

[Sat Jan 19 02:27:27 2008] [alert] (11)Resource temporarily unavailable: setuid: unable to change to uid: 33
[Sat Jan 19 02:27:29 2008] [alert] (11)Resource temporarily unavailable: setuid: unable to change to uid: 33
[Sat Jan 19 02:27:30 2008] [alert] (11)Resource temporarily unavailable: setuid: unable to change to uid: 33
[Sat Jan 19 02:27:30 2008] [alert] (11)Resource temporarily unavailable: setuid: unable to change to uid: 33
[Sat Jan 19 02:27:45 2008] [alert] Child 6072 returned a Fatal error... Apache is exiting!

Then:

[Sat Jan 19 02:28:57 2008] [emerg] (43)Identifier removed: couldn't grab the accept mutex
[Sat Jan 19 02:29:00 2008] [emerg] (22)Invalid argument: couldn't grab the accept mutex
[Sat Jan 19 02:29:00 2008] [emerg] (22)Invalid argument: couldn't release the accept mutex
[Sat Jan 19 02:29:00 2008] [emerg] (22)Invalid argument: couldn't grab the accept mutex
[Sat Jan 19 02:29:00 2008] [emerg] (22)Invalid argument: couldn't grab the accept mutex

---

