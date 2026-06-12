---
title: "Cron and/or a mail problem on (x)ubuntu 14.04 LTS"
date: 2015-04-02
forum: General Help
---

### Post by james_r3 on 2015-04-02
Hi All,

Partially fixed mail problem but not fully tested as yet. Updates /additions are in my quick reply below.

I was running 3 archival servers plus other PCs  running 10.04 and 12.04 LTS versions of Xubuntu.

The 10.04 LTS server failed, a  hardware error. So I installed 12.04 on new (but old) hardware. The system worked although not tested fully .I then upgraded to 14.04 in situ.

Started to set-up my standard set of used programmes.
Most programmes worked although I did need to tweak some settings, obviously the inner workings had changed.
 But I could not get Mondorescue to work which I use to do a "bare metal" backup, nor could I get mondorescue to work from cron. I was using the same setup as used on the older versions 10.04 and 12.04.
The Mondorescue problem that they had changed the programme to solve a bug that had appeared because of of lower level  code changes between 12.04 and 14.04. So Sorted out a temporary solution so I could test the rest of the system.

My current root crontab -l
 ```
root@Jake2:~# crontab -l
# Edit this file to introduce tasks to be run by cron.
#
#Jake2 root
# 
#
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For more information see the manual pages of crontab(5) and cron(8)
#
PATH=/root:/bin:/sbin:/usr/bin:/usr/sbin
# 
# m h  dom mon dow   command
01 * * * * ./.rjwrapperw1yorn.sh
01 1 * * 6 ./.rjbackupw1yorn.sh
* * * * * ./.rjnotifyw1.sh

root@Jake2:~# 

```
The last line was added to test out operation  of cron. 
If I run the script manually, I see the result of the running script in an open root terminal window and a notification window appear on the main desktop.
Running from Cron nothing, but I do see a message in my cron log.
```
Apr  2 14:05:06 localhost crontab[19459]: (root) LIST (root)
Apr  2 14:06:01 localhost CRON[19468]: (root) CMD (./.rjnotifyw1.sh)
Apr  2 14:07:01 localhost CRON[19479]: (root) CMD (./.rjnotifyw1.sh)
Apr  2 14:08:01 localhost CRON[19490]: (root) CMD (./.rjnotifyw1.sh)
Apr  2 14:09:01 localhost CRON[19501]: (root) CMD (./.rjnotifyw1.sh)
Apr  2 14:10:01 localhost CRON[19517]: (root) CMD (./.rjnotifyw1.sh)

```

but job does not seem to run .rjnotifyw1.sh nor send mail to my root mailbox

```
root@Jake2:~# cat .rjnotifyw1.sh
#!/bin/bash
export DISPLAY=:0
echo "Hi Welcome"
echo "This is Week 1"
echo $(date)
notify-send "This is Week 1"


```

I also changed the script to split the line "export DISPLAY=:0" as had been suggested in a couple of postings, no change.

Also My mail log showed some errors 

```
pr  2 13:27:02 localhost postfix/pickup[18828]: 027C5A0D8A: uid=0 from=<root>
Apr  2 13:27:02 localhost postfix/cleanup[18946]: 027C5A0D8A: message-id=<20150402172702.027C5A0D8A@Jake2.localdomain>
Apr  2 13:27:02 localhost postfix/qmgr[1476]: 027C5A0D8A: from=<root@Jake2.localdomain>, size=581, nrcpt=1 (queue active)
Apr  2 13:27:02 localhost postfix/local[18948]: error: open database /etc/aliases.db: No such file or directory
Apr  2 13:27:02 localhost postfix/local[18948]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Apr  2 13:27:02 localhost postfix/local[18948]: warning: hash:/etc/aliases is unavailable. open database /etc/aliases.db: No such file or directory
Apr  2 13:27:02 localhost postfix/local[18948]: warning: hash:/etc/aliases: lookup of 'root' failed
Apr  2 13:27:02 localhost postfix/local[18948]: 027C5A0D8A: to=<root@Jake2.localdomain>, orig_to=<root>, relay=local, delay=0.18, delays=0.11/0.01/0/0.06, dsn=4.3.0, status=deferred (alias database unavailable)

```

Normally I do not need to set up the file /etc/alias.

Help would be appreciated in solving this problem, so that that when the time comes I will be able to run 14.04 on my other systems as well. I am currently depending on my 12.04 versions because cron, mail and mondorescue run. They are all necessary for system backups.

Best wishes
Jim R
Running Xubuntu 12.04 various desktops and laptops and running 14.04 unreliably on a netbook and desktop.

---

### Post by james_r3 on 2015-04-02
Hi All,

Further update, I know that I am top posting but, the update messages will seen first.
After more complete testing seems that the mail problem have been solved see another new post for a further addition.
.
My partial fixes for the mail problem, "Google works wonders" but why I could not find the answers before!!

Checked the error message.
> Apr  2 13:27:02 localhost postfix/local[18948]: error: open database /etc/aliases.db: No such file or directory

It was correct there was no file /etc/alias.db whereas there was a file /etc/alias.
Compared the file with the same file on the working file , it was different. I changed root to \root
```
root@Jake2:~# cat /etc/aliases
# See man 5 aliases for format
postmaster:    \root

root@Jake2:~# 

```


Tried to restart postfix no change!!

I found a reference to generating /etc/alias.db

```
root@Jake2:~# newaliases
```

Then restarted postfix.
```
root@Jake2:~# /etc/init.d/postfix reload
 * Reloading Postfix configuration...                                    [ OK ] 
root@Jake2:~
```

Ran mail 
```
root@Jake2:~# mail
"/var/mail/root": 6 messages 6 new
```

Hurray!!! new messages and they made sense.

Best Wishes
Jim R

---

### Post by Habitual on 2015-04-02
Good Job and well done, Jim!

---

### Post by james_r3 on 2015-04-03
Hi Habitual,

Thanks for the encouragement.

Hi All,

After further testing overnight, I found that a further update/addition was needed, to fully solve the problem, Because it seems that the operation of mail had changed. All read mail was moved from /var/mail/root to /root/mbox upon quitting mail

I used mutt to read the root mailbox.

I set up an alias in root to access the mailbox so I do not have to remember the full command.
```
alias rjmutt='mutt -f /root/mbox'

```

Mail wise all seems to work.

It also seems that that cron has started to work properly, not sure why but I did need to change the crontab file by using crontab -e as root  several times in the process of testing to get mail messages from CRON to work properly, perhaps a corrupt file ???. But I will be doing a more complete test overnight of my main usage of CRON and that is run mondorescue automatically. It will not be the full set of mondo scripts that I normally use but an abbreviated  version.

Note my signature change, when I get some time I will try and Identify what is the problem on the netbook.

Best Wishes
Jim R.
Running Xubuntu 12.04 various desktops and laptops and running 14.04 on a a desktop but unreliably on a netbook.

---

