---
title: "Get normal file with Terminal"
date: 2006-12-09
forum: General Help
---

### Post by Portable_Jim on 2006-12-09
I want to get a file from the internet (an .iso file) using the terminal - I want it to be downloaded at a time when I am not attending the computer.

(Does anyone know how to make a command to be executed at a certain time)

---

### Post by 23meg on 2006-12-09
You can use cron and wget to do it. Type ```
crontab -e
```and enter ```
wget [http://your-url.net/filename.iso](http://your-url.net/filename.iso)
``` as your command and specify the time when it should be executed. You can learn about the time format [here]("https://help.ubuntu.com/community/CronHowto"), or just create the line using [this]("http://www.clockwatchers.com/cron_tool.html").

---

### Post by Portable_Jim on 2006-12-10
> **23meg said:**
> You can use cron and wget to do it. Type ```
crontab -e
```and enter ```
wget [http://your-url.net/filename.iso](http://your-url.net/filename.iso)
``` as your command and specify the time when it should be executed. You can learn about the time format [here]("https://help.ubuntu.com/community/CronHowto"), or just create the line using [this]("http://www.clockwatchers.com/cron_tool.html").
thanks.

---

