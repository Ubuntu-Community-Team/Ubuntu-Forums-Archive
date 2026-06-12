---
title: "communal living with ubuntu"
date: 2008-03-11
forum: General Help
---

### Post by MizikeJulian on 2008-03-11
so i set up the computer in the living room of our house, like me and 8 other people could potentially be using this computer at one time or another, i of course choose ubunut as the operating system, 
the only thing we use it for is to access the internet, and everything is right in the world.
 right so like theres 9 of us, nobody really has any need for privacy or specific user names, file systems, and all that, and really it comes down to just being an annoyance to have to log in, now personally i don't mind it, and i made the first user something fairly easy to remember, and i'm not at all opposed to making a sign with the user name and password, but hey this is open source technology after all,
 i was wondering if there was an easy way to have the computer automatically log in or something, so that all a user would have to do it turn it on and then start to use it. right any ideas would be appreciated,

also im gonna be a bad forum poster and make this a 2fer1,

down here in Mississippi they burn coal to make the power, not just any coal mountaintop coal, from the Appalachian  mountains, right so mississippi power has the monopoly, and well our solar panal-bike-carbattery super monopoly crushing generator, isn't exactly up and running yet, so my convaluded question is can somebody help me to understand how to set up anacron to turn off my computer after its been idle for so long, or like every night at 1am or something,

right thanks for the 2fer1,

right and sorry verbosity 

the revolution will be on you tube

---

### Post by bodhi.zazen on 2008-03-11
[http://ubuntuforums.org/showpost.php?p=3203881&postcount=47](http://ubuntuforums.org/showpost.php?p=3203881&postcount=47)

---

### Post by Oldsoldier2003 on 2008-03-11
set up a cronjob  for  the time you want the computer turned off
the command is shutdown -P  you may want o have this as a root cronjob so that tehre are no permission issues with execution of shutdown

the crontab listing should look like this:

```
00 1 * * * /sbin/shutdown -P
```

---

### Post by bodhi.zazen on 2008-03-11
doh, missed the second question, thanks Oldsoldier2003 :)

You could also simply add an at command to rc.local

at uses HH:MM or you can use terms like midnight. Not as sexy as cron, but it gets the job done :)

[http://linux.about.com/library/cmd/blcmdl1_at.htm](http://linux.about.com/library/cmd/blcmdl1_at.htm)

---

### Post by MizikeJulian on 2008-03-11
sweet thanks for the quick reply

---

