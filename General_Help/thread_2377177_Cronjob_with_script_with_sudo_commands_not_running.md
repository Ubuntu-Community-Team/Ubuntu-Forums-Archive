---
title: "Cronjob with script with sudo commands not running Ubuntu 16.04"
date: 2017-11-10
forum: General Help
---

### Post by steeflemmens on 2017-11-10
[TABLE]
[TR]
[TD="class: postcell"][/TD]
[/TR]
[/TABLE]
I'm trying to get a script with commands that have to be executed as   sudo to run daily using cron. I've installed the cron job using 
  ```
sudo crontab -e

```  but it doesn't seem to execute...
  It's a script that sends me the output of two command on my Plex   server in my email every day. When I run this manually (sudo ~/report.sh   it does work) This is the script:
  ```
#!/bin/bash

touch file.tmp /usr/local/lib/PlexConnect/PlexConnect_daemon.bash
status > file.tmp service plexmediaserver status >> file.tmp 
if [ -s    file.tmp ] 
then
       mailx -s "Plex daily report $(date)" 8901190836@donboscokortrijk.be <file.tmp 
fi 
rm file.tmp

```  This is the line for the cronjob:
  ```
34 15 * * * ~/report.sh

```  When I run the command manually, I receive the email. When I use it in a crontab, nothing... Any ideas?

---

### Post by steeflemmens on 2017-11-10
This was solved on [https://askubuntu.com/questions/974956/cronjob-with-script-with-sudo-commands-not-running-ubuntu-16-04](https://askubuntu.com/questions/974956/cronjob-with-script-with-sudo-commands-not-running-ubuntu-16-04)

---

