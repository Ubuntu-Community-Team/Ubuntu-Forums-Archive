---
title: "Knotify"
date: 2007-02-15
forum: General Help
---

### Post by CheeseQueen452 on 2007-02-15
I was running Digikam, & suddenly Knotify launched. Is it safe to "kill the process" in the system monitor? Do I even need Knotify running for anything in particular?

---

### Post by louis_nichols on 2007-02-15
knotify is just an error reporting daemon. it tells you that some process failed (related to digikam or not). i think it's safe to kill it, but that won't solve the reason of the error you get. it just keeps it hidden. it is a good idea to see what the error is and troubleshoot that.

---

### Post by CheeseQueen452 on 2007-02-15
Well, I never saw any error message or anything. It's just running silently in the background. If I kill the process, will it launch again if there's a problem?

> **louis_nichols said:**
> knotify is just an error reporting daemon. it tells you that some process failed (related to digikam or not). i think it's safe to kill it, but that won't solve the reason of the error you get. it just keeps it hidden. it is a good idea to see what the error is and troubleshoot that.

---

### Post by louis_nichols on 2007-02-15
hm... I must admit I don't know. In my case, knotify shows up in case of errors, but it doesn't run all the time. Then again, I use gnome and only a couple kde apps, so I can't be certain.

I think it is called by every kde app when it needs to report an error, so you can't really prevent it from running.

---

