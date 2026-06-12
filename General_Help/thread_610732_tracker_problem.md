---
title: "tracker problem"
date: 2007-11-12
forum: General Help
---

### Post by migo2011 on 2007-11-12
Hallo,

I have a strange problem with the tracker search tool.
It finds categories and displays the number of results found but the results are not shown in the search result area.
I attach a screenshot to make clear what I mean.

Has anyone an idea why this happens?
Info:
I had disabled the tracker in the sessions config (and activated it again) and i also switched off indexing for a while.

thx for any help,
migo

---

### Post by nonducor on 2007-11-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/148520](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/148520) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I was suffering from the same problem. I found a solution in this bug entry:

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/148520](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/148520)


After correcting the overlap and issuing trackerd --reindex, it seens to be working (at least now tracker-stats shows a lot of files :-) )

---

