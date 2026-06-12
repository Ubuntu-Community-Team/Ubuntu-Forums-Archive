---
title: "ntpdate cron job not working"
date: 2007-10-07
forum: General Help
---

### Post by 7echno7im on 2007-10-07
Hello,

I am running ubuntu server 7.04 in a virtual envirnment and the time drift tremendously.  In efforts to keep it relatively close I created a few cron jobs to try and stop it.  They are running as root, and if I look at the cron.log I can see they are running, but the time is not syncing unless I run the manually.  Here is my crontab

* * * * * /etc/init.d/ntpdate

0,5,10,15,20,25,30,35,40,45,50,55 * * * * ntpdate 10.10.1.5  #sync time to 10.10.1.5

These are 2 jobs I have made to try and get it to work.  

If I run the job manually as root or privileged user, it runs fine as show below:

ntpdate 10.10.1.5  #sync time to 10.10.1.5
 7 Oct 20:06:58 ntpdate[5447]: step time server 10.10.1.5 offset -1442.729400 sec


Any help is ghreatly appreciated.

Thanks in advance.
Tim

[www.techtronic.us](www.techtronic.us)

---

### Post by abovett on 2007-10-07
Not sure of the answer but here's a few ideas.

1. I'd look for a solution to the clock speed error itself first. Not sure about in a virtual machine, but for my laptop adding the boot option noapictimer solved my clock speed problem.

2. Can you enable the ntp daemon (ntpd) rather than running ntpdate all the time from a cron job? Look at man ntpd for more info.

3. If you do need to use the cron job, try logging the output from the ntpdate command to see if it's reporting why it fails. One method to help with debugging would be to put the ntpdate command in a small script and run that from cron.  It can then redirect the output of ntpdate and also do any other logging or tests you want.

Hope that helps

Andy B

---

### Post by 7echno7im on 2007-10-07
Thanks for the reply.  I am just looking for the best way to keep the server's time correct.  My time server on my domain is 10.10.1.5, if you can help me keep this is sync, it would be appreciated. 

My virtual machines are running on MS Virtual Server 2005 R2, and this seems to be a common problem and there is not a current way to fix it.  I think it is because the cpu cliock on the virtual machines sway, from 1.8 to 1.9.  I could be wrong, but it happens on all my guest ubuntu machines on this server.

I have ntpd installed, and the /etc/ntpd.cof is correct, however this never solved my issue.  I have also heard of ntp-simple, but not sure how to configure.  If the daemon will check on the time server every few minutes that would be grand, I just made cron jobs because it was easy for me to track and log what was really going on.

The cron jobs are running according to the cron log, but no error and no details of the job, it just says it ran the command, almost like the command is just waiting for somehting, I never see the same output that I do when I run it manaually

---

### Post by 7echno7im on 2007-10-07
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0481bb4a-410c-4e34-a850-fcc2f3591abe ro [SIZE="5"][COLOR="Red"]noapictimer[/COLOR][/SIZE]

is that where I add it?  if so, it is not helping.

---

### Post by 7echno7im on 2007-10-07
this is in my cron log, it is running but nothing is happening:

Oct  7 21:46:01 pluto /USR/SBIN/CRON[6545]: (root) CMD (ntpdate -u 10.10.1.5)
Oct  7 21:45:55 pluto /USR/SBIN/CRON[6549]: (root) CMD (ntpdate -u 10.10.1.5)
Oct  7 21:46:01 pluto /USR/SBIN/CRON[6553]: (root) CMD (ntpdate -u 10.10.1.5)

---

### Post by 7echno7im on 2007-10-08
none of the cron jobs I put in cron are even working.  They run fine from command line, but not from cron...


I HATE YOU CRON

---

### Post by 7echno7im on 2007-10-08
OK cron I still hate you but I found a fix for anyone that runs into an issue with cron.  

I have found that creating an entry in crontab using -e did not work.  I created a script that ran the cron job and actually put it in /etc/cron.hourly and scheduled it to go every minute.  Don't ask me why, but it works.  Something about putting it in crontab, it never runs.

---

