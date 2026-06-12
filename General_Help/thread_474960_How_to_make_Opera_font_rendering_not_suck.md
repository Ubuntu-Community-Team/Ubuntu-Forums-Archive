---
title: "How to make Opera font rendering not suck"
date: 2007-06-15
forum: General Help
---

### Post by Dynaflow on 2007-06-15
I'm not sure if this fix has been posted here before, but the issue has come up as a general complaint about Opera (my favorite web browser) in other threads here, and no one has seemed to have a solution for it.  Now that I've stumbled upon the solution at the Opera forums, I just thought I'd share it with y'all.

The problem has been that certain fonts used by certain websites show up looking somewhat pixelated or granular-looking, unlike the smooth fonts other browsers will display for the same text.  See the top headlines in the screenshot below to see what the problem looks like.

The problem seems to be that core X fonts are enabled in Linux Opera by default, and the solution is as easy as disabling them through [opera:config#UserPrefs|EnableCoreXFonts]("opera:config#UserPrefs|EnableCoreXFonts") (the "Save" button is at the very bottom of the page).  Restart Opera, and you're good to go.

The thread on the problem is here: [http://my.opera.com/community/forums/topic.dml?id=185329]("http://my.opera.com/community/forums/topic.dml?id=185329").

---

