---
title: "End of Life/Burial Process for 15.04?"
date: 2015-09-25
forum: General Help
---

### Post by roland-logikalsolutions on 2015-09-25
I saw a post today which claims 15.04 "ends" in January 2016. Ordinarily I wouldn't care about splitting hairs for such a statement, but, is there a link which documents the burial process for 15.04?

What I'm asking is this: Does end in January simply mean they stop doing development and bug fixes? (Not that bugs get fixed in Linux by any means other than dropping support for the version they were reported against.)

Or, does it mean in January 2016 they turn the 15.04 repositories off thus making it nearly impossible to continue installing 15.04?

The first doesn't impact me, but the second is a horrible thing.

Thanks,

---

### Post by coffeecat on 2015-09-25
Yes, yes and yes. All the non-LTS releases have a 9-month life, after which there are no bugfixes or updates and the repositories are moved. This has been so since 13.04. 15.10 will be coming out next month, which will give you plenty of time to upgrade before 15.04 becomes end of life in January. 

If you find the short life of the interim releases to be inconvenient or otherwise undesirable, it is best to stick with the LTS (long-term support) releases which are supported for 5 years. These currently are 12.04, which becomes end-of-life in 2017, and 14.04 which becomes end-of-life in 2019. The next LTS will be 16.04, to be released next April.

---

### Post by Bucky Ball on 2015-09-25
Have a look [here]("https://wiki.ubuntu.com/Releases") for a full list of births, deaths and marriages.

---

### Post by deadflowr on 2015-09-25
> [COLOR=#000000]Does end in January simply mean they stop doing development and bug fixes? [/COLOR]
They stopped development the day it was released back in April.
And bug fixes are geared toward security and not feature-related.
If any feature-related bug fixes have come, they would more likely have been during the release's early days.

Prior to the new release schedule, when a release hit end of life, the repos moved quickly out of the normal archive servers and into the old-release servers.
But since the switch to 9-month, those repos seem to sit in the normal servers longer. fwiw

---

### Post by PaulW2U on 2015-09-25
> **roland-logikalsolutions said:**
> I saw a post today which claims 15.04 "ends" in January 2016. Ordinarily I wouldn't care about splitting hairs for such a statement, but, is there a link which documents the burial process for 15.04?
Not that I know of. You might have to piece together several Wiki pages before you see the complete picture.

A starting point for Ubuntu 15.04 would be:- [https://wiki.ubuntu.com/VividVervet/ReleaseSchedule](https://wiki.ubuntu.com/VividVervet/ReleaseSchedule)
> **deadflowr said:**
> They stopped development the day it was released back in April.
And bug fixes are geared toward security and not feature-related.
If any feature-related bug fixes have come, they would more likely have been during the release's early days.

Prior to the new release schedule, when a release hit end of life, the repos moved quickly out of the normal archive servers and into the old-release servers.
But since the switch to 9-month, those repos seem to sit in the normal servers longer. fwiw
Thanks deadflowr. I've seen many posts here which imply as soon as a release becomes "End-of-Life" that the repositories are closed. I can't remember that ever being the case.

@roland-logikalsolutions, the use of any repository past its end-of-life date is at your own risk whether its been moved to "old-releases" or not.

---

### Post by grahammechanical on 2015-09-25
We can still download and install old releases. Best not to tick the box to install updates at the same time as the URLs to the repositories for that release may not be accurate. At some point in time, as stated, the repositories do get moved. That much can be clearly said. And there is another thing to note:

Upgrading from one release to another release is based on the practice of upgrading to the next in line. If we are using an LTS release we can upgrade to the next LTS release. If we are using an Interim release we can upgrade to the next release (Interim or LTS, whatever is next in line). This means that anyone using 15.04 will have to upgrade to 15.10 at some point before they can upgrade to 16.04.

I would not call this method of working horrible. I think it is certainly better than buying an OS that needs a service pack almost from the day it was put on sale.

Regards.

---

