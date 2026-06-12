---
title: "jpilot will not sync in 12.04 unless invoked by &quot;sudo&quot; in terminal"
date: 2012-12-17
forum: General Help
---

### Post by revtds on 2012-12-17
In 11.04 before it went EOL, jpilot was working very well with my Handspring Visor.  When I was informed 11.04 wasa EOL, I debated and made the upgrade.

Now, jpilot will only sync with my Visor if I invoke jpilot from CL with "sudo".  Jpilot will not read those files that have been synced now, until I chown all the files in .jpilot back to my user name, since they all get changed to root ownership.

While this works, it is exceptionally awkward.  The pilot-link commands all work well, and again, only with "sudo" invocation.

I had massive permissions problems when I tried 12.04 on introduction, and returned to 11.04 for that reason. It now appears that permissions are still my problem, and I haven't a clue to even know where to start to iron out the permissions/ownership issues.

I have been using Ubuntu since Breezy, but still am a noob on many things.

---

### Post by revtds on 2012-12-20
bump?

---

### Post by morgan71 on 2013-07-31
You need to be a member of the group dialout.

---

