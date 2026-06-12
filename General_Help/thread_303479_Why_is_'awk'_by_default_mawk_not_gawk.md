---
title: "Why is 'awk' by default mawk not gawk?"
date: 2006-11-20
forum: General Help
---

### Post by fivemack on 2006-11-20
Hi.

At Global Phasing, we write software which does a lot of file processing by calling awk from perl scripts.  Various of our users have adopted Ubuntu, and we were getting rather odd bugs which we traced to awk on dapper being by default a 1996 version of mawk.

It's easy to check that gawk is installed, but I'm just wondering why such an old awk is used by default.

---

### Post by TheRingmaster on 2006-11-20
what are you talking about?

---

### Post by frodon on 2006-11-20
He is talking about awk which is a powerfull text handling tool.
[https://launchpad.net/distros/ubuntu/+source/gawk/1:3.1.5.dfsg-4](https://launchpad.net/distros/ubuntu/+source/gawk/1:3.1.5.dfsg-4)

@fivemack, maybe you can ask this directly to the developpers maybe filling a bug report saying that the version used is too old.

---

