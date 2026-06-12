---
title: "Cannot download files with firefox 43"
date: 2015-12-22
forum: General Help
---

### Post by spazzeri on 2015-12-22
I have two User accounts on my machine, user1 and user2.


In user1 account, Firefox downloads fail: if I click on a link to a something like a zip file, or choose 'Save link as...', no dialog window appears and the download fails.


The same problem occurs in Safe Mode, or in a fresh Firefox profile.


It also occurs in a Guest session.


In user2 account, where Firefox already had a profile before the problem started to appear, things work as usual.


Versions: Firefox 43.0, Ubuntu 14.04


Ideas welcome.

---

### Post by lou6 on 2015-12-22
The same thing here, right after FF43 installed. After wasting an hour trying things (including wiping the mime-types) and searching the internet I gave up and restarted Ubuntu. When The system came back up FF43 was able to download normally.

Just happened again a few minutes ago. This time I immediately restarted and all is OK.

I see that this has been confirmed as a bug on Launchpad but no action taken yet.

---

### Post by spazzeri on 2015-12-22
Please post a link to the bug on Launchpad.

---

### Post by u-mock on 2015-12-23
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1527884](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1527884)

---

### Post by spazzeri on 2015-12-23
Thanks.
It works after a machine restart here too.

---

### Post by lou6 on 2015-12-24
Mozilla appears to have identified the problem - fix should be coming (probably after the holidays).

[https://bugzilla.mozilla.org/show_bug.cgi?id=1233434](https://bugzilla.mozilla.org/show_bug.cgi?id=1233434)

---

### Post by lou6 on 2016-01-08
Hard to believe but this is STILL not fixed!

Check out the latest bugzilla entries at the site previously linked (see above) - one guy actually says "no rush on pushing the fix - it doesn't affect Windows users".

Will Linux users always be second-class citizens?

---

### Post by spazzeri on 2016-01-08
[https://www.mozilla.org/en-US/firefox/43.0.4/releasenotes/](https://www.mozilla.org/en-US/firefox/43.0.4/releasenotes/) mentions a fix "Multi-user GNU/Linux download folders can be created ([Bug 1233434]("https://bugzilla.mozilla.org/show_bug.cgi?id=1233434"))"

---

