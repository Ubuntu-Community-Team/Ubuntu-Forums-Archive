---
title: "Where can I find the full syntax for incrontab?"
date: 2018-08-05
forum: General Help
---

### Post by Paddy Landau on 2018-08-05
The manual for [incrontab]("https://linux.die.net/man/5/incrontab") ([FONT=lucida console]man[/FONT] 5 [FONT=lucida console]incrontab[/FONT]) gives its syntax.

But the document doesn't mention, for example, that [FONT=lucida console]incrontab[/FONT] may have comments and blank lines, or that whitespace must be exactly one space &#8212; tabs or multiple spaces mess things up.

Do you know where can I find the full syntax for [FONT=lucida console]incrontab[/FONT], including comments, whitespace restrictions, and any other quirks that it might have?

**EDIT**: I've found that incrontab also messes up comments when it saves!

**EDIT**: I've found that any comments in the file prevent successful running. So, my guess is that [FONT=&quot]incrontab[/FONT] can't have comments at all.

---

### Post by TheFu on 2018-08-05
If the local manpage, not the manpage on the web, is incorrect, you should submit a bug report to the project.  [http://inotify.aiken.cz/?section=incron&page=about](http://inotify.aiken.cz/?section=incron&page=about)  seems to be the project website.

Always use the local manpage, since it is matched to the same version of the program you have installed locally.

---

### Post by Paddy Landau on 2018-08-05
Thank you, @TheFu. I shall have to report this.

Also, I suppose, report incrontab for messing around with the file!

---

### Post by Paddy Landau on 2018-08-06
After some experimentation, I see that there's more to it than meets the eye — it's a bit buggy. I've [reported the bugs]("https://bugs.launchpad.net/ubuntu/+source/incron/+bug/1785573").

---

### Post by TheFu on 2018-08-06
> **Paddy Landau said:**
> After some experimentation, I see that there's more to it than meets the eye — it's a bit buggy. I've [reported the bugs]("https://bugs.launchpad.net/ubuntu/+source/incron/+bug/1785573").

Launchpad is for Ubuntu. Is this only an Ubuntu issue or does it happen on Fedora, Debian, Slackware, Arch ...  distros?  The project bug system is the fastest way to get things fixed, then you can open a bug with canonical to get the new package added to their supported releases, I would think.

BTW, I'd never heard of incron before this thread.

---

### Post by Paddy Landau on 2018-08-06
> **TheFu said:**
> Is this only an Ubuntu issue…?
Sorry, I don't know!
> **TheFu said:**
> BTW, I'd never heard of incron before this thread.
It's a useful tool!

---

