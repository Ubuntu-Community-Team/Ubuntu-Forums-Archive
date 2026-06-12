---
title: "Gnome not available after yesterday update."
date: 2022-12-08
forum: General Help
---

### Post by jrjove on 2022-12-08
After yesterday update I was not able to enter gnome graphic environment with my user.

I have recovered from a timeshift snap, but when I restart the problem happends again....

Any clue?

Regards

---

### Post by ian-weisser on 2022-12-08
"yesterday update" is too vague to offer useful advice, sorry.

Folks are in different timezones; "yesterday" may differ.
Updates differ depending upon your release, the software you have installed, what time of day you checked, phasing, and more.

Review your /var/log/apt/history.log file to see exactly what package actions took place yesterday.
Review your /var/log/apt/term.log for error messages that you may have missed yesterday.

---

### Post by jrjove on 2022-12-11
Not really know what happened, but only my user got corrupted, not the other ones.
I could not fixed it so deleting it, recreating it, and restore a timeshift backup has solved the issue.
Regards,

---

