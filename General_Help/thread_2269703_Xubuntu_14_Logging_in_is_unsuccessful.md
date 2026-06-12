---
title: "Xubuntu 14 Logging in is unsuccessful"
date: 2015-03-17
forum: General Help
---

### Post by a.h.lohmann on 2015-03-17
Xubuntu 14.04 LTS

I logged out with save session option ticked. The things that were open included Gparted - I think this is the problem.

When I try to log in the screen looks almost like the normal screen but without tool-bar and icons. There are no warnings or messages  but I suspect that the problem is that Gparted should at this point have been launched and would be expecting me to authenticate but no such dialogue box is shown.

So I think I need to log in without starting up the things that were running in the last running session? Please would you suggest a solution?

---

### Post by Toz on 2015-03-17
Try clearing out your saved sessions cache before logging in by deleting the ~/.cache/sessions folder.

---

### Post by a.h.lohmann on 2015-03-18
Thanks for the suggestion Toz - I did not try that but;

I tried again this morning and after a wait the desktop started normally but without the previous session restarted. In future I think I shall avoid save session option.

The issue can be considered closed. Thank you.

---

### Post by slickymaster on 2015-03-18
> **a.h.lohmann said:**
> Thanks for the suggestion Toz - I did not try that but;

I tried again this morning and after a wait the desktop started normally but without the previous session restarted. In future I think I shall avoid save session option.

The issue can be considered closed. Thank you.
Being so, please mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

