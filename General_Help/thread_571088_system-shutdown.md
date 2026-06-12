---
title: "system-shutdown"
date: 2007-10-08
forum: General Help
---

### Post by rynp1984 on 2007-10-08
Gud day all,.

  Newbie here,. badly need your help guys,. previously i used dapper in my pc here in office,. but i have a problem,. as i turn my pc on, it shutdown automatically after a couple of minutes,.  as i turn it on again,. then it runs all day,.. 
    
  This happens every day (morning) the first time i turn my pc on,.  

  So i decided to install fiesty,. but it doesnt work,. still my pc shutdown everyday the first time i turn my pc on,. i already check the cmos or bios setup regarding the power management and im sure that there is no problem with its configuration or with my system hardware,.
 
  As i look on the syslog,..
  
  user anacron[5264]: Anacron 2.3 started on (date)
  user anacron[5264]: Normal exit (0 jobs run)
  user /usr/sbin/cron[5299]: (CRON) INFO (pidfile fd = 3)
  user /usr/sbin/cron[5300]: (CRON) STARTUP (fork ok)
  user /usr/sbin/cron[5300]: (CRON) INFO (Running @reboot jobs)

 this was the last log right after my pc shuts off,..

 my pc was dual booted with win xp,. i test to start first with xp for me to be able to know if the problem is within the hardware,. i wait for almost an hour but it never shuts off,. 

  pls help me guys how can I able to get rid of this cron or what so ever script, which turns my pc off everyday without any prompts or messages..

  Hope you can me guys,. :( Thank you in advance,.

---

### Post by tgalati4 on 2007-10-09
Post output of:
>crontab -l

To install more detailed system logging:

>sudo apt-get install logwatch

Run your machine through a few cycles, then check either your local email or /var/log for more information on what processes are being run.

---

### Post by rynp1984 on 2007-10-09
contab -l says...

>no crontab for (current_user)

i installed the logwatch, currently observing now,. what other processes run on my system,. i will update you sir as soon as posible if thers any,. 

thank you very much sir tgalati4...

---

### Post by tgalati4 on 2007-10-09
Also check all the files in /var/log for clues as to what is occuring just before shutdown.

Also check dmesg:

>dmesg | grep shutdown

>dmesg | grep error

---

