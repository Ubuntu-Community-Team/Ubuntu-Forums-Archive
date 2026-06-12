---
title: "Firefox Unable To Connect After Update"
date: 2013-06-29
forum: General Help
---

### Post by ubu_lin on 2013-06-29
Hello, Today after updating firefox, I am unable to connect any website using firefox. Even tried connecting disabling all add-ons and plugins.

FIrefox version 22.
Ubuntu 12.04 64 Bit

Any help please ? thanks.

---

### Post by carl4926 on 2013-06-29
Try re-naming your hidden .mozilla folder to .mozilla-bak
Start firefox
Is there still a problem?

---

### Post by ubu_lin on 2013-06-29
Hi Carl, It worked. What was the problem ? Thank you for your help. :)

---

### Post by carl4926 on 2013-06-29
Corrupt FF profile I guess

Here is the solution to follow.

Look in the old renamed mozilla folder
Mine is like this: .mozilla/firefox/3vbwf2j7.default/bookmarkbackups
Yours will be different here 3vbwf2j7.default

But find the latest .json file in there and with firefox - Bookmarks manager point to there to import
This will recover your bookmarks etc...

---

### Post by ubu_lin on 2013-06-29
Thank You, I restored my bookmarks in that way. I will close this thread now.

---

### Post by claracc on 2013-06-29
> **ubu_lin said:**
> Thank You, I restored my bookmarks in that way. I will close this thread now.

To close the thread you need to ask it for a moderator.

What you can do, as you have fixed your problem, is to mark the thread as solved in order other people can find information in an easier way.

To mark the thread as solved, you can follow this link:[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

