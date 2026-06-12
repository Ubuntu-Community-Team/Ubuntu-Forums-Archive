---
title: "Cronjob not running dist-upgrade"
date: 2015-08-31
forum: General Help
---

### Post by zoidberg2 on 2015-08-31
I have added this entry to the etc/crontab  file
```
###Monday Update
0 10 * * 1 root /usr/bin/apt-get dist-upgrade -q -y >> /var/log/apt/myupgradesmonday.log 

```

When I open the  /var/log/apt/myupgradesmonday.log a few minutes after the update is scheduled to run I get this output, 
```
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be upgraded:
  bash-completion firefox
2 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

I assumed that the update has run but it hasn't as if I type in apt-get dist-upgrade only a minute after the cronjob was executed I get the exact same prompt & it asks me to click y to install (which I do). 


What am I overlooking?


*******Fix 
I found this resolved the issue for me 

> ###Test Thursday Update
# m h  dom mon dow      command
36 22 *    *   3        root /usr/bin/apt-get update && /usr/bin/apt-get -y dist-upgrade

---

### Post by QDR06VV9 on 2015-08-31
Not what you were after I know But, If automatic update and upgrade(&dist-upgrade) is what you are after.
This one works great for me at least. And for a few Friends testing it that are complete Noobs to linux.
[http://forums.linuxmint.com/viewtopic.php?f=42&t=190241](http://forums.linuxmint.com/viewtopic.php?f=42&t=190241)
You will need a working connection at the time your DE boots, The only reason I say that is I have mine configured to use a vpn at start.
Pretty straight forward.
You also see a text file that will show you what was updated or upgraded (See Attachment)
Regards

---

