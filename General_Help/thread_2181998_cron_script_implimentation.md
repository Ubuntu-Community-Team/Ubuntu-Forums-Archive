---
title: "cron script implimentation"
date: 2013-10-19
forum: General Help
---

### Post by twinturbotom on 2013-10-19
I need my server to email me when my WAN IP changes and what the new address is.  I'm unclear on some of the best practices to implement this.  I've read plenty of Google and forum material and have a decent Idea on how to get everything working (almost fully functional below) but I'm most concerned with the best practices for setting up this sort of thing as I see myself scaling this to other cron jobs and notifications.  

Any insight or direction will be appreciated.  Thank you.


Improvements and direction required:
LOG_FILE is hard coded to /var/log/, is that the proper location?  Should it be tied to an environment variable?
curl command has standard output when executing script but not when typing into the terminal.  Should I redirect this to another log along with other errors?
I'd like the system to send an email notification (from a template file) with my new IP.  
Where should the email template the system will use be located?
How will I pass my script variable to the email template?

Here's a WIP version of my simple script that writes the current IP if it is different than the last line of a log file it outputs to. The script resides in my /etc/cron.hourly/ directory:



```
#!/bin/sh
LOG_FILE="/etc/logs/IPADR.log"
TIME_STAMP=$(date +"%m-%d-%y,%H:%M:%S")

IP_WAN=$(curl -q icanhazip.com)
#echo IP_WAN: $IP_WAN
OLD_IP_WAN=$(tail -n1 $LOG_FILE | sed 's/.*\,//g')
#echo OLD_IP_WAN: $OLD_IP_WAN
if [ $IP_WAN = $OLD_IP_WAN ]
then
        #echo EQUAL
        exit
else
        #echo NOT EQUAL
        echo $TIME_STAMP,$IP_WAN >> $LOG_FILE
        echo $TIME_STAMP, $IP_WAN) | sudo ssmtp -vvv MY_EMAIL_TEMPLATE_WITH_VARIABLE

fi
```


Thank you.

---

