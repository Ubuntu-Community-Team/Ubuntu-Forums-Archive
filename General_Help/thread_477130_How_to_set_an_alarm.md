---
title: "How to set an alarm?"
date: 2007-06-18
forum: General Help
---

### Post by herbster on 2007-06-18
How would I set an alarm to go off at a specific time?

Being able to play a song in Amarok at say 1:00pm or something. I was thinking of cron but I have no clue how to get it to play a song in Amarok or an alarm sound otherwise.

EDIT: Figured it out, using similar command that gets my OO files running every night:

```
32 02 * * *     export DISPLAY=:0 && amarok -p
```

That will play the current playlist, and just add the file path after "-p" to get it to play whichever song.

---

