---
title: "Awstats has stopped updating ..."
date: 2008-03-29
forum: General Help
---

### Post by David Tomic on 2008-03-29
Hi folks,

This one has got me completely puzzled, not least of all because it's worked flawlessly for months now, and has all of a sudden just stopped working completely out of the blue.

I've been using a cron task to update my awstats data every 15 minutes.

```
*/15 * * * * www-data /usr/lib/cgi-bin/awstats.pl -config=einstein.dontexist.net -update
```

Like I said this has worked perfectly for months, but has suddenly just mysteriously stopped working.

All my other cron tasks are still executing properly, and I can still update awstats manually using the command:

```
sudo /usr/lib/cgi-bin/awstats.pl -config=einstein.dontexist.net -update

```

Any ideas / advice about fixing this?

Regards,

--David Tomic

---

