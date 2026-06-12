---
title: "shell script for making automatic package update..."
date: 2007-09-03
forum: General Help
---

### Post by Mia_tech on 2007-09-03
don't know my way around shell scripting too well, is there a way to make apt-get update and apt-get upgrade run automaticly...let's say at least once a week?...if someone could p0int me to the right direction.

---

### Post by capink on 2007-09-03
1. Open your text editor with root privileges using the following command:

```
sudo gedit /etc/cron.weekly/update
```

2. Copy the following text into the text editor and press save
```

#!/bin/bash
sudo apt-get -y update
sudo apt-get -y upgrade
```

3. Make the script executable:

```
sudo chmod a+x /etc/cron.weekly/update
```

---

### Post by seabattle on 2007-09-03
To run both of the commands, you can use

```
 apt-get update && apt-get upgrade 
```

To run the command weekly, it may be worth using crontab, here's a useful guide to using it...

[http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

Hope that helps!

---

### Post by Mia_tech on 2007-09-03
I came up with this using the crontab file to make automatic the virus scan, check for rootkits, and package updates.

```
crontab -E
```

opening crontab in default editor

```

30 1	* * *	root	mkdir /tmp/virus ; clamscan -ri --log=/var/log/clamscan.log --move=/tmp/virus /
30 3	* * *	root	chkrootkit -q
30 5	* * *	root	apt-get -y update && apt-get -y upgrade 

```

clamscan will run everyday at 1:30am
chckrootkit at 3:30am
and apt-get at 5:30am

---

