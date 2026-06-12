---
title: "crontab won't work properly"
date: 2005-05-28
forum: General Help
---

### Post by Mikey7047 on 2005-05-28
I want to run an update to a stats website I have...the script to be run is stats.pl
I try crontab -e and put the following:
*/30 * * * * nice /home/clanfa/Desktop/.psychostats2.3.1/stats.pl
I try sudo crontab -e and put the following:
*/30 * * * * nice /home/clanfa/Desktop/.psychostats2.3.1/stats.pl
I try to edit /etc/crontab with the following:
# m h dom mon dow user  command
*/30 *    * * *   root    /home/clanfa/Desktop/.psychostats2.3.1/stats.pl
#

None of it will work because my stats page is not updating every half hour!
Hopefully someone here knows what I am doing wrong.

---

### Post by jonrkc on 2005-05-29
[QUOTE=Mikey7047]I want to run an update to a stats website I have...the script to be run is stats.pl
I try crontab -e and put the following:
*/30 * * * * nice /home/clanfa/Desktop/.psychostats2.3.1/stats.pl
I try sudo crontab -e and put the following:
*/30 * * * * nice /home/clanfa/Desktop/.psychostats2.3.1/stats.pl
I try to edit /etc/crontab with the following:
# m h dom mon dow user  command
*/30 *    * * *   root    /home/clanfa/Desktop/.psychostats2.3.1/stats.pl
#

None of it will work because my stats page is not updating every half hour!
Hopefully someone here knows what I am doing wrong.[/QUOTE]
 I believe if you will change it to read:

30 * * * * 

instead of what you have now, it will run right.  The first place in the line represents minutes, so if you want it to run at 30 min. past each hour, it goes 30 * * * *.

There are some really good examples in man 5 crontab, written by the man who wrote the crontab program.  It amounts to a brief tutorial.  I can never remember all the combinations and possibilities, but most of them are presented there in that file.  

Hope this helps.

---

### Post by JonahRowley on 2005-05-29
To run every half hour (on minute 0 and minute 30), use:
```
0,30 * * * * nice /home/clanfa/Desktop/.psychostats2.3.1/stats.pl
```

---

### Post by Mikey7047 on 2005-05-29
Thanks for the help guys

---

