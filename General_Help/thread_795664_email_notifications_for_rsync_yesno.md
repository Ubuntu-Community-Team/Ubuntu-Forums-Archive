---
title: "email notifications for rsync?? yes/no"
date: 2008-05-15
forum: General Help
---

### Post by jcup on 2008-05-15
I am in the midst of discovering what rsync can do... awesome technology...

I'm to the point where I have a test run going right, after a long days work, everything seems to be working smoothly...

I have been searchin the internet and forum posts here to find out how I can set up email notifications once the job is done.

I would like for my computer to email me the results like success/failure and possibly all the details if it fails.

Is that something I can specify in the cron job, or in the rsync script... 

I'm still a little new at this, but not really a noob either, so technical talk or general help would be great...

So, if anyone knows how to do this, I would be really very appreciative...

THANKS!!

---

### Post by jcup on 2008-05-16
bump!

anybody?

---

### Post by koenn on 2008-05-16
what you want is to collect all output of rsync, and mail it. 
you're going to need a command line mail program. Try mailx or nullmailer.

you could probably do something like

```
OUT=$(tempfile) ; 
rsync /srv /dest >$OUT 2>&1 ; 
mailx me@maildomain.xx < $OUT ;
```
check rsync -v option to get the desired level of verbosity.
the ; separator allws you to put all of the above in 1 line.

There's probably a more elegant way of doing this, eg by piping rsync output directly to mailx, but I'm not sure that would always work - you might not get error msgs through the pipe. 
The command would look something like
```
rsync /src /dest | mailx me@domain...
```
or maybe 
```
rsync /src /dest 2>&1 | mailx me@domain...
```

---

### Post by jcup on 2008-05-16
Thanks I will give that I try when i get back to work on monday....

I appreciate it!!!

---

