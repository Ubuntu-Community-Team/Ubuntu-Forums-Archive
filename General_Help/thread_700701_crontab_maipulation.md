---
title: "crontab maipulation"
date: 2008-02-18
forum: General Help
---

### Post by itzpapalotl on 2008-02-18
can somebody tell my WHY I can't directly edit a user's crontab in /var/spool/cron/crontabs/username.

I am working on a bell system for my school, which has several schedules depending on various factors. While it would be possible to program the whole show in to a single and ridiculous crontab file. It would be MUCH simpler to be able to SWAP crontab files. That way I could program say a holiday schedule and swap that in to the crontab during the holidays.

I have a script. I need to know
1) Is it going to work? (no I think is the answer here)
2) Why not? (or maybe this isn;t as important)
3) is there ANY other way to do this? I Do NOT want to create separate users for the different schedules.

Here's the script:

#! /bin/bash


# ye olde' crontab swapping thingy
#
#
#First do some Janitorial stuff
# like check that there IS an argument


if [ $# = 0 ];
then
echo '##########' >> /usr/bin/bellsys/log
date >> /usr/bin/bellsys/log
echo 'script failed: no argument supplied' >> /usr/bin/bellsys/log
echo 'script failed. syntax is: ./swapchron filename'
exit 1
fi

# and then check to see that argument is valid

if [ -f /usr/bin/bellsys/schedules/$1 ];
then
echo '##########' >> /usr/bin/bellsys/log
date >> /usr/bin/bellsys/log
echo "All tests passed, initiating script" >> /usr/bin/bellsys/log
else
echo '##########' >> /usr/bin/bellsys/log
echo 'Script Failed: Bad argument supplied' >> /usr/bin/bellsys/log
echo 'script failed: Bad file name, or no such schedule. Check spelling perhaps?'
exit 1
fi

######## If all of that checks out #############

###### 1) STOP the cron deamon
/etc/init.d/cron stop
echo 'cron deamon stopped' >> /usr/bin/bellsys/log

###### 2) COPY the schedule to be loaded in to temp directory
cp /usr/bin/bellsys/schedules/$1 /usr/bin/bellsys/tmp/$1
echo "copied tab $1 to temporary directory" >> /usr/bin/bellsys/log

###### 3) COPY the user "bells"'s crontab to the bax directory incase things get borked
cp /var/spool/cron/crontabs/bells /usr/bin/bellsys/bax/
echo "copied current crontab to bax directory" >> /usr/bin/bellsys/log

###### 4) DELETE the current crontab file for "bells"
rm /var/spool/cron/crontabs/bells
echo 'removed current crontab file' >> /usr/bin/bellsys/log

###### 5) MOVE the file from the tmp diectory to the "bells" user's crontab
mv /usr/bin/bellsys/tmp/$1 /var/spool/cron/crontabs/bells
echo 'crontab file updated' >> /usr/bin/bellsys/log

###### 6) START the cron deamon again
/etc/init.d/cron start
/etc/init.d/cron reload
echo 'cron deamon refreshed' >> /usr/bin/bellsys/log
echo "system updated. Now running the $1 schedule" >> /usr/bin/bellsys/log
echo '##########' >> /usr/bin/bellsys/log
echo 'script executed successfully'
echo "now running the $1 schedule"
exit 0
#END

Now, I KNOW the code is weak, and bulky, but I'm doing this book in hand. 
This script does not seem to work. I'm thinking it has to do with the whole DO NOT EDIT THE CRONTAB FILE DIRECTLY thing.

Can I do something like this:

cat /usr/bin/bellsys/scedules/regular > crontab -u bells -e

Looking for a way to pull this off. Any help would be appreciated.

---

### Post by SpaceTeddy on 2008-02-18
i don't quite get why you would want to edit the users crontab files instead of the gloabl crontab, where it should work. You can specifiy the user the script/programm should run under and you CAN simply replace that file or parts of it which will take effect immediatly after cron is restarted... 

you can find the file to edit (yes, you can edit it directly !) in /etc/crontab. 

hope this helps :)

---

