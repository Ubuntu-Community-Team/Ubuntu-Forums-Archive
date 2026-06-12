---
title: "cron running my crontab as root"
date: 2006-10-10
forum: General Help
---

### Post by lozenge on 2006-10-10
And I don't want it to! For some reason root can't attach to dcop, which is the command I want to run through cron, but it runs my crontab as root.

How can I fix this?

---

### Post by mssever on 2006-10-10
If you edit crontab with ```
crontab -e #or more explicitly
crontab -eu youruser
``` then cron will run those jobs as your user. To access root's crontab, type ```
sudo crontab -eu root
```

---

### Post by jimbren on 2006-10-10
Are you using 
```
crontab -e
```

or 

```
sudo crontab -e
```?

To create cronjobs for yourself, you don't need to use sudo.

---

### Post by lozenge on 2006-10-10
I'm just using crontab -e, crontab -eu james yields the same file, etc.

They still run as root for some reason. I don't know why but dcop doesn't work when logged in as root, and dcop isn't working, so logically, the only conclusion I can come to is that since the daemon is running as root, the crontab is too.

I've no idea why it's doing it. :(

---

### Post by mssever on 2006-10-10
Are you sure that the job is running as root and that you're not experiencing a different problem?

Put the following command in your crontab:
```
/usr/bin/id > /home/james/cron_test
```After the job runs, look at the file and see who it ran as. Also, check the owner of the file (remove it before re-testing). If it shows that root owns that file, then your cron is weird indeed. Every cron I've ever used executes jobs as the user who owns the crontab. I think that you've got a completely different problem--probably with DCOP.

---

### Post by lozenge on 2006-10-11
It runs as me. I've got it executing a script that has dcop instructions in it, here are the contents.

```
james@monkey:~$ cat .alarm
#!/bin/sh
dcop amarok player play
```

But I get nothing. Maybe it is dcop, but dcop works perfectly when I run the exact same command in a terminal.

And here is my crontab:

```
james@monkey:~$ crontab -l
#m     h     dom     mon     dow    command
*      *     *       *       *      exec /home/james/.alarm
```

---

### Post by mssever on 2006-10-11
If it runs as you, there are only two things that I can think of: either DCOP is messed up, or some environment variable isn't getting passed. If you do env > /home/james/env.cron and run a diff against env > ~/env.shell executed from a shell, you might learn something.

Also, as I said earlier, I'm not a KDE user, but I wonder if dcop is even necessary. amarok player play started amarok for me. It didn't auto-play, but then I don't think that I've ever told amarok where to find music files. When I tried it with dcop, it complained about being unable to attach to a server--probably because KDE isn't running. What does DCOP provide of importance?

---

