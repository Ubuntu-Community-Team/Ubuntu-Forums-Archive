---
title: "&quot;System Program Problem Detected&quot; Warning -- after running Clamtk"
date: 2016-03-29
forum: General Help
---

### Post by Shobuz99 on 2016-03-29
HELP.
I've seen 2 or 3 posts regarding this, but no solutions as pertains ClamTK.

Full disclosure: I ran Clamtk with the search for PUA's checked, because
I was searching Twitter landed on a Twitter account that had porn. I was concerned that malware or PUA's
may have been deposited while I was there. I know I'm a very bad man.... <sigh> :(

After I ran ClamTK it found 22 PUA's and sited 3 or 4 of them as "trojan" related.
I deleted all but 2 of them. Those two resided in /usr/share/mime/ and /usr/lib/Ruby.
I tried repeatedly to delete these or quarantine these two files, *to no avail.*
So, I exited all and restarted the machine. I'm using 14.04.3 Trusty Tahr and ClamTK 5.09 (out of date but it won't auto update)
When the machine arrived at the desktop, I got the error message above, twice.
Rerunning ClamTK made no difference, except that it detected the same two mime-cache PUA's.
I still couldn't delete or quarantine these two issues.
I uninstalled ClamTK, and rebooted; but the "System Program Problem Detected" warning still comes up at boot/start.
I have looked in dmesg and the Freshclam logs; but can't find anything that appears to be the reason.
I have attached two PNG images if they will help. I can also attach the logs here if you need them.
If something is broken, I want to fix it. I just don't know what the steps are, at this point.
Thank you for your help..
Shobuz99

---

### Post by Shobuz99 on 2016-03-31
Update: I have solved this myself. I found the proper way to remove this error message:
( More of an explanation: [http://www.binarytides.com/ubuntu-fix-system-program-problem-error/](http://www.binarytides.com/ubuntu-fix-system-program-problem-error/) )

Go to Terminal and then the folder /var/crash
```
 cd /var/crash  
 ls
 sudo rm /var/crash/* 
```

I shouldn't have requested help for this so quickly. Instead I should've done more research.
But now this may help someone else.

Thank you Ubuntu!

Shobuz99

---

