---
title: "Question about apt-get and dpkg"
date: 2007-01-08
forum: General Help
---

### Post by chapterthree on 2007-01-08
Hi All,

I am currently running 6.10.  I noticed that the latest version available in the stable repo's of gaim seems to be 2.0.0beta3.  (I am using gaim in this example, but this would apply to any package).

Let's say I want to upgrade to 2.0.0beta5.  I should be able to find a .deb package and use dpkg -i <package name> to upgrade my gaim installation to 2.0.0beta5, correct?

Then, let's say in a month gaim is updated to 2.1.0 in the stable repo's.  If I do an apt-get update && apt-get upgrade, would my 2.0.0beta5 be upgrade to 2.1.0, or would it fail because I manually installed beta5?

My basic question is, can I install .deb's over top of packages that were installed with apt-get without any issues as to further compability/functionality?

I hope this makes sense.

Thanks!

---

### Post by WiseElben on 2007-01-08
Yes, it will automatically update it for you once it is in the repos. Or at least, that's what happened to me. =o

---

