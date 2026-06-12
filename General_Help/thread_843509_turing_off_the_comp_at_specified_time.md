---
title: "turing off the comp at specified time"
date: 2008-06-28
forum: General Help
---

### Post by charanpreethu on 2008-06-28
hi... how can i make my computer to turn off by itself at given time....

---

### Post by ajgreeny on 2008-06-28
You will need to write a simple bash script and make it executable without a password, which I have forgotten how to do.  Others will be able to tell you that, or you may find it on google.

The script will be:-

```
#!/bin/bash
sudo shutdown -h now
```Whether you will still need the **sudo** at the start if it is a "no password" script, I'm not sure; again others will know, I'm sure.  This script will then need to be run using cron.

---

### Post by nick_h on 2008-06-28
No need for a script.  Use the *shutdown* command but specify the time required instead of *now*.

For the manual page type:
```
man shutdown
```

Example:
```
sudo shutdown -h 20:00
```

and you can cancel it with:
```
sudo shutdown -c
```

---

### Post by prshah on 2008-06-28
> **charanpreethu said:**
> hi... how can i make my computer to turn off by itself at given time....

Create a small script file in "/root" with the following commands:```

sudo gedit /root/stop.sh
```

In that script file, add a single line of code```
/sbin/shutdown -P now
```

Save and quit. Now give the commands ```
sudo chmod +x /root/stop.sh
sudo crontab -e
``` That edits **root's** crontab, so any jobs that are run though this run with root privileges.

To the end of the (newly) opened crontab file (don't disturb _any_ existing entries) add a line as below (assuming a shutdown at 11:30pm)```

30 23 * * * /root/stop.sh
```

And if you want a more complex condition (eg) shutdown at 11:30 Pm on every _weekday_ but ignore weekends```

30 23 * * 1-5 /root/stop.sh
```

```
crontab -l | head -1
``` will explain the various columns above.

---

### Post by ajgreeny on 2008-06-28
Thanks nick-h, I forgot that you could issue a specific time for the shutdown rather than the simple now.  You can also do a "+m" instead of the now, where "m" is the number of minutes after issuing the command.

---

