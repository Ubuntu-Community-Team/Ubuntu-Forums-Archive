---
title: "Unable to contact time server"
date: 2012-10-19
forum: General Help
---

### Post by pwabrahams on 2012-10-19
When I attempt to update the time with the time widget and activate automatic updating, I get the message "Unable to contact time server:pool.ntp.org".  I can ping pool.ntp.org, however.  I also tried a few other time servers, with the same result.

However, if I enter the widget with "adjust time automatically" already checked and then click OK, the time does get adjusted.  If I uncheck the box and check it again, then both "Apply" and "OK" give me the error.

What is going on here?

---

### Post by bra|10n on 2012-10-19
[https://bugs.launchpad.net/ubuntu/+source/kde-baseapps/+bug/668748](https://bugs.launchpad.net/ubuntu/+source/kde-baseapps/+bug/668748)

---

### Post by pwabrahams on 2012-10-19
I forgot that I had reported this very same bug back in the days of Maverick. "Plus ça change, plus c'est la même chose."  (Ain't that character picker neat?)

In any event, it seems that if you click OK from the time-setter, it does the job even though it complains.

---

