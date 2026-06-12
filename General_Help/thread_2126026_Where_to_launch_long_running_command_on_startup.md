---
title: "Where to launch long running command on startup?"
date: 2013-03-15
forum: General Help
---

### Post by michaelveloz on 2013-03-15
Hi there
I need to launch a python script during system startup, and the script will run "forever". I was thinking about launching it from /etc/rc.local but there's a comment in there saying be sure to end the script with "exit 0".... I'm *assuming* the implication is that some other process is waiting for this script to finish fairly quickly and thus it would be a bad place to launch my script. Is this right?

So the question becomes: how/where to launch this script automatically?

Also, the script writes regularly to stdout, and I need to be able to peek at its output as needed, so it shouldn't be run in some way that it's output is lost. (redirecting it to a file, etc would be okay)

Any ideas would be a great help.
Thanks!
Michael

---

### Post by papibe on 2013-03-15
Hi michaelveloz.

If you only need it when you boot into the desktop, you could use 'Startup Applications' from 'System Settings'.

As a general boot task, you may try using rc.local, but sending it to the background (using a detached screen, nohup or just '&'), although I haven't tried that.

Another general alternative is to create a crontab with the tag '@reboot' so it runs every time the machine starts.

Let us know how it goes.
Regards.

---

### Post by sisco311 on 2013-03-15
rc.local is there only for backward compatibility with the old (SysV style) init process.  think that the file was first used by the BSD style init process[citation needed]. Anyway, Ubuntu uses Upstart now, so I'd probably write an Upstart job to run the script.

Redirecting the stdout and stderr of the script is relatively simple. I'd use two log files, one for stdout and one for stderr:
```
/path/to/script >> /path/to/stdout.log 2>> /path/to/stderr.log
```
but you can redirect both of them to the same file:
```
/path/to/script >> /path/to/log 2>&1
```

Since your script will run `forever' the log file(s) eventually will become too big. You could use logrotate to backup, rotate, remove them...


See:

 [https://help.ubuntu.com/community/UpstartHowto](https://help.ubuntu.com/community/UpstartHowto)

---

