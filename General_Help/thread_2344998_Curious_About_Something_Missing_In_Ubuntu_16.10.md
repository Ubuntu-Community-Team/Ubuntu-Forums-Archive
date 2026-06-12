---
title: "Curious About Something Missing In Ubuntu 16.10"
date: 2016-11-29
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-11-29
I'm just curious about a feature missing in Ubuntu 16.10.  While in any folder when you right click you have things you can do such as New Folder, Paste, Select All, Properties and Open In Terminal.  Where has New Document gone?  It happens on my desktop and laptop so I do not think it is a problem with my download.  Does anyone else notice this?

---

### Post by ian-weisser on 2016-11-29
See bug report: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1632027](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1632027)

---

### Post by shane_faulkinbury2 on 2016-11-29
I've installed Ubuntu 16.10 on my laptop and desktop with two different downloads.  I notice in any folder when you right click you have New Folder, Paste, Select All, Properties and Open In Terminal.  I do not see New Document anymore.  Is this a problem with Ubuntu or with my downloads?  Don't forget they are two different downloads.

---

### Post by mc4man on 2016-11-29
I'm sure someone answered you though their post is curiously missing (linked a bug report
For the moment use gedit to save an empty file in ~/Templates
Name it whatever you'd like the new docu's to be named, then it should show up
(- if not quit & restart nautilus or just log out/in

Edit: I see, you've 2 or 3 posts about same thing ....

---

### Post by lisati on 2016-11-29
Threads merged.

---

### Post by shane_faulkinbury2 on 2016-11-29
Thanks guys, I guess I'll just wait for the fix and do the ~/Templates fix in the mean time.

---

### Post by bra|10n on 2016-11-29
I recall contributing to a similar bug report in 2009 that had over 2000 user-contributions stretching over 6 years that detailed the very same issue. Perhaps Ubuntu will sort this out once and for all.

---

### Post by ian-weisser on 2016-11-29
> **bra|10n said:**
> I recall contributing to a similar bug report in 2009 that had over 2000 user-contributions stretching over 6 years that detailed the very same issue. Perhaps Ubuntu will sort this out once and for all.

Ugh. I usually close bugs like those when I run across them.
If I have to read for 10 minutes, and none of the dozen reporters can clearly explain the real, triage-able problem, then it's usually not worth upstreaming to a developer.
It's even worse when a bug report gets hijacked by a user with an entirely different problem. Then I get to read them arguing about it.
And then there are the users complaining in fixed/closed bugs that the bugfix didn't work for their slightly-different problem.

If you find a super-huge bug report, stay out.
If you really want a bug fixed, make it super-easy for the developer to understand the actual bug (not the symptom). That sometimes takes a bit of work. If the bug is annoying, then the effort is worthwhile.

---

### Post by bra|10n on 2016-11-30
@Ian,

I definitely agree with your philosophy on bugs but in the particular instance I refer to, we had developers split on how to implement what was a very simple feature to what was the Gnome2 desktop in it's heyday. For the record the bug was specific and concise but at least 6 years of bickering ensued (might have been 8 come to think of it)... someone on here who reads this post will surely recall.

All the best.

---

### Post by ian-weisser on 2016-11-30
Ah, developer arguing!
I like reading those bugs. Much more fun.

---

