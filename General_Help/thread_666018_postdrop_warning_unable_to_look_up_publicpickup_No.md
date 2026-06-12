---
title: "postdrop: warning: unable to look up public/pickup: No such file or directory"
date: 2008-01-12
forum: General Help
---

### Post by dsims on 2008-01-12
I continue to run this command:

mailx -s "test email to work" [email]darrellsims2@gmail.com[/email] < ip.txt

And get this following message:


postdrop: warning: unable to look up public/pickup: No such file or directory.

Please Help.

Cheers, D

---

### Post by dcstar on 2008-01-12
> **dsims said:**
> I continue to run this command:

mailx -s "test email to work" [email]darrellsims2@gmail.com[/email] < ip.txt

And get this following message:


postdrop: warning: unable to look up public/pickup: No such file or directory.

Please Help.

Cheers, D

What MTA have you installed?

---

### Post by dsims on 2008-01-12
> **dcstar said:**
> What MTA have you installed?

Im a beginner to all this... What is MTA... and what command do i need to run to get you that info?

---

### Post by dsims on 2008-01-13
i actually used the apt-get install for

mailx and postflx if that is MTA

---

### Post by Permafrost91 on 2008-03-18
having the same problem here ... I'm trying to use postfix to get PHP mail() to send form submissions to a gmail account. The mail() function returns true (which should mean it worked) but the logs tell a different story. /var/log/mail.err shows nothing of interest but /var/log/mail.log shows:

```
Mar 18 17:49:31 localhost postfix/postdrop[13652]: warning: unable to look up public/pickup: No such file or directory
```

After some googling, it turned out that /var/spool/postfix/public/pickup did not exist so I did the following:

```
sudo mkfifo /var/spool/postfix/public/pickup
sudo /etc/init.d/postfix restart
```

That seemed to fix *that* problem. Now postfix complains:

```
Mar 18 18:00:18 localhost postfix/master[13902]: fatal: bind 0.0.0.0 port 25: Address already in use
```

I just got to this point but wanted to share what I've come up with so far. I have never worked with postfix (or any other MTA for that matter) so all of this is Chinese to me. If anyone cares to shed some light into what's going on, that would be great.

(By the way, I tend to tell people to RTFM but the postfix documentation I have come across so far is very non-explanatory to beginners like me so don't hate for asking basic questions).

---

### Post by inphektion on 2008-06-19
I had this same issue with postfix after trying to switch away from sendmail to it.  I uninstalled sendmail and install postfix and ran into this error.  
so after trying this: mkfifo /var/spool/postfix/public/pickup
I then got the same couldn't bind to port 25.
turns out a sendmail was still running:
```
root@server:/etc/postfix# ps aux | grep mail
root     23554  0.0  0.0   8232  1900 ?        Ss   10:17   0:00 sendmail: MTA: accepting connections          
root     27308  0.0  0.0   3004   764 pts/0    S+   10:30   0:00 grep mail
root@server:/etc/postfix# kill 23554
```

Then I restarted postfix and all the mail came in. 

so for those seeing this issue make sure you don't have another mail system running, sendmail, exim, etc.

---

### Post by coffeemist on 2008-06-29
The last suggestion worked great on 8.04-

thanks v much !!

---

