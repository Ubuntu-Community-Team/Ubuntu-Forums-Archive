---
title: "Lightning Stopped Syncing Calendars"
date: 2019-10-30
forum: General Help
---

### Post by speartip on 2019-10-30
Not had this situation before & have used Thunderbird/Lightning for many years.
I Triple boot mint xfce - Ubuntu - Kubuntu. All 18.04.3.
All of a sudden lightning has stopped syncing my Google Calendar. I set up my Calendar in the usual way, signing in through Google accounts, then acknowledging on my Mobile Phone the 2 step verification protocol. My Calendar appears then quickly disappears. Under the Calendar tab Google is greyed out in the left panel. If I right click, then Properties, I can switch the Calendar on, but as soon as I click OK, I end up going through the Google sign in again & the Verification, & just end up at square one with the calendar greyed out & switched off. Endless loop. I assumed the problem was at Google's end, So tried with my Zoho Calendar, same problem. New Thunderbird profile, same problem. Same on all 3 of my installations, so have to assume this is a Thunderbird/Lightning issue, as all works fine through Kontact on Kubuntu.
Anyone else have this issue? Or any suggestions?

---

### Post by walts48 on 2019-10-30
Sounds like you are having the same problem users are having creating a new email account for Google mail.

For informational purposes only as the bug has been confirmed. You can follow the bug and see when it gets fixed.

[https://bugzilla.mozilla.org/show_bug.cgi?id=1592407](https://bugzilla.mozilla.org/show_bug.cgi?id=1592407)

---

### Post by speartip on 2019-10-30
Hi walts48.
After reading the Bug report, I think you are right. Just for information, I installed Evolution, & did get an extra message about Google not recognizing the app or something, but unlike Thunderbird it allowed me to proceed. So Evolution works fine. Google have changed something though, & because my Zoho calendar is linked to my Google one, it's causing me the same problem. 
I will wait & see if the issue gets resolved.

---

### Post by #&amp;thj^% on 2019-10-30
@speartip you could "try" to install the Lightning beta extension from the **xpi **file for Thunderbird. You can download the latest Lightning here: [s][https://ftp.mozilla.org/pub/calendar/lightning/candidates/6.2b6-candidates/build1/linux-x86_64/](https://ftp.mozilla.org/pub/calendar/lightning/candidates/6.2b6-candidates/build1/linux-x86_64/)[/s]
Pointed out below by speartip, outdated link.

---

### Post by rbmorse on 2019-10-30
Gnome-calendar quit syncing, too, so it's not just Lightning.

---

### Post by speartip on 2019-10-30
@1fallen. The link you gave points to lightning builds that are 18 months old. The problem has only arisen in the last day or 2. Thanks Anyway.
@rbmorse. Not a surprise. This is Google ramping up it's security. Should be grateful really. It's just a bit annoying.

---

### Post by #&amp;thj^% on 2019-10-30
> **speartip said:**
> @1fallen. The link you gave points to lightning builds that are 18 months old. The problem has only arisen in the last day or 2. Thanks Anyway.


Thanks for that speartip, that link was given to me by a Dev, I'll let him know about that. I also pointed him to this thread here.
I'll fix my post. ;)

---

### Post by rbmorse on 2019-10-30
Speartip: Yes, quite agree.

---

### Post by walts48 on 2019-10-31
Thunderbird 68.2.1 has been released fixing the "Google services are currently disrupted" bug.

If you are using a distribution version of 60.9.0 you will have to wait for Ubuntu to provide an update.

---

