---
title: "Restore data : Can Testdisk do something ?"
date: 2018-04-13
forum: General Help
---

### Post by fantasya on 2018-04-13
Hi ! 

My HDD crashed several days ago, and I am desperately trying to have my data back.
I just couldn't access to any folder. I am trying to recover my data using testdisk, but can not figure out if there is still something to do.

This is was I have access to in the beginning 
[ATTACH=CONFIG]279273[/ATTACH]

And the directories I have access to before any search.
[ATTACH=CONFIG]279274[/ATTACH]

I enclosed the report after a deeper search 
[ATTACH=CONFIG]279275[/ATTACH]

Report : 
[ATTACH]279271[/ATTACH]
[ATTACH]279272[/ATTACH]

Do you have any suggestion on what could be done next ? 
Thank you very much !

---

### Post by TheFu on 2018-04-13
Can you not restore to a new disk from the backups?   That would be much easier than testdisk.

If not, there is a data recovery how-to: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
I would start by mirroring the failing disk to a new disk with ddrescue.  That should get all the data back except those in failed sectors.  The new disk should be the same size or larger than the failed disk.

Testdisk and photorec are the last chance for non-professional tools and really quite painful for more than a few files.
Hope that link helps.

---

