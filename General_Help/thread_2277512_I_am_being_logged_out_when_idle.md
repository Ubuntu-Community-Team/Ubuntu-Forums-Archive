---
title: "I am being logged out when idle"
date: 2015-05-09
forum: General Help
---

### Post by luvshines on 2015-05-09
Ubuntu 14.04 on Thinkpad T420
Acting weird since last week. If I leave laptop idle for long(I haven't checked the duration), I find that I am logged out of the system.
First I thought that it's just screen lock, but when I entered the password all the apps were closed, work lost etc.

Haven't seen this before.
Any ideas/suggestions ?

---

### Post by ian-weisser on 2015-05-09
> **luvshines said:**
>  but when I entered the password all the apps were closed, work lost etc.

Seems like a possible X Server crash.
Look in /var/crash for .crash files.
Look in /var/syslog for crash or error log.
Look in /var/Xorg.0.log for clues

---

### Post by luvshines on 2015-05-10
There is an xorg crash file in /var/crash but is a week older.
Will it help debug this ?
What should I look for ? Should I share it here ?

---

### Post by ian-weisser on 2015-05-10
Generally, you upload the crash file to Launchpad as part of the bug report.

Ubuntu's apport application, if enabled, automaticaly offers to do this for you when it detects a new .crash file "An error has occurred. Send report?"
If not enabled, you can start apport using the 'apport-cli' command, and it should figure out the crash report on it's own.
A .crash report usually contains all the debug information needed for a developer to identify and fix the bug. No further action by the reporter is needed.

Another suggestion: I would look through /var/log/apt/history.log and /var/log/apt/term.log around the time that the problem appeared.
Did you install anything new? Did anything get updated?

---

### Post by luvshines on 2015-05-11
> **ian-weisser said:**
> Did you install anything new? Did anything get updated?

I happened again today. I found _usr_bin_compiz.1000.crash file.

I was having an issue with compiz recently which I reported here [http://ubuntuforums.org/showthread.php?t=2269986](http://ubuntuforums.org/showthread.php?t=2269986)
I was eventually resolved by deleting this file [B]~/.config/dconf/user
[/B]
Mostly after that I am having this issue

---

### Post by ian-weisser on 2015-05-11
The .crash file should tell you, deep within it's labyrinthine content, why compiz is crashing.
It might be due to the change you previously made...but it might not.

---

### Post by luvshines on 2015-08-05
** BUMP **

This issue is still nagging me :(

I leave the system unattended for long and I return to see the login screen.
I login, thinking that maybe the screen is just locked. But everything is gone, all apps closed and my work is lost

Any ideas how to proceed ?

---

### Post by Vladlenin5000 on 2015-08-05
> The .crash file should tell you, deep within it's labyrinthine content, why compiz is crashing.

This should give you an idea.

---

### Post by luvshines on 2015-08-07
> **Vladlenin5000 said:**
> This should give you an idea.
In most of my cases, there is no .crash file so I am unable to debug it

---

