---
title: "is powernap still around?"
date: 2022-12-30
forum: General Help
---

### Post by dlbrewe on 2022-12-30
Hello
I am back w/ essentially the same situation I've encountered before:
I have a couple of desktops that i would like to automatically suspend when nobody is logged in. Also a couple of headless servers that i'd like to suspend on a schedule. I have used powernap for a long time, as recently as w/ 18.04. However I recently upgraded to 20.04 and powernap appears to be obsoleted and removed from the standard repositories.  I'd appreciate any suggestions about accomplishing what i need to do.

Edit: 
It dawned on me that i think I can adequately control the servers using cron and rtcwake. With the desktops, I guess I need a simple way to detect if any users are logged in, so that is a corollary question.

---

### Post by MAFoElffen on 2022-12-31
I see 'powernap' list in focal (20.04) but diving deeper, I don't see it further than 18.04(???)

On checking for logged in users...
```

#!/bin bash

logged_in=$(w | grep -v 'average\|LOGIN@' | awk '{print $1}') ## Check for logged in users, return UserName

if [ -z $logged_in ]
then
  echo "No one is logged in"
  #systemctl suspend   ##hibernate 
  rtcwake -m disk -s 900   ## Hibernate to disk and wake up in 15 minutes...
else
  echo "Users are logged in"
fi

```
The problem would be to power back on via command line... Using rtcwake, you could wake up in 15 minutes, then check for activity again (cron running this scipt)

---

### Post by zeke2135 on 2022-12-31
Thanks for the ideas! I'm not sure I follow the details but I came up with a simple solution that seems to work well enough for me. 

logins=$(users) 

if [ "$logins" = "" ]; then
   systemctl suspend
fi

I run this script at intervals from /etc/crontab. So far it seems to work well enough.

Thanks again. (BTW somehow I have two ubuntu forums accounts and logged in to the other one to post this question.

---

