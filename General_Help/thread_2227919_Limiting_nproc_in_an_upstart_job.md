---
title: "Limiting nproc in an upstart job"
date: 2014-06-04
forum: General Help
---

### Post by Kevin_Schmid on 2014-06-04
[COLOR=#000000][FONT=Arial]What exactly does the stanza
[/FONT][/COLOR]
[FONT=courier new][COLOR=#000000]limit nproc 20 20
[/COLOR]
[/FONT][COLOR=#000000][FONT=Arial]in an Upstart job do?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I've read the documentation here ([http://upstart.ubuntu.com/wiki/Stanzas#limit](http://upstart.ubuntu.com/wiki/Stanzas#limit)), and it seems like it would limit nproc for any process related to the job. However, I don't see this effect when I've added this to my job's conf file - in this specific case, I've confirmed that my test job's single process was able to fork more than 20 child processes. Any advice?

Thanks![/FONT][/COLOR]

---

