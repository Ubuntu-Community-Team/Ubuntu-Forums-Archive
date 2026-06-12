---
title: "Why didn't my cron job work? Sudo?"
date: 2015-12-16
forum: General Help
---

### Post by morganpatrick on 2015-12-16
Hello,

I have a script in my home directory called zap2xml.sh. It looks like this:

```

#!/bin/sh

cd ../hts/.xmltv
rm tv_grab_file.xmltv
perl zap2xml.pl -u user@domain.com -p [password] -o tv_grab_file.xmltv -e -D
chown hts:hts tv_grab_file.xmltv
service tvheadend restart
```

Now when I run these commands they work fine. However, they all require sudo (except the first line). So, I ran:

```
sudo crontab -e
```

and in there I added 

```
@weekly /home/user/zap2xml.sh
```

I read somewhere, and now I don't remember where, that if I ran crontab as root, then the script will execute as root. It's been in there for a few weeks, though, and it didn't work. So what did I do wrong?

Thanks!

---

### Post by buzzingrobot on 2015-12-17
Yes, "sudo crontab -e" will edit the root user's crontab.  Your script will execute within the root user's environment, not your user's. 

Perhaps, then, it's the "cd ../hts/.xmltv" that causing trouble assuming the hts directory is in your home directory. That relative path does not exist for root unless you've created it. The CD fails.  Try using an absolute path that points explicitly to that file.

---

### Post by morganpatrick on 2015-12-27
Hi, thanks so much for the quick reply. Sorry, I didn't get a notification so I didn't know you responded.

I bet you anything you're right. I will change this path an an absolute one, and report on the results.

Thanks.

---

