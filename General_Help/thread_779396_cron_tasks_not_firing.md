---
title: "cron tasks not firing"
date: 2008-05-02
forum: General Help
---

### Post by chris.olsen on 2008-05-02
I have to do some backing up of some files. To ensure I knew what I was doing I created a simple example:

$ crontab -l
01 * * * * touch /Users/chris/foo

(As you can see it is in the cron file)

The crappy thing is the above script doesn't work. The touch command with the args works fine from the command line, but nothing happens on the minute.

Any clues to where I went wrong with this simple test?

Thanks.

---

### Post by Oldsoldier2003 on 2008-05-02
> **chris.olsen said:**
> I have to do some backing up of some files. To ensure I knew what I was doing I created a simple example:

$ crontab -l
01 * * * * touch /Users/chris/foo

(As you can see it is in the cron file)

The crappy thing is the above script doesn't work. The touch command with the args works fine from the command line, but nothing happens on the minute.

Any clues to where I went wrong with this simple test?

Thanks.
cron often needs the full path, which would be /usr/bin/touch

```
01 * * * * /usr/bin/touch /Users/chris/foo
```
BTW that command will run touch at 1 minute past the our every hour so its not ideal for a test

here is a simple cron tutorial

[http://ubuntujourney.wordpress.com/2008/03/26/cronjobs-for-dummies-command-line-edition/](http://ubuntujourney.wordpress.com/2008/03/26/cronjobs-for-dummies-command-line-edition/)

---

### Post by Monicker on 2008-05-02
Check your local workstation email account. Cron sends an email with any output from a cron job, so if there was an error it would be there.

---

### Post by chris.olsen on 2008-05-02
:) Thanks

It was the 01.  I clued out and thought that meant every minute.

The * * * * * touch /Users/chris/foo works fine.

Thanks again.

---

### Post by Oldsoldier2003 on 2008-05-03
> **chris.olsen said:**
> :) Thanks

It was the 01.  I clued out and thought that meant every minute.

The * * * * * touch /Users/chris/foo works fine.

Thanks again.

No worries, I'm glad you got it sorted.  The reason I mentioned that you should sue the full path in cronjobs is occasionally you'll run into an environment issue so the extra couple seconds it takes to put in the full path never hurts :)

---

