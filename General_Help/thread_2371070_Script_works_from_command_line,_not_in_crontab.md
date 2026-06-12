---
title: "Script works from command line, not in crontab"
date: 2017-09-10
forum: General Help
---

### Post by jrmymllr on 2017-09-10
I have an entry in crontab that runs a script every night to do cloud backups.  The script is basically functioning, but the problem is the output redirection to a file isn't.  The pertinent lines are:


echo "********************start sync at $(date)********************" >> /tmp/synclog.txt
/usr/sbin/rclone sync --transfers=3 --old-sync-method --bwlimit "05:00,400K 22:00,700K" -v /NetworkShare/backup/ B2: &>/tmp/synctemp


The first line is working and results in that text being written to synclog.txt.  The second line is executing and doing its thing, but synctemp has no content as a result.  If I run this line from the command prompt, it works perfectly.  I've found some mentions of using "[COLOR=#000000][FONT=verdana]2>&1" instead, and I tried replacing "&>" with that, but no change.  I'm sure this is simple but I've yet been able to get it working.[/FONT][/COLOR]

---

### Post by HermanAB on 2017-09-10
The cron environment is very limited.  You have to use the full path name of all programs and files in your cron scripts.

---

### Post by sisco311 on 2017-09-10
&> is bashism use the posix syntax :
```
command > filename 2>&1
```

---

### Post by steeldriver on 2017-09-10
Where exactly did you put the 2>&1?

AFAIK cron uses /bin/sh, so what you read is correct since &> is a "bashism" - however the placement of the redirections is important:

```

/usr/sbin/rclone sync --transfers=3 --old-sync-method --bwlimit  "05:00,400K 22:00,700K" -v /NetworkShare/backup/ B2: [COLOR=#0000ff]**>**[/COLOR]/tmp/synctemp [COLOR=#0000ff]**2>&1**[/COLOR]

```

---

### Post by jrmymllr on 2017-09-10
2>&1 in the right place did it!  Thanks!

---

