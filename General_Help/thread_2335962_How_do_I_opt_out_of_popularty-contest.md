---
title: "How do I opt out of popularty-contest?"
date: 2016-09-03
forum: General Help
---

### Post by 894532185610544562 on 2016-09-03
Good evening.

I [SIZE=2]**wasn't**[/SIZE] given the option to opt-out during the Ubuntu Mate 16.04.1 installation process so I assume that that it's running:

```
(root) CMD (   test -x /etc/cron.daily/popularity-contest && /etc/cron.daily/popularity-contest --crond)
```

...Attempting to removing the package manually produces the following, which I balk at:

[IMG]https://i.imgur.com/X4hLcW6.png[/IMG]

-------------------------------------------------------------------------------------------------------------------------------------------

There's an ask thread [here]("http://askubuntu.com/questions/84831/removing-popularity-contest-without-trashing-the-system") with @enzotib saying that **ubuntu-standard** is a "metapackage" and therefore removing it does not brick the system. I would like some additional confirmation on that here.

[This wiki documentation]("https://help.ubuntu.com/community/UbuntuPopularityContest") says it's not enabled by default -- however that wiki entry is over 5 years old and refers to [an out-of-date screenshot]("https://help.ubuntu.com/community/UbuntuPopularityContest?action=AttachFile&do=view&target=software_sources_screenshot.png") that no longer applies to the current "software sources" gui as there is no "statistics" tab mentioned...so that entry needs to be updated. In the meantime, I would either like to safely remove the package or **opt-out**. Thank you.

---

### Post by TheFu on 2016-09-03
You can safely purge that package.  Don't be afraid to try things. That is the best way to learn. 
Also, be certain you have daily backups, so if anything bad does happen, it is just a restore away. These days, there really isn't any good excuse NOT to have solid backups.

---

### Post by 894532185610544562 on 2016-09-03
Ok, per the bold items in [the popcon FAQ]("http://popcon.ubuntu.com/FAQ"):
[QUOTE=Debian Devs]Q) What information is reported by popularity-contest ?

A) popularity-contest reports the system architecture you use, the version of
   popularity-contest you use and the list of packages installed on your
   system. [B]For each package, popularity-contest looks at the most recently used
   [/B](based on atime)[B] files, and reports the filename, its last access time
   [/B](atime)** and last change time **(ctime). However, some files are not
   considered, because they have unreliable atime.[/QUOTE]

What exactly are the "files" specified? Are they relevant "package files" only or...(other)? We need more clarification on this.

From what I gather looking at the crontab file in **cron.d**, it does run daily at 22:00 and checks to see if it uploaded at least once in the past week, if not then upload now and then wait a week before sending again. The FAQ seems to be out of date saying "popularity-contest is run by the weekly cron job" (which is at 06:47 local time every Sunday.) They must have bumped it up to daily to make the extra daily checks in case the machine was off for an extended period.

And speaking of things being out of date, someone here also needs to edit the [cron wiki ]("https://help.ubuntu.com/community/CronHowto#Crontab_Lines")-- the last "time-and-date field" in a crontab line can indeed be a '7' -- to also signify "Sunday". 0 == 7 in this instance.

The "better" news is: that I found evidence this contest is set to "no participation" by default. (However I would like confirmation on that from the mods here.) The "no participation" settings are found in **/etc/popularity-contest.conf** and **/usr/share/popularity-contest/default.conf** and that's what the daily contest loads up before proceeding with a run.

---

### Post by TheFu on 2016-09-03
Nobody here works for Canonical. We are all volunteers.

---

### Post by 894532185610544562 on 2016-09-03
> **TheFu said:**
> Nobody here works for Canonical. We are all volunteers.

That's irrelevant. I've made 2 Ubuntu wiki update suggestions for the community members here and also someone should email the Debian popcon devs to get their FAQ up to date as well -- especially considering the nature of potentially sensitive information being involved here.

---

### Post by wildmanne39 on 2016-09-03
> That's irrelevant. I've made 2 Ubuntu wiki update suggestions for the community members here and also someone should email the Debian popcon devs to get their FAQ up to date as well -- especially considering the nature of potentially sensitive information being involved here. 
Sure go ahead and take care of that you are as much a member of this community as everyone else here.

I am running ubuntu mate and the first file confirms that it is set to no by default.
Thanks!

---

### Post by QIII on 2016-09-03
> **894532185610544562 said:**
> That's irrelevant. I've made 2 Ubuntu wiki update suggestions for the community members here and also someone should email the Debian popcon devs to get their FAQ up to date as well -- especially considering the nature of potentially sensitive information being involved here.

Please do not make demands of the community.

> And speaking of things being out of date, someone here also needs to edit the cron wiki -- the last "time-and-date field" in a crontab line can indeed be a '7' -- to also signify "Sunday". 0 == 7 in this instance.

Since 0 to 6 are sufficient to cover all 7 days of the week, what use would there be in adding another value?  Days of the week are zero-based:  0 represents the first day of the week, which is Sunday.  Adding 7 is redundant.  There is certainly no urgency in changing that in the wiki.

> The FAQ seems to be out of date saying "popularity-contest is run by the weekly cron job" (which is at 06:47 local time every Sunday.) They must have bumped it up to daily to make the extra daily checks in case the machine was off for an extended period.

OK.  There are contacts [here]("http://popcon.ubuntu.com/").  They might appreciate a heads up.

"Someone here" includes you.  We are not Canonical employees.  Canonical developers do not hang out here as a rule.  The popularity-contest devs probably don't hang around here, either.  These things *are* relevant.

---

