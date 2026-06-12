---
title: "Summary storage usage in 6 months ago"
date: 2018-12-01
forum: General Help
---

### Post by edicande0477 on 2018-12-01
Hi, I'm new in ubuntu user.
currently running ubuntu 10.04 LTS and I want to check the summary storage usage of one directory in 6 months ago.
I like to use the command du -ch --time /var/www/Image/lib/template but it only showed the updated total usage.

Any one can help me with the correct command?


much appreciate for your help in advance.

Thanks.

---

### Post by howefield on 2018-12-01
Thread moved to the "*General Help*" forum.

New to Ubuntu but using 10.04 ?

You probably should move to a currently supported release.

---

### Post by edicande0477 on 2018-12-01
> **howefield said:**
> Thread moved to the "*General Help*" forum.

New to Ubuntu but using 10.04 ?

You probably should move to a currently supported release.

sorry, I mean that I'm new user in ubuntu to support the current old server was running old ubuntu version (10.04 LTS).

---

### Post by edicande0477 on 2018-12-01
anyone please can help and share the solution to me how I can get the summary storage usage in within 6 months? using linux command 
much appreciate for any help from you all. :)

---

### Post by edicande0477 on 2018-12-02
dear all,

finally I use this command: 
find /[COLOR=#000000]val/Image/lib/template[/COLOR] -type f -newermt 2018-06-01 -not -newermt 2018-11-30 -exec du -ch {} + 

then I get the output summary with all file with size and file name within the month period with totally all files size info about 549M.
Is there any alternative or better command for the similar output?

---

