---
title: "cron problems"
date: 2008-05-22
forum: General Help
---

### Post by SatNav on 2008-05-22
Hi,

as the title suggests, I'm having some trouble with cron. In that it doesn't seem to be working. To clarify..

- I have verified that cron is, in fact running, using 'ps -el | grep cron'

- I have checked the last used time of both '/etc/init.d/cron' and '/etc/crontab', and they are consistent with when i last restarted my box.

- I have also restarted the cron daemon (a number of times in fact).

But for some reason, tasks do not seem to be running. my crontab currently looks like this:
```
#
* * * * *       deluge

```
(I chose deluge for debugging, simply because it is a gui app - better suggestions are welcomed)

Oddly, when i check '/var/log/messages' i get lines like this:
```
May 22 20:42:02 pegasus kernel: [333259.339689] deluge[10606]: segfault at 968 rip 7f5fa440901c rsp 7fffb12abc80 error 4
May 22 20:43:02 pegasus kernel: [333319.346735] deluge[10640]: segfault at 968 rip 7f983bd5a01c rsp 7fff48bfb5d0 error 4
```
Again, the timing is consistent, i just dont get what's happening. And I only get these messages when the task is deluge, anything else gives *nothing*.

Please help, this is driving me up the wall!

Many Thanks,
Mark

---

### Post by latna on 2008-05-22
Don't do it with a gui app. I'm don't think cron has access to to your X session and therefore can't run a gui program. Try this instead:

```
* * * * *       touch /home/user/testfile
```

Replace /home/user with a directory that cron can write to and check if testfile is there after cron had run.

---

### Post by euux on 2008-05-24
> **latna said:**
> Don't do it with a gui app. I'm don't think cron has access to to your X session and therefore can't run a gui program. Try this instead:

```
* * * * *       touch /home/user/testfile
```

Replace /home/user with a directory that cron can write to and check if testfile is there after cron had run.

Just found that, yes you can run an gui-app with cron, with a very good explanation on this forum's thread [http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

I've already put qbittorrent to work via cron.

---

