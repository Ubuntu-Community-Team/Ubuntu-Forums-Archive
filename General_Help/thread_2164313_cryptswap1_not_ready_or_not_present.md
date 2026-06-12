---
title: "cryptswap1 not ready or not present"
date: 2013-07-31
forum: General Help
---

### Post by rbscairns on 2013-07-31
I recently had need to reinstall Ubuntu 12.04, this time encrypting my hard disk. Since then, before the login screen appears, I get the following message:

> The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present.
Continue to wait or Press S to stop mounting or M for manual recovery.


If I wait, the log-in screen appears and I log in as normal.

If I press S, there is a wait and then the log-in screen appears and I log in as normal.

If I press M, there is a wait and then the log-in screen appears and I log in as normal.

This happens every time I start my computer.

Any ideas on what all this means?

---

### Post by Dave_L on 2013-07-31
I often got that message on 12.04.  I found an article about it that said it was a timing issue.  I would wait for the message to go away, which only took a few seconds, and the swap partition got mounted properly, so it seemed harmless.

After booting, you can check whether the swap is mounted correctly:
```
$ swapon -s
Filename				Type		Size	Used	Priority
/dev/mapper/cryptswap1                  partition	2096444	603520	-1
```

---

### Post by rbscairns on 2013-07-31
I think you might be right. After logging in, I am getting:
```
$ swapon -s
Filename				Type		Size	Used	Priority
/dev/mapper/cryptswap1                  partition	1038332	9280	-1
```
I will do some more research and see if I can make the message not appear.

---

### Post by rbscairns on 2013-07-31
Here is what I did to stop the message appearing:

Using ```
sudo gedit /etc/fstab
``` I changed the line```
/dev/mapper/cryptswap1 none swap sw 0 0
```to read ```
/dev/mapper/cryptswap1 none swap sw,noauto 0 0
```
I then used ```
sudo gedit /etc/rc.local
``` and immediately before ```
exit 0
``` added these two lines:
```
sleep 5
swapon /dev/mapper/cryptswap1
```

Upon re-booting, I do not get the message and swapon -s returns:
```
$ swapon -s
Filename				Type		Size	Used	Priority
/dev/mapper/cryptswap1                  partition	1038332	0	-1
```
Everything is looking good (I think).

---

### Post by Dave_L on 2013-07-31
Thanks for posting your solution.  I may try it in 12.04, since I noticed that I still get the warning message.

---

### Post by frupito on 2013-08-29
I use Xubuntu Raring Ringtail 13.04 and I got the same message
> [I]The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present.
Continue to wait or Press S to stop mounting or M for manual recovery.[/I] 
The swap seems to be mounted correctly:
> ~$ swapon -s
Filename				             Type		Size	        Used	        Priority
/dev/mapper/cryptswap1                  partition	1023996	68     	-1

Do you think I can fix the problem like you did?
Thanks

---

