---
title: "cron.hourly script not working"
date: 2008-04-12
forum: General Help
---

### Post by skunkwerk on 2008-04-12
i've got a shell script in my /etc/cron.hourly directory that calls a python script (i didn't put the python script in /etc/cron.hourly as its part of a subversion repository i check out as a whole)

the shell script has been made executable and doesn't contain any dots in the file name, and the owner is root as with all the other script in /etc/cron.daily:
ls -l:
-rwxr-xr-x 1 root root 58 2008-04-10 21:10 rundump

shows that cron is running:
ps aux | grep cron
root      2467  0.0  0.0   2348   900 ?        Ss   Apr04   0:00 /usr/sbin/cron
imran    31308  0.0  0.0   3032   708 pts/1    R+   15:55   0:00 grep cron

script doesn't show up anywhere when i do: sudo cat /var/log/syslog | grep CRON:
Apr 12 07:39:01 ip-10-251-106-64 /USR/SBIN/CRON[20960]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
/etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
Apr 12 07:40:01 ip-10-251-106-64 /USR/SBIN/CRON[20973]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /mnt/logs/lighttpd/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=site -update >/dev/null)
Apr 12 07:40:01 ip-10-251-106-64 /USR/SBIN/CRON[20974]: (munin) CMD (if [ -x /usr/bin/munin-cron ]; then /usr/bin/munin-cron; fi)

the script itself, which works when i execute it myself:
#!/bin/sh
/usr/bin/python /mnt/winebago/utils/dump.py

suggestions?

---

### Post by mmc on 2008-04-13
quick suggestions:

[1] check /etc/crontab & make sure that cron.hourly is included.
[2] add another simple script into cron.hourly that just echo's something into a /tmp/newfile or similar to check if the problem is relative to your script or not, i suspect not as i believe the cron directories are checked each minute for updates so you should have seen 'rundump' being added to the list in the syslog outputs...


hth

-mmc

---

### Post by skunkwerk on 2008-04-13
thanks mmc,
   here's the relevant part of /etc/crontab:

17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly

I've added a new shell script 'test' to /etc/cron.hourly:
#!/bin/sh
echo "testing" > /tmp/newfile

and will report back on whether or not it works

---

### Post by skunkwerk on 2008-04-13
the test shell script seems to be working, as it created a /tmp/newfile at 17 minutes on the hour, which is when cron.hourly is set to run... which means it's a problem with my script?

here's the script again:
#!/bin/sh
/usr/bin/python /mnt/winebago/utils/rundump2.py

when I ran ./rundump (the shell script) nothing printed out to the terminal (but i think it might have taken a few seconds to initialize), but seems to be working fine now when I try it again... i'll see if it works now..

thanks

---

### Post by mmc on 2008-04-13
ok - then yes it implies the problem is with your script when running via the cron environment.

first common culprit is that the contents of the script depend on something that is present in your shell environment like a $PATH variable so it can find binaries etc .... this is the most common reason why something will run via the command line but not via cron (remember that the cron does not login as you do so contents of .profile's & friends are not picked up. 

next thing to do after checking the script is to capture the output (just as you did with the test to a tmp file should suffice). this should let you see whats going on.


to speed things up for you try putting the wrapper into /etc/cron.d (you can then call when it runs & define the user to run as - as an example, here's a sanitised version of one of my cronjobs

<snip>
#
# comment to describe cron job goes here
# 

MAILTO=some.real.address@somewhere.com
0 * * * *    mmc     /home/mmc/example.sh
</snip>

the first column is minutes & the second hours ... so this script would run on the hour every hour, tweak the timings as appropriate for you so you dont have to wait an hour for each test ;)   ( ... the email address will also get sent the output so your not blind to what just happened)

hope this helps.

-mmc

---

