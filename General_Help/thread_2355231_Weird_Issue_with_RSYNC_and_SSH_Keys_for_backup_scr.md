---
title: "Weird Issue with RSYNC and SSH Keys for backup script"
date: 2017-03-10
forum: General Help
---

### Post by jameswinteborn on 2017-03-10
ello! 


First, thanks for clicking on this thread and considering stuff :) We have a large script that handles backups for 30+ servers. The system that the backup server is trying to rsync with is a server that takes files from multiple other servers and stores them in sep folders with different owners. Its a jailed SCP environment.


Anyways, I got this error on one of the directories after running my script and can't figure out a good way to deal with it: 


2017-03-09 02:34:06,594 - root - INFO - Command:  '/usr/bin/rsync','-akh','--rsh=ssh -c arcfour -F /root/.ssh/dbconfig','--delete','--stats','--timeout=7200','--bwlimit=2500000','shen-prod@bck3a.domain.com:~/first/incoming/ ~/second/incoming/','/usr/local/shen/backups/shen-prod/res/2017-03-09'
2017-03-09 02:34:06,771 - root - WARNING - Permission denied, please try again.
2017-03-09 02:34:06,772 - root - WARNING - Permission denied, please try again.
2017-03-09 02:34:06,773 - root - WARNING - Permission denied (publickey,password).
2017-03-09 02:34:06,773 - root - WARNING - rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
2017-03-09 02:34:06,774 - root - INFO - added /usr/local/domain/backups/shen-prod/res/2017-03-09 to the progress file
2017-03-09 02:34:06,775 - root - WARNING - rsync error: unexplained error (code 255) at io.c(605) [Receiver=3.0.9]


So what makes this kindof weird for me is that the same script is able to properly sync a different folder on the same system. Example: above it is failing on /usr/local/shen/backups/shen-prod/res/2017-03-09. When the next part of the script runs, it will properly sync /usr/local/corn/backups/corn-prod/res/2017-03-09 on the same server. Both parts of the script are referencing the same SSH key file on the same server but it won't work for shen-prod.


I cannot remove everything from the hosts files and try to start over since there are so many systems using this script constantly throughout the day. Should I just send another ssh-copy-id to the server that is tryign to get backed up? I don't want to break the other backups that are working with that key. 


Let me know what you guys think on this. Im getting to the point where im over-thinking everything and kindof freezing up. Thanks in advance for your consideration!

---

