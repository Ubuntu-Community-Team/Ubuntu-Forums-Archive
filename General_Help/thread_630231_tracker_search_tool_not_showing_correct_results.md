---
title: "tracker search tool not showing correct results"
date: 2007-12-03
forum: General Help
---

### Post by mailbinoy on 2007-12-03
I have a large hard drive and I love tracker. My problem is with tracker-search-tool not showing the results as expected
I get the results as expected when I use
~$ tracker-search "templates unreal" | wc -l
512

I have attached a screen shot of tracker-search-tool with the above query. Notice it says 690 files but shows only one file. 
I also noticed this
~$ tracker-search -d "templates unreal" | wc -l
1
I think i might be able to fix this by reindexing, but that might takes days. I just wanted to check with the community first.
Some other info that might be helpful

:~$ tracker-stats 

-------fetching index stats---------

default : 0 
Files : 393646 
Folders : 24901 
Documents : 40031 
Images : 137674 
Music : 4277 
Videos : 2835 
Text : 25384 
Development : 22328 
Other : 136216 
Emails : 0 
EvolutionEmails : 0 
ThunderbirdEmails : 0 
KMailEmails : 0 
EmailAttachments : 0 
EvolutionAttachments : 0 
KMailAttachments : 0 
Conversations : 827 
GaimConversations : 827 
Applications : 308 
------------------------------------

:~$ tracker-status
Tracker daemon's status is Idle.

---

### Post by satkata on 2007-12-13
I'd rather install the new version of tracker. It helped me out with my issues.
I would suggest reindexing anyway  or just delete 

/home/username/.cache/tracker
/home/username/.config/tracker
/home/username/.local/share/tracker

since I had misspelled option names in the config file and let it index all from the beginning.

It's worth it.

---

### Post by vladu on 2008-07-07
Same problem here, with Ubuntu 8.04
Tried to re index but no luck.

I've now switched to Beagle and I'm very pleased. It doesn't seem to slow my machine, like some people complain (I use the latest version which is not available in the repositories and that might also be a factor when considering speed)

---

### Post by eldragon on 2008-07-07
i have the same problem, it doenst display the correct results with certain searches.

---

