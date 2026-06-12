---
title: "cron frustrations..."
date: 2013-08-14
forum: General Help
---

### Post by Dave / Mosaic on 2013-08-14
So I'm trying to get a small shell script to run as root every few minutes with cron, and there's something I'm just not getting - seems like it should be easy, but I can't make it work.  Here's where I'm at so far:

Using "sudo bash" to log in as root, and then running "crontab -e", I add this line after the few other things that are already there (and running correctly by the way):

[INDENT][FONT=Courier New]*/60 * * * * root /var/www/vhosts/mosaicengineering.com/crontestadd.sh
[/FONT]
[/INDENT]

There's a newline, or maybe two, after this line...

(BTW, I've tried this both with and without the "root" field; doesn't seem to work for me either way.)

Here's what's in the directory where the "crontestadd.sh" script lives, with how I have permissions set:

[INDENT][FONT=Courier New]root@mosaicengineering:/var/www/vhosts/mosaicengineering.com# ls -la
... (extra stuff omitted...) ...
drwxr-xr-x  5 root     root         4096 Aug 13 23:34 .
drwxr-xr-x  4 root     root         4096 Aug 10  2011 ..
-rw-rw-rw-  1 root     root          215 Aug 14 00:03 crontest.log
-rwxr-xr-x  1 root     root           72 Aug 13 23:48 crontestadd.sh
[/FONT]
[/INDENT]

Here's what "crontestadd.sh" has in it:

[INDENT][FONT=Courier New]root@mosaicengineering:/var/www/vhosts/mosaicengineering.com# more crontestadd.sh
#!/bin/bash
date >> /var/www/vhosts/mosaicengineering.com/crontest.log
[/FONT]
[/INDENT]

crontest.log has just a couple of lines of text in it.

I can run "crontestadd.sh" manually from a shell, and it appends the current date onto the end of crontest.log, as I expect.

I believe I have all the permissions right, all full pathnames specified, etc.

But cron isn't running this script - or if it is, it isn't appending anything to crontest.log...  I believe the "*/60" should be making it run once every minute, but no - nothing!

Any ideas??  I've searched around, but not coming up with the clue I need...

THANKS!

--dave

---

### Post by alarme on 2013-08-14
Maybe */60 is out of range.  Range for minutes is from 0 to 59

*/1 runs fine (every minute).  If you intend to run every hour, try some like  * */1 * * * /your/script/here

---

### Post by ian-weisser on 2013-08-14
Couple issues here.

1) */60 is not valid syntax. Use * for once each minute.

2) Use full paths in your crontab **and in your script**. For example: /bin/date

3) If you use 'sudo crontab', you don't specify root within it. Doing so is invalid syntax, and the job will fail.

You seem to be mixing up the crontabs. 
Crontabs in the /etc/cron* tree need to specify if they are user or root crontabs, and don't use the 'crontab' command
Crontabs in /var/spool/cron don't specify user/root, and do require the 'crontab' command

Users should use the 'crontab' command, and keep crontabs in /var/spool/cron.
Root is already set up to use the /etc/cron* tree. Your system's many cron and anacron jobs are in there.
Root can also use /var/spool/cron and the 'crontab' command.

4) Permissions. A script run as root will output as root. That means you won't be able to read the output without sudo. Does your script really need to be root?

```

# Example user crontab, using the 'crontab' command
* * * * * /bin/date >> /tmp/testfile
* * * * * /bin/sh /home/me/script.sh

# Example root crontab, using the 'sudo crontab' command
* * * * * /bin/date >> /tmp/testfile     # Yes, it's exactly the same as above, does not specify root
* * * * * /bin/sh /home/me/script.sh

# Example root crontab, placed in /etc/cron.d
* * * * * root /bin/date >> /tmp/testfile    # Extra field that specifies root or user.
* * * * * root /bin/sh /home/me/script.sh
```


Two tips for successful cron jobs:
- Document your cron job thoroughly. Six months from now, you may not remember why you wrote it that way.
- Use links so you can find cron jobs and scripts and configs again that may be scattered across /etc or /var.

---

### Post by Habitual on 2013-08-14
I'd like to recommend the [Crontab Sandbox]("http://www.dataphyx.com/cronsandbox/cronsandboxgui.php")

---

### Post by Dave / Mosaic on 2013-08-14
Excellent - well for me the main thing was my misunderstanding of the */n syntax; things are working now and I can run my real and more complex script every ten or twenty minutes or whatever.  The deeper information is also much appreciated - especially about the different crontabs, and the sandbox tool...

Mainly though, thanks for the quick reply to my original post from basically the wee hours of the morning here; the great community support available here is one of the main reasons I'm running Ubuntu on my servers.

regards--

--dc

---

