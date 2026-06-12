---
title: "TZdata Broken?  Here's how to fix it."
date: 2007-10-21
forum: General Help
---

### Post by Ryoushi19 on 2007-10-21
I've noticed that tzdata has a habit of breaking on me, so I'm going to make this post to help anyone who suffers the same thing.  It's a really easy fix.  Here we go!

Open up the console and type "sudo nano /etc/timezone"

Replace whatever it says with "Europe/London"

Reinstall tzdata with your preferred package management tool.

That should do it ^.^
It's a weird fix, but it works.

---

### Post by halfB on 2007-10-22
Thanks for the recommendation.  
Sorry to say, it did not work for me.
Bye

---

### Post by wjhildreth on 2007-10-23
When I tried to reinstall this is what I get.

```

joeh@THJOEH:~$ sudo apt-get install tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tzdata is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tzdata (2007h-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
joeh@THJOEH:~$ 

```

Regards,

Joe

---

