---
title: "Ubuntu 20.04 after recent updates on startup get: System Program Problem Detected"
date: 2021-04-07
forum: General Help
---

### Post by wiz70 on 2021-04-07
[SIZE=4]After a little research I found the problem to be: [COLOR=#000000]usr libexec gnome-session-binary.121.crash

Any idea on how to solve this problem?[/COLOR][/SIZE]

---

### Post by Xian on 2021-04-09
If you want to dig-in to the root cause you can try searching Google for the error notice. 

Or you can just remove the old crashes and notifications until some package misbehaves again.

$ sudo rm /var/crash/*

---

### Post by wiz70 on 2021-04-10
I did a search prior to this post and didn't find any resolution.  So, I'll give the ' [COLOR=#000000]$ sudo rm /var/crash/* ' a try.  Thanks...  But would really like to know the root cause of this error....[/COLOR]

---

### Post by CatKiller on 2021-04-10
> **wiz70 said:**
> But would really like to know the root cause of this error.
Well, that depends. And seeing if deleting the crash reports helps will be indicative.

The mechanism is that when something crashes, it dumps the crash report. Then, some time later, the contents of that directory will be checked, the upload offered, and a new file will be created when the upload is successful. Sometimes programs will crash over and over, and you're given the option of suppressing the crash notifications; sometimes the system doesn't notice that you've already uploaded the crash report (or the upload fails for some reason) and so you get asked to upload the same crash report over and over, even though you haven't had any more crashes.

If deleting the crash reports stops the issue, you know that it was a problem with the crash reporting mechanism. If you get more crash reports after that, then you know that something is actually crashing.

---

### Post by wiz70 on 2021-04-11
"[COLOR=#000000]sometimes the system doesn't notice that you've already uploaded the crash report"

That seems to be the problem..  I uploaded the crashed report after the 1st time it appeared and repeated that numerous times after that.  Now, it doesn't appear after booting up.

Thanks and appreciate the help....

BTW,  I can't find a way to mark this thread solved.....[/COLOR]

---

### Post by tea for one on 2021-04-11
> **wiz70 said:**
> "[COLOR=#000000]BTW,  I can't find a way to mark this thread solved.....[/COLOR]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

