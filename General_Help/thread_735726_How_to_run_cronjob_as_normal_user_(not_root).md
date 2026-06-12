---
title: "How to run cronjob as normal user (not root)?"
date: 2008-03-25
forum: General Help
---

### Post by se2131 on 2008-03-25
I found a couple of threads that were somewhat related, but none of them solved the problem, hence I'm starting a fresh one.

Basically I have a script that updates my laptop's IP address to a secure location that I can access from any internet-enabled computer.

If I run the script as /home/[myname]/bin/ipupdate, as a normal user, it works fine.

If I run it as root, it fails with errors **"Permission denied (publickey,password,keyboard-interactive)."** and **"Couldn't read packet: Connection reset by peer"** That's fine with me, I'd rather not run it as root. The error is related to SSH keys, not sure how to fix that, but would rather not anyway.

OK, so here's the problem, as my normal user (not root), I type in 
```
crontab -e
```

and here are the contents of my crontab file:

```

# m h  dom mon dow   command
0 * * * * /home/[myname]/bin/ipupdate

```

Basically I want it to run the script every hour. But unfortunately, it doesn't work. After some time, I installed a mail program to check for errors, and here's the output from the 'mail' program:

```

[myname]@[mycomputer]:/var/mail$ mail
Mail version 8.1.2 01/15/2001.  Type ? for help.
"/var/mail/[myname]": 1 message 1 new
>N  1 root@[mycomputer]      Tue Mar 25 22:06   22/792   Cron <[myname]@[mycomputer]> /home/[myname]/bin/ipupdate
& 
Message 1:
From [myname]@[mycomputer] Tue Mar 25 22:06:03 2008
Envelope-to: [myname]@[mycomputer]
Delivery-date: Tue, 25 Mar 2008 22:06:03 -0500
From: root@[mycomputer] (Cron Daemon)
To: [myname]@[mycomputer]
Subject: Cron <[myname]@[mycomputer]> /home/[myname]/bin/ipupdate
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/[myname]>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=[myname]>
Date: Tue, 25 Mar 2008 22:06:03 -0500

[B]Permission denied (publickey,password,keyboard-interactive).
Couldn't read packet: Connection reset by peer
[/B]
```

Notice that the errors at the end are the same as the errors I encounter if I run the program as root, so I'm fairly certain that the cronjob is being run as a root user (even though I did not edit the cron file as root, and if I type in "sudo crontab -l", I get a different crontab than the one I pasted in earlier in this post).

Any ideas on how I can get cron to run as a normal user?

---

### Post by ibuclaw on 2008-03-25
I'm not the best person when it comes to cronjobs. But here's my attempt.

My default state crontab files looks like this:
```

17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```

Which kinda speaks for itself.
But just incase you can't figure it out, first thing I'd do is locate my script somewhere safe.
then add this to your /etc/crontab file

```
 
00 *    * * *   **yourname**    cd / && run-parts --report **/path/to/script**

```
As I said, I'm not that big on cronjobs, but I think this will do.

Hope this helps
Regards
Iain

---

### Post by se2131 on 2008-03-26
Here's what my /etc/crontab file looks like now:

```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
14 *    * * *   [myname] cd / && run-parts --report /home/[myname]/bin/ip
#

```

I moved the ipupdate script into a folder called "ip", but it still fails and when I check the mail errors, it shows a similar message to the one that I pasted in in the first post (except it replaced the command with the new one). So it's still running as root for some reason

---

### Post by Oldsoldier2003 on 2008-03-26
> **se2131 said:**
> Here's what my /etc/crontab file looks like now:

```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
14 *    * * *   [myname] cd / && run-parts --report /home/[myname]/bin/ip
#

```

I moved the ipupdate script into a folder called "ip", but it still fails and when I check the mail errors, it shows a similar message to the one that I pasted in in the first post (except it replaced the command with the new one). So it's still running as root for some reason

what is the script? the script itself may be causing the failure.

---

### Post by se2131 on 2008-03-26
ipupdate script:
```

#!/bin/bash
#Updates IP addres to a text file, and uploads it to the server

lynx -dump www.whatismyip.com | grep ' Is ' > /home/myname/currentip.txt
sftp -b /home/myname/bin/sftpbatch.bat  username@server
rm /home/myname/currentip.txt

```

the ipupdate script calls sftp which runs a batch file:

```

put /home/myname/currentip.txt /home/.../web/private/
bye

```


I should note that all of this used to work somehow (edgy, feisty, gutsy, but now I'm on hardy heron beta), but I can't for the life of me remember whether I ran the cronjob as root or as a normal user. I highly doubt it's some kind of bug that's in hardy and not gutsy, I'm pretty sure it's more likely that the root account used to work well w/ the SSH certificates (so I don't need to type in a password), but I've been messing around w/ SSH and am new to it, so I was hoping to get this to work by simply running it under my own login and not as root.

See [http://ubuntuforums.org/showthread.php?t=346711&highlight=sftp+upload](http://ubuntuforums.org/showthread.php?t=346711&highlight=sftp+upload) for what I'm talking about concerning SSH certificates

---

### Post by Oldsoldier2003 on 2008-03-26
> **se2131 said:**
> ipupdate script:
```

#!/bin/bash
#Updates IP addres to a text file, and uploads it to the server

lynx -dump www.whatismyip.com | grep ' Is ' > /home/myname/currentip.txt
sftp -b /home/myname/bin/sftpbatch.bat  username@server
rm /home/myname/currentip.txt

```

the ipupdate script calls sftp which runs a batch file:

```

put /home/myname/currentip.txt /home/.../web/private/
bye

```


I should note that all of this used to work somehow (edgy, feisty, gutsy, but now I'm on hardy heron beta), but I can't for the life of me remember whether I ran the cronjob as root or as a normal user. I highly doubt it's some kind of bug that's in hardy and not gutsy, I'm pretty sure it's more likely that the root account used to work well w/ the SSH certificates (so I don't need to type in a password), but I've been messing around w/ SSH and am new to it, so I was hoping to get this to work by simply running it under my own login and not as root.

See [http://ubuntuforums.org/showthread.php?t=346711&highlight=sftp+upload](http://ubuntuforums.org/showthread.php?t=346711&highlight=sftp+upload) for what I'm talking about concerning SSH certificates

well from the error messages it seems you are not passing your credentials when you connect. thats the direction i would take the troubleshooting. I think you are on the right track...

---

