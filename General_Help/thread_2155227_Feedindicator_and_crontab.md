---
title: "Feedindicator and crontab"
date: 2013-06-17
forum: General Help
---

### Post by zoozd on 2013-06-17
Hello,

For some reason, Feedindicator stops working after a while, and becomes unresponsive. All the menu buttons become useless, and I have to kill python and run feedindicator again.

I have tried adding 0 * * * * pkill python, 1 * * * * feedindicator to crontab. However, it just kills it, and doesn't run it back again. I am wondering why this is happening. Running "feedindicator" in terminal is enough to run it, without any sudo.

---

### Post by Cheesehead on 2013-06-17
Cron does not run in your terminal window - it runs in it's own environment.
So feedindicator may be crashing immediately because it doesn't know which display to attach to.

Try passing a $DISPLAY environment variable. Er, depending upon your setup, the $DISPLAY variable may be different each time you login...

```
$ printenv | grep DISPLAY
DISPLAY=:0
```

So the crontab would be
```
1 * * * * export DISPLAY=:0 && /path/to/feedindicator
```

---

### Post by zoozd on 2013-06-18
Thank you, but this didn't work :(

DISPLAY was 0

I tried adding
1 * * * * export DISPLAY=:0 && /home/zed/FeedIndicator/feedindicator

And it didn't work.

---

### Post by Cheesehead on 2013-06-18
That's the same path as the executable you run in terminal?

You can also use STDOUT and STDERR redirection on cron jobs to capture error messages.

For example, this will send error messages to a tempfile.
```
1 * * * * export DISPLAY=:0 && /home/zed/FeedIndicator/feedindicator 2> /tmp/feedindicator_errors
```

---

### Post by zoozd on 2013-06-18
The error file states

No protocol specified
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/home/zed/FeedIndicator/feedindicator", line 52, in <module>
    from configobj import ConfigObj
ImportError: No module named configobj

---

### Post by Cheesehead on 2013-06-18
That would be two critical problems, all right.
You realize that those are problems with your script, not cron, right?
Do you understand the error messages?
Do you understand what to do about them?

---

### Post by zoozd on 2013-06-19
Well it isn't my script. It is out there on the internet, and it works on if ran on Terminal.
I will be looking at the script to see if there is something to do about it.

Thank you!

---

