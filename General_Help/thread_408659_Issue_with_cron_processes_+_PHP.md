---
title: "Issue with cron processes + PHP"
date: 2007-04-13
forum: General Help
---

### Post by Kickboy on 2007-04-13
This has been an issue for a while now, and I've come no closer to a solution.

Here's my problem:
I have my crontab setup to execute a specific PHP script every 30 seconds. I know this seems like a lot, but it is necessary for what I'm doing. The PHP scripts execute perfectly fine. The issue is that randomly the cron process will decide it doesn't want to close. This doesn't happen during every cron process, so I haven't been able to find a specific pattern yet. What it comes down to is that after just a few hours, I'll have dozens of cron processes "Sleeping" and eating up my memory. After a day, there are hundreds. If I don't clean out the processes every day then the server will crash from being overloaded with processes. I provided a screenshot of my System Monitor to show you what this looks like. The only way to close the processes has been to open up System Monitor, select all the cron processes, and slowly kill them all.

Here is a copy of my crontab aswell:
```

* * * * * php -f /www/cron/gather.php; exit;
* * * * * sleep 30; php -f /www/cron/gather.php; exit;

```

Thanks for any help you can provide in trying to resolve this issue.

---

### Post by kidders on 2007-04-13
Hi there,

I have two comments to make (one of which is probably related to the cause of your problem)...

_**Issue 1**_
Launching separate PHP processes every 30 seconds is extraordinarily inefficient, because it subjects your system to the (quite considerable) overhead associated with doing so, eating away at performance by wasting a *huge* amount of CPU time. It is _really_ worth considering ways of daemonising a single PHP process (or at least a smaller number of them) ... it would save your machine an awful lot of memory reallocation, process management & other donkey-work associated with continuously spawning shells, PHP environments, and all the other housekeeping that goes on.

