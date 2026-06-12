---
title: "Spamassassin headers in Evolution"
date: 2007-04-05
forum: General Help
---

### Post by Chris Johnson on 2007-04-05
I've got spamassassin installed and working with Evolution. It isn't currently attaching X-Spam-#### headers (#### = Status, Flag, Level, Score etc.), and I'd like to know how to get it to do so, in order to see how I might tweak the filter settings.

I've currently got the line 
```
add_header all Status _YESNO_, score=_SCORE_ required=_REQD_ tests=_TESTS_
```

in my ~/.spamassassin/user_prefs and /etc/spamassassin/local.cf (I'm not sure which one might be being used), but this isn't working.

Does anyone have any ideas?

Cheers

---

