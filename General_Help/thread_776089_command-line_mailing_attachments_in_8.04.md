---
title: "command-line mailing attachments in 8.04"
date: 2008-04-30
forum: General Help
---

### Post by Bulldog9908 on 2008-04-30
I just upgraded to 8.04, and am very happy with almost everything.

My one problem is with the loss of the program nail.  I used it to mail files from my computer to myself from an ssh session and to e-mail mp3 files of radio shows I record using a cron job.

```
nail -s "subject" -a "attachment path" xxxxxxx@gmail.com </dev/null
```

What replaces nail?  I have tried Heirloom mailx, but it does not appear to support attachments, and even when I send mail without an attachment, the mail disappears.  Not in /var/spool/mail, not in the recipient mailbox.

So, what program can I use to e-mail files to myself from the command line and a cron job?  Mailx doesn't seem to cut it, and I apparently have it configured incorrectly as nothing is getting out using mailx, even without an attachment.

Thanks in advance

---

### Post by Monicker on 2008-04-30
I've always liked using mutt when it comes to mailing attachments from the console.

---

### Post by Bulldog9908 on 2008-04-30
Thanks.  Mutt looks like it will work.

However, I'm still having the problem I had with mailx.  Under Gutsy Gibon, I could mail attachments out with the simple command line in my first post.

Now, when I do that (this time using mailx or mutt) the message goes nowhere.  It's not being bounced to /var/spool/mail, and it never reaches any recipient.

Where else do I need to look to find out what's still wrong?

---

### Post by Monicker on 2008-04-30
> **Bulldog9908 said:**
> Thanks.  Mutt looks like it will work.

However, I'm still having the problem I had with mailx.  Under Gutsy Gibon, I could mail attachments out with the simple command line in my first post.

Now, when I do that (this time using mailx or mutt) the message goes nowhere.  It's not being bounced to /var/spool/mail, and it never reaches any recipient.

Where else do I need to look to find out what's still wrong?

There should be something in your mail logs.  Which MTA are you using? Sendmail? Postfix?

Depending on your setup, errors will be logged in something like /var/log/mail.log or /var/log/mail.err

You could do a test message with an unusual subject and then "grep -r UnusualSubject /var/log"

---

### Post by Monicker on 2008-04-30
> **Monicker said:**
> There should be something in your mail logs.  Which MTA are you using? Sendmail? Postfix?

Depending on your setup, errors will be logged in something like /var/log/mail.log or /var/log/mail.err

You could do a test message with an unusual subject and then "grep -r UnusualSubject /var/log"

Actually, it would probably be better to grep on the recipient address.  I don't think the subject will appear in the mail logs.

---

### Post by Bulldog9908 on 2008-04-30
Alright, everything is solved. :)

I don't remember what MTA I was using under Gutsy, but there was no  MTA running.  I guess the upgrade got rid of it.  I guess I should have gotten a clue when messages went nowhere (including mail.log and mail.err). :(

Since I'm using Gmail, I searched on mutt and gmail, and got this:
[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)

I now have mutt and procmail setup and can mail directly to my gmail account using mutt to edit and send a message or sending /dev/null to mutt to send without interaction (i.e. from a cron job).

Thanks

---

### Post by andrew.46 on 2008-05-02
Hi:

> **Bulldog9908 said:**
> Alright, everything is solved. :)

[...]
[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)


My heart grows a little warmer every time someone mentions some of my work :-)

               Andrew

---

### Post by lptr on 2008-05-09
Anyone knowing why 'nail' was dropped?

Found here why: [https://launchpad.net/ubuntu/+source/mailx/](https://launchpad.net/ubuntu/+source/mailx/) obviously a temporary debug removal that did not get corrected, yet.

Update (small work around):
Because I recently needed nail/mailx again to automate some mail things from inside a script I did following to get it installed in 8.04 Hardy:

Went to SID archives searching for 'nail' ([http://packages.debian.org/unstable/mail/nail](http://packages.debian.org/unstable/mail/nail)). 
I found, that former nail now is in heirloom-mailx. [http://packages.debian.org/sid/heirloom-mailx](http://packages.debian.org/sid/heirloom-mailx)

Some lines scrolling down I found 'Download heirloom-mailx'
Choosed i386 on the following download page copied one link location and started a console.

> $ wget [http://http.us.debian.org/debian/pool/main/h/heirloom-mailx/heirloom-mailx_12.3-4_i386.deb](http://http.us.debian.org/debian/pool/main/h/heirloom-mailx/heirloom-mailx_12.3-4_i386.deb)
$ sudo dpkg -i heirl*Instead of nail -s blabla... you need to specify mailx -s 'Some headerinfo here' ... but syntax is same as with nail.

enjoy :)

rob*

---

