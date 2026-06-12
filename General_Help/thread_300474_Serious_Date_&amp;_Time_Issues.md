---
title: "Serious Date &amp; Time Issues"
date: 2006-11-15
forum: General Help
---

### Post by 3dmaker on 2006-11-15
Hello guys, I use Ubuntu 6.06 on all of my computers, I love it, but there is one problem.
Date & Time just does not work! I set the correct time zone America/Los-Angeles, GMT -8:00
So its 4:00 here, but my clock shows that its 12:00 AM
Why is this?
And if I right click the thing and click Adjust Date & Time, it opens the "Bug Buddy - Bug Reporting Tool"

Very useful.

How do I fix this?

---

### Post by bollix47 on 2006-11-15
See if anything [here]("http://ubuntuforums.org/showpost.php?p=1730934&postcount=5") helps.

---

### Post by bollix47 on 2006-11-15
Here's another [one]("http://ubuntuforums.org/showpost.php?p=1605219&postcount=5") to try.

---

### Post by 3dmaker on 2006-11-15
No sorry, none of those work...

---

### Post by bollix47 on 2006-11-16
One thing you could try is right-click on the date and time and select preferences.  Make sure there is no checkmark in the UTC box.  Then go to system-administration-time and date and set the correct time for your timezone.

This probably won't fix the bug problem but may fix your time issue.

Out of curiosity did you try changing your timezone to America/Vancouver?

---

### Post by 3dmaker on 2006-11-16
Changing the UTC fixed it, I tried changing it to Australia, but that still doesn't fix anything... the bug buddy still opens. I tried a new installation of 6.10, it worked fine, but after I updated the system, I could not adjust the date & time

---

### Post by bollix47 on 2006-11-16
Glad to hear you at least got the time corrected.

When I went to System - Administration - Language and changed from English/US to English/Canada the bug buddy disappeared for me.

Also, check System - Administration - Time and Date and make sure the Keep clock sync.... is not checked.

---

