---
title: "pam_tally"
date: 2006-07-31
forum: General Help
---

### Post by obrouni on 2006-07-31
Hi,

I have just done a dist-upgrade from breezy to dapper. On reboot I found I could no longer login. I traced this to a problem with the pam_tally module I was using to do account lockouts.

I used the live CD to quote out the module in common-auth and common-account files. After doing this I could log in as normal.....great.

Now the question is, how do I get pam_tally working in dapper. No matter what I seem to do, it doesn't work. If I place pam_tally in either of the above two config files I can still log in, but if it is in both I can't and it needs to be in both to work correctly.

Looking at auth.log, nothing seems to be wrong, it simply says that a session has been opened with no errors.

Can anybody shed any light on this problem, or post on how they have configured pam_tally?

---

### Post by obrouni on 2006-08-01
Hi,

Just thought I would post this in case anybody else has this problem. It appears there might be a problem in the current version  of Pam_tally:-

[http://www.redhat.com/archives/pam-list/2005-July/msg00016.html](http://www.redhat.com/archives/pam-list/2005-July/msg00016.html)

Not sure if that is the version in use in Dapper but it is exactlly what happens to me.

---

