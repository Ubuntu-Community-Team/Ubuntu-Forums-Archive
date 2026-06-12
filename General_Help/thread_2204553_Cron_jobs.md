---
title: "Cron jobs"
date: 2014-02-09
forum: General Help
---

### Post by mark103 on 2014-02-09
Hi all just wondering if someone could tell me from the pics i put up if they know what that's doing please.
I'm new to linux so i don't really understand plus i never created those con jobs and
the email i got as well thanks any help would be really appreciated

---

### Post by prasys on 2014-02-09
Based on the image you have given 

The first one is basically php related housekeeping. You could actually open up /usr/lib/php5/maxlifetime , and notice that it actually does some house keeping stuff

The second cron job is related to Mdadm (RAID) , it just runs a consistent check to make sure your array is healthy and such

As for the other picture , i am assuming it is doing some housekeeping of log files.

---

### Post by mark103 on 2014-02-09
thanks very much for getting back to me ok cool so would the raid cron job be setup it self as i didnt set that up ? and the other cron jobs as i didnt set them up thats all and was wondering

---

### Post by prasys on 2014-02-09
Sometimes it get's setup automatically by the application. An example would be the php script , I am assuming that you have installed LAMP (Apache , PHP , MySql combination) and hence that cron script appeared

---

### Post by mark103 on 2014-02-09
yeh i have lamp installed alright how would i get and email to me saying that my RAID has failed ? thanks for your reply :) and have php scripts for CPUTemps and DriveTemps

---

### Post by prasys on 2014-02-09
From what I see is that you have setup cron to send you an e-mail , have you been getting e-mail notification for all of your crons ?

If so there is nothing to worry about :)

---

### Post by mark103 on 2014-02-09
i have php scripts setup so if my cpu goes over 45 degree it will shutdown and send me an email same with hard drives i just wanted to do the same with the raid so i  know if it goes down i have no scripts setup for that and was wondering how id do that so i would get and email

---

