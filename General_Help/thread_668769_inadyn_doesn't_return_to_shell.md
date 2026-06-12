---
title: "inadyn doesn't return to shell"
date: 2008-01-15
forum: General Help
---

### Post by fizban9 on 2008-01-15
I'm trying to write a script that will check my current IP and, if my IP address has changed, update my dyndns.com account.  I've gotten everything working except one part. 

When it gets to the command that updates my dyndns account, it updates the account but doesn't return to the shell, so the script I wrote freezes and I have to crtl+c out of it.  I want to cron this script so I can't have it hanging like that.

The line the is giving me the problem is that one that starts with "inadyn"

```
#Load previous IP address
OLD_IP=`cat IP.old`
#Load current IP address
NEW_IP=`lynx --dump ipswift.com | grep "Your IP" | awk {'print $3'}`

#Compare old IP address against new IP address
if [ $OLD_IP != $NEW_IP ]; then
        inadyn -u xxxxxxxxx -p xxxxxxxxx -a redmage.doesntexist.com
        echo $NEW_IP > IP.old
fi

```

---

