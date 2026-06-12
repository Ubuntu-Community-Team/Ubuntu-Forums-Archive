---
title: "Cron not working"
date: 2006-12-08
forum: General Help
---

### Post by ryland22 on 2006-12-08
I cannot get cron to work.  Here is a detailed list of everything I have done and checked.  Please let me know if anyone can help.

1. I am running Ubuntu 6.06 LTS
2. I setup cron by running the following command:
sudo crontab -e

3. I have a cron file with the following script:

# m h  dom mon dow   command
*/2 * * * * /usr/bin/firefox >> /var/www/apache2-default/mjt_cron/log

When I run /usr/bin/firefox from command line it opens a firefox browser.  Thus, my crontab should openup firefox every 2 minutes, and log any problems to the file I have in var: /var/www/apache2-default/mjt_cron/log.

However, firefox never opens and no errors are logged to my log file. 

4. I also tried to set this up without using sudo, and still got nothing.
5. Each time I ran crontab -l to make sure the crontab was installed.
6. I checked to make sure that crond was running by using the following command: ps -ef.  Here is the line confirming cron is running:  

root      4802     1  0 20:02 ?        00:00:00 /usr/sbin/cron

At this point I am entirely out of ideas, and don't know what else to do.  Can anyone point me in the right direction?

---

### Post by ryland22 on 2006-12-08
Ok, so I found a thread here on ubuntu forums and it solved the problem.  here is the answer:

*/2 * *  * *  export DISPLAY=:0 && /usr/lib/firefox/firefox

works like a charm!

---