_**Issue 2**_
On a Gentoo box of mine a few months ago, I encountered an issue that looked remarkably similar to yours (judging from your screenshot). I *think* I decided that it was my **sendmail** processes (rather than the **sh**/**php** processes) that were causing the trouble. In my case, it took weeks for things to degenerate to the state you are probably winding up in within hours, but my system basically drowned in open file handles, and got very upset. A periodic **killall sendmail** freed everything up again.

The trouble is that, having thought about it for a while, I simply can't remember how I made the issue go away. :mad: ](*,)

I suppose the first question is whether you think I'm right. (In a way, I hope I'm not, in case I can't remember what to do about it!!)

---

### Post by Kickboy on 2007-04-13
Thanks for your reply...


_**In response to Issue 1**_
I am aware of that. In fact, I researched for a while (mostly in light of this current problem) trying to find another way of doing it. However I haven't found an alternative method that I liked.


_**In response to Issue 2**_
I have suspected for a while the problem was with sendmail, because when I watch the processes unfold I notice sendmail isn't part of the initial process call. It only spawns when the process gets stuck. But I wasn't able to definitively prove that this was the cause.

Your solution of using the 'killall' command is quite useful, and seems to work. But it still leaves dead sh/php processes scattered around, but it does kill it's parent "cron" processes. However, if I add the '-g' switch to the killall command it kills everything. I think I can use this technique to create a shell script to do cleanup for me (which I can then add as a cronjob, heh).

This is a great temporary solution, but I'm still hoping there is a more permanent one.

Thanks for your help.

---

### Post by kidders on 2007-04-14
> **Kickboy said:**
> I notice sendmail isn't part of the initial process call. It only spawns when the process gets stuck.This may be connected to a PHP error. I imagine sendmail is only invoked if cron has something to report (normally an error message or a nonzero exit code, returned by a child). Unfortunately, by killing **sendmail** you lose error messages that (although probably unconnected to your problem) may be worth reading. :-( This was what I remember finding most frustrating!

> **Kickboy said:**
> I think I can use this technique to create a shell script to do cleanup for me (which I can then add as a cronjob, heh).Ha! At least your little problem hasn't driven you past having a sense of humour about it hehe. (Yet.)

This may be a dumb suggestion, but it would be nice to know definitively (somewhat) that the reason your cron jobs are hanging around past their use-by dates isn't because the PHP scripts aren't finishing their work...

Basically, I'm wondering about using lock files to try to track PHP's behaviour. Would it be possible to (temporarily) start your PHP script by **touch**-ing a temporary file (eg /tmp/php-[pid].lock)? You could then finish off by removing the temporary file, and perhaps an explicit call to **exit(0)**. The "normal" behaviour is, of course, completely obvious ... but wouldn't it be interesting if you wound up with some other result.

If nothing odd turns up, it might then be worth changing **php -f /www/cron/gather.php** into **touch /tmp/cron-$$.lock && php -f /www/cron/gather.php && rm /tmp/cron-$$.lock** ... again, just to see if you wind up with any orphan lock files.

Essentially, we know *something's* not terminating normally ... the trouble (at least for _my_ poor brain @ 5 in the morning!) is that there are so many interrelated subprocesses being spawned, it's hard to know what.

Would my suggestion be completely pointless?

---

### Post by Kickboy on 2007-04-14
> **kidders said:**
> This may be connected to a PHP error. I imagine sendmail is only invoked if cron has something to report (normally an error message or a nonzero exit code, returned by a child). Unfortunately, by killing **sendmail** you lose error messages that (although probably unconnected to your problem) may be worth reading. :-( This was what I remember finding most frustrating!

I've looked at the system emails. They aren't sending error messages, instead they are emailing me the outputs of the PHP script (which is odd).

> **kidders said:**
> 
Basically, I'm wondering about using lock files to try to track PHP's behaviour. Would it be possible to (temporarily) start your PHP script by **touch**-ing a temporary file (eg /tmp/php-[pid].lock)? You could then finish off by removing the temporary file, and perhaps an explicit call to **exit(0)**. The "normal" behaviour is, of course, completely obvious ... but wouldn't it be interesting if you wound up with some other result.

If nothing odd turns up, it might then be worth changing **php -f /www/cron/gather.php** into **touch /tmp/cron-$$.lock && php -f /www/cron/gather.php && rm /tmp/cron-$$.lock** ... again, just to see if you wind up with any orphan lock files.

The first thing I tried was adding a 'exit(0)' to the end of my PHP script, which did absolutely nothing. Also, I already have a lock file setup inside the PHP script setup. I use this for a completely different purpose, but I do know the file is being deleted at the end of each run. I also know that each PHP script is executing perfectly fine, because I have the script setup to write it's outputs to a daily log file (again, used for a completely different purpose).

> **kidders said:**
> 
Essentially, we know *something's* not terminating normally ... the trouble (at least for _my_ poor brain @ 5 in the morning!) is that there are so many interrelated subprocesses being spawned, it's hard to know what


That's the problem I've been struggling with. I'm pretty sure it's not the PHP script itself hanging up, which leaves the following possibilities: The PHP CLI is faulty and not returning proper exit codes, the cron process is faulty and not accepting exit codes, the sendmail process is faulty and not returning proper exit codes. The latter begs the question: Why is sendmail spawning in the first place? :confused:

---

### Post by kidders on 2007-04-14
Sorry my last post was no help. :-( You're waaaay ahead of me!

> **Kickboy said:**
> Why is sendmail spawning in the first place?This is normal behaviour for cron. The logic is that output is bad, and when it's not being displayed in a terminal somewhere, some way needs to be found to show it to you. Normally, cron tasks are designed to produce no output other than what you might expect to have redirected to stderr.

Given that, you would imagine that changing **php -f /www/cron/gather.php** to **php -f /www/cron/gather.php &>/dev/null** would make your problem go away. (Naturally, a redirection somewhere more sensible would be in order!) The only problem I have with doing that is that side-stepping an issue and solving it are two different things. Hehe.

Anyhow, if we assume for a moment that **sendmail** is the problem, the first thing that jumps to mind is that it will block until "\n.\n" (or presumably an EOF marker) is fed to it. Assuming all your script executions result in output (and assuming that nothing running between sendmail & PHP is smart enough to escape control characters), I can't help wondering if explicitly outputting "[LF].[LF][EOF]" at the end would make a difference.

... That's lots of "assuming" ... I wonder ... :-k

**Edit:** Incidentally, I'd be happy to let you log in and set up your cron jobs on my box, if that would be any use to you. I'm sure you'd like to know if whatever's going on is peculiar to your computer!

---

### Post by Kickboy on 2007-04-14
> **kidders said:**
> This is normal behaviour for cron. The logic is that output is bad, and when it's not being displayed in a terminal somewhere, some way needs to be found to show it to you. Normally, cron tasks are designed to produce no output other than what you might expect to have redirected to stderr.

Given that, you would imagine that changing **php -f /www/cron/gather.php** to **php -f /www/cron/gather.php &>/dev/null** would make your problem go away. (Naturally, a redirection somewhere more sensible would be in order!) The only problem I have with doing that is that side-stepping an issue and solving it are two different things. Hehe.

I had considered that as well, but I didn't think it would really do much.

> **kidders said:**
> 
Anyhow, if we assume for a moment that **sendmail** is the problem, the first thing that jumps to mind is that it will block until "\n.\n" (or presumably an EOF marker) is fed to it. Assuming all your script executions result in output (and assuming that nothing running between sendmail & PHP is smart enough to escape control characters), I can't help wondering if explicitly outputting "[LF].[LF][EOF]" at the end would make a difference.

... That's lots of "assuming" ... I wonder ... :-k

Possibly. But since I don't have any direct control over the sendmail process, it'll probably ignore any such characters I append to my output.


> **kidders said:**
> 
**Edit:** Incidentally, I'd be happy to let you log in and set up your cron jobs on my box, if that would be any use to you. I'm sure you'd like to know if whatever's going on is peculiar to your computer!

Thanks for the offer, but it would take a lot of work to set this up on another server. The backend uses a rather large MySQL Database (over 50,000 entries across 12 tables).


Thanks for the help you have provided. Though still no direct solution, you have helped quite a bit ;)

---

