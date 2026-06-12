---
title: "problem with apt-index-watch"
date: 2006-12-16
forum: General Help
---

### Post by sblanzio on 2006-12-16
Hi, i've noticed I have a problem with this process "apt-index-watch" that is loading every about 5 secs and keeps 100% of my cpu busy for few moments.
It doesn't seem to stop. I tried to reboot but it's always there.

I found some old threads where they said it was a bug in Edgy development but nothing more recent.

I'm updated with all Edgy updates.

Any ideas?

thanks

---

### Post by bapoumba on 2006-12-16
[https://launchpad.net/distros/ubuntu/+source/libapt-front/+bug/64531]("https://launchpad.net/distros/ubuntu/+source/libapt-front/+bug/64531")
[https://launchpad.net/distros/ubuntu/+source/libapt-front/+bug/61518]("https://launchpad.net/distros/ubuntu/+source/libapt-front/+bug/61518")
Please check these bug reports.

---

### Post by Tulsapoke on 2007-02-19
I had this problem... followed the links.  Read through them and this is the fix that worked for me.

sudo apt-get install --reinstall debtags

Says that it reinstalls this debtags program that causes the bug.

---

### Post by sblanzio on 2007-04-03
possible solution (for a while) is to run

sudo touch /var/cache/apt-index-watcher/*

HIH
bye

---

