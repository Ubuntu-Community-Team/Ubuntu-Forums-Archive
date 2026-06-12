---
title: "Ubuntu keeps saying Successful su for me, why? I thought it used sudo."
date: 2007-04-05
forum: General Help
---

### Post by My_Forums_Username on 2007-04-05
I keep getting these weird sayings in auth.log about Successful su.  Does not Ubuntu use sudo.  Below is a snippet of auth.log with my id replaced by username.

Apr  4 19:39:52 ubuntu su[8416]: Successful su for username by root
Apr  4 19:39:52 ubuntu su[8416]: + ??? root:username
Apr  4 19:39:52 ubuntu su[8416]: (pam_unix) session opened for user username by (uid=0)
Apr  4 19:39:52 ubuntu su[8416]: (pam_unix) session closed for user username
Apr  4 19:43:28 ubuntu su[8695]: Successful su for username by root
Apr  4 19:43:28 ubuntu su[8695]: + ??? root:username
Apr  4 19:43:28 ubuntu su[8695]: (pam_unix) session opened for user username by (uid=0)
Apr  4 19:43:28 ubuntu su[8695]: (pam_unix) session closed for user username
Apr  4 20:17:01 ubuntu CRON[10771]: (pam_unix) session opened for user root by (uid=0)
Apr  4 20:17:01 ubuntu CRON[10771]: (pam_unix) session closed for user root
Apr  4 21:17:01 ubuntu CRON[12891]: (pam_unix) session opened for user root by (uid=0)
Apr  4 21:17:01 ubuntu CRON[12891]: (pam_unix) session closed for user root
Apr  4 22:17:01 ubuntu CRON[15320]: (pam_unix) session opened for user root by (uid=0)
Apr  4 22:17:01 ubuntu CRON[15320]: (pam_unix) session closed for user root

---

