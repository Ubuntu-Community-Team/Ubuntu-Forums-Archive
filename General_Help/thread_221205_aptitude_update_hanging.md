---
title: "aptitude update hanging"
date: 2006-07-22
forum: General Help
---

### Post by douga on 2006-07-22
I apologize if this has been covered before -- I couldn't find it. 

If I do a 'sudo aptitude update' it hangs at:

Connecting to us.archive.ubuntu.com (146.137.96.15)

for a while and finally checks out with:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.15), connection timed out

Have I somehow messed up my installation, or is this something that just started happening today?

Thanks,

Doug

---

### Post by Ziox on 2006-07-22
i think the mirror is down, just edit your sources.list to not include any "us." just use archive.ubuntu.com instead of us.archive.ubuntu.com

---

### Post by TheRingmaster on 2006-07-22
> **douga said:**
> I apologize if this has been covered before -- I couldn't find it. 

If I do a 'sudo aptitude update' it hangs at:

Connecting to us.archive.ubuntu.com (146.137.96.15)

for a while and finally checks out with:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.15), connection timed out

Have I somehow messed up my installation, or is this something that just started happening today?

Thanks,

Doug

And also 146.137.96.7 This hangs also

---

