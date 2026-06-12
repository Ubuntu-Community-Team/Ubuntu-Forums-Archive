---
title: "SSHFS slow performance / random freezes"
date: 2013-05-10
forum: General Help
---

### Post by john_navarro on 2013-05-10
I've successfully used SSHFS since Ubuntu 11.04. However, with the 13.04 the SSHFS behavior has changed. The problem I experience is a system slowdown/freeze that seems to come and go every 3 seconds or so. Here is the command I use to start the session:

sshfs -o cache=yes,workaround=all user@host:/ ~/rs

To recreate the issue I simply copy a file from my local hard drive to ~/rs/tmp/.  for example. After about 2-3 seconds the entire desktop will freeze for about 2 seconds or so then unfreeeze for about 1 second. It freezes again then unfreezes. This continues until either the copy finishes or I Ctrl-C out of it.

I've tried various sshfs options and also disabled IPv6 but the problem persists. I'm hoping someone may be able to offer some advice that can get this fixed.

Thanks,
john

Ubuntu 13.04 64bit, Gnome desktop, Dell D640 laptop

---

### Post by will007 on 2014-01-06
Same issues here!
That's one reason I used Mate, Cinnemon, and so on, but actually I would like to use gnome-shell.

---

