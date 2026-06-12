---
title: "what is the sync command waiting for?"
date: 2020-01-11
forum: General Help
---

### Post by Skaperen on 2020-01-11
when i run the [COLOR=#0000cd][FONT=courier new]**sync**[/FONT][/COLOR] command in a timed way right after some command that causes a lot of writes to be cached, i can see that it takes some time, like a few seconds or more, depending on how much the previous program did.  if i run [COLOR=#0000cd][FONT=courier new]**sync**[/FONT][/COLOR] a 2nd time the same way, it often takes a little more time (not as much).  i thought it was waiting for all the cached writes to be written.  what is the 2nd sync waiting for?  i have even seen a 3rd [COLOR=#0000cd][FONT=courier new]**sync**[/FONT][/COLOR] wait a little bit (much less than the first two) in extreme cases. can anyone explain this?  what event wakes it up each time?

---

