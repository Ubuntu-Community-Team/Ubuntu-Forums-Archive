---
title: "Cron Jobs not Running"
date: 2008-03-11
forum: General Help
---

### Post by sgardne on 2008-03-11
Hi,

Yesterday morning at 0915, cron stopped running jobs. I don't think I did anything to my crontab file yesterday that would have caused the error. The server's been rebooted twice since then. Out of desperation, I deleted everything out of the crontab file and added just this line:

```

*/1 * * * * root /bin/echo "crontab is running" >> /home/sgardne/cron.test

```

This should append the string to the file every minute, but it is not happening. "ps aux | grep cron" results in:

```

root      8083  0.1  0.0   3548  1028 ?        Ss   13:29   0:00 /usr/sbin/cron
sgardne   8094  0.0  0.0   2976   752 pts/0    R+   13:29   0:00 grep cron

```

Any help is greatly appreciated. This has been extremely frustrating for me.

---

### Post by Oldsoldier2003 on 2008-03-11
> **sgardne said:**
> Hi,

Yesterday morning at 0915, cron stopped running jobs. I don't think I did anything to my crontab file yesterday that would have caused the error. The server's been rebooted twice since then. Out of desperation, I deleted everything out of the crontab file and added just this line:

```

*/1 * * * * [COLOR="Red"]root[/COLOR] /bin/echo "crontab is running" >> /home/sgardne/cron.test

```

This should append the string to the file every minute, but it is not happening. "ps aux | grep cron" results in:

```

root      8083  0.1  0.0   3548  1028 ?        Ss   13:29   0:00 /usr/sbin/cron
sgardne   8094  0.0  0.0   2976   752 pts/0    R+   13:29   0:00 grep cron

```

Any help is greatly appreciated. This has been extremely frustrating for me.

```

sudo crontab -l
``` to see roots crontab listing

also the word root shouldn't be in the crontab

---

### Post by sgardne on 2008-03-11
```
$ sudo crontab -l
# m h  dom mon dow   command

*/1 * * * * root /bin/echo "crontab is running" >> /home/sgardne/cron.test
```

---

### Post by sgardne on 2008-03-11
Taking out the word "root" seems to have fixed that line. Now to add my jobs back in one at a time to see which one is breaking it. 

Thanks.

---

### Post by Oldsoldier2003 on 2008-03-11
edit: should have waited for a response  :)

---

### Post by sgardne on 2008-03-11
I think we've got it all sorted out now. Thanks again!

---

