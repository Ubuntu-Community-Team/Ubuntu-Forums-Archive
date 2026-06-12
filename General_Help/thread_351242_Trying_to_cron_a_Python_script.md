---
title: "Trying to cron a Python script"
date: 2007-02-01
forum: General Help
---

### Post by diamond on 2007-02-01
I have a little Python script I've written and I want it to run every 10 minutes. From what I've read, I gather that the following line in my crontab should work:

```

*/10 * * * * "/usr/bin/python /usr/bin/myscript.py" >/dev/null 2>&1

```

But it doesn't. Any idea what I might be doing wrong? I know that the paths are right, and the script itself works fine when I run it manually.

---

### Post by WW on 2007-02-01
I don't know why you have those double-quotes in there. Try taking them out.

---

### Post by diamond on 2007-02-01
> **WW said:**
> I don't know why you have those double-quotes in there. Try taking them out.

OK, I changed that and it still doesn't work. Any other ideas?

---

### Post by WW on 2007-02-01
If you are putting your command in /etc/crontab, your line is missing the "user" field.  If the user should be root, for example, try this line:
> */10 * * * * root /usr/bin/python /usr/bin/myscript.py >/dev/null 2>&1

---

### Post by diamond on 2007-02-01
> **WW said:**
> If you are putting your command in /etc/crontab, your line is missing the "user" field.

I'm not. I created this by editing my user-level crontab, using the "crontab -e" command.

---

### Post by WW on 2007-02-01
OK, I'm stumped.  I just put this in my user-level crontab
```
*/2 * * * * /usr/bin/python -c "print 'Hello, world.'" > /tmp/junk
```
and the file /tmp/junk was overwritten every two minutes.

---

### Post by diamond on 2007-02-01
> **WW said:**
> OK, I'm stumped.  I just put this in my user-level crontab
```
*/2 * * * * /usr/bin/python -c "print 'Hello, world.'" > /tmp/junk
```
and the file /tmp/junk was overwritten every two minutes.

Hmm. Weird.

Could this have something to do with cron.allow and cron.deny files? I have them both in /etc; cron.deny is empty, and cron.allow has my username in it.

---

### Post by diamond on 2007-02-01
> **WW said:**
> OK, I'm stumped.  I just put this in my user-level crontab
```
*/2 * * * * /usr/bin/python -c "print 'Hello, world.'" > /tmp/junk
```
and the file /tmp/junk was overwritten every two minutes.

I just tried that, and it worked for me too. But my script won't work, even though it works fine from the command line.

This is very bizarre.

---

### Post by RAOF on 2007-02-01
> **diamond said:**
> I just tried that, and it worked for me too. But my script won't work, even though it works fine from the command line.

This is very bizarre.

You're probably assuming some sort of environment for your script, then.  Cron jobs get run in a new shell, one with pretty much no environment set.  If we could see the script, we may be able to spot the problem.

Alternatively, you could try piping the stdout & stderr of your script somewhere other than /dev/null, to see what it's complaining about :).

---

