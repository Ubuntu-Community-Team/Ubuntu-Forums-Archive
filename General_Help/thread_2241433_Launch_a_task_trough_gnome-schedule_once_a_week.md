---
title: "Launch a task trough gnome-schedule once a week"
date: 2014-08-26
forum: General Help
---

### Post by Rih_Ba on 2014-08-26
Hi Guys,

I am currently launching a task through gnome-schedule with 'every week' basic timing setting.  It looks like it sets up the task to be executed on every Monday at midnight. The problem is that if I do not have my laptop switched on, then obviously task is not going to get executed. As I cannot always predict when I am going to have my laptop on, I would like the scheduling be more flexible. Pretty much I would like the task to run no more or less than 1 time a week, no matter on which day or time frame, but execution should occur when my laptop is turned on. Is it possible to set up configuration like that through gnome-schedule or I have to use something else ?

Thanks in advance,
Richard

---

### Post by btindie on 2014-08-26
gnome-schedule is just a front end for crontab, e.g. from a shell type 'crontab -l' and it'll show the crontab entries it's installed.

If you create a system cron job that'll then use anacron to run it which is able to handle the fact your laptop isn't running 24/7. - see 'man anacron'.

To create the job, from the shell run 'sudoedit /etc/cron.weekly/MY_JOB' - where MY_JOB is the name of the job. It'll prompt you for your password.

You need need to write a shell script to run the commands you want. You didn't say if you've already got a script or if it's just a couple of commands that you want to run?

By default it'll run as root, but you can change that by using 'su'.

```
#!/bin/sh

su - -c '/home/richard/bin/myjob' richard

```

And remember to make that script executable or it won't run - 'sudo chmod +x /etc/cron.weekly/MY_JOB'

The above script will run the script /home/richard/bin/myjob as user 'richard'.

---

### Post by Rih_Ba on 2014-09-16
> **btindie said:**
> 
If you create a system cron job that'll then use anacron to run it which is able to handle the fact your laptop isn't running 24/7. - see 'man anacron'.

To create the job, from the shell run 'sudoedit /etc/cron.weekly/MY_JOB' - where MY_JOB is the name of the job.


Thanks for your reply.
If I create a cron job as you are describing above, is it really going to use anacron in any way ? If a create a cron job for my script, shouldn't I create an hourly anacron job to be run via cron as anacron is not a daemon ?

---

### Post by Bucky Ball on 2014-09-16
Welcome. Either way, if your computer is off when a cron job is scheduled, the cron job should run the next time it has the opportunity, i.e. the next time your computer is on. ;)

---

### Post by btindie on 2014-09-16
> **Rih_Ba said:**
> If I create a cron job as you are describing above, is it really going to use anacron in any way ? If a create a cron job for my script, shouldn't I create an hourly anacron job to be run via cron as anacron is not a daemon ?

Provided the anacron deb is installed (dpkg -l anacron) and the cronjob is installed in /etc/cron.{daily,weekly,monthly} then it'll run via anacron.

Creating it as an hourly job will result in it being run via cron and you'll have to implement the logic to have it only run once a week as you stated in your original question. You'll end up duplicating the logic that already exists in anacron.

From /usr/share/doc/anacron/README.Debian
> Anacron itself however is not a daemon, so it will either be called at startup,on APM power status change, or by cron. Disabling those will result in some
jobs not being executed on time.

The anacron deb installs it's own crontab into /etc/cron.d/anacron which is used to run it on a daily basis via cron, this is in addition to being run at startup.

---

### Post by Rih_Ba on 2014-09-18
> **btindie said:**
> 

The anacron deb installs it's own crontab into /etc/cron.d/anacron which is used to run it on a daily basis via cron, this is in addition to being run at startup.

Here is a good summary how anacron is invoked by default for ubuntu -
[http://www.softprayog.in/tutorials/anacron](http://www.softprayog.in/tutorials/anacron)

But what I fail to see how is  /etc/cron.d/anacron crontab linked to cron so that it sees that  /etc/cron.d/anacron should be taken into consideration ?

---

### Post by Rih_Ba on 2014-09-18
> **Rih_Ba said:**
> Here is a good summary how anacron is invoked by default for ubuntu -
[http://www.softprayog.in/tutorials/anacron](http://www.softprayog.in/tutorials/anacron)

But what I fail to see how is  /etc/cron.d/anacron crontab linked to cron so that it sees that  /etc/cron.d/anacron should be taken into consideration ?

Looks like cron.d folder is used by cron as another location for manually made crontabs, as it is decribed in cron man.

But I've run into another issue:

The script I am trying to run is supposed to bring up the an new xterm window. 

When I edit  /var/spool/anacron/cron.weekly so that timestamp is bigger than a week and then run anacron command manually everything works fine and the new xterm pop up happens.

But when I either plug into my AC adapter, wake up computer from sleep or even wait for the time specified under /etc/cron.d/anacron the xterm window does not come up, but time stamp is getting changed for the cron.weekly job, as /etc/cron.weekly/0anacron script is getting executed(which changes timestamp) and then mine script which is next in alphabetic order is executed as well but (i've checked that) but xterm pop up does not come up. What might be the issue here ?

My scripts code under cron.weekly 

```

#!/bin/sh
#
# Command for creating scheduled android image  in xterm


/bin/tcsh -c "xterm -hold -T android_image -e /home/user/bin/android_image.pl"

```

---

### Post by btindie on 2014-09-19
> **Rih_Ba said:**
> The script I am trying to run is supposed to bring up the an new xterm window.
That won't work as it relies upon the DISPLAY variable which is unset when run through cron.

If you look in your logs or local email for root you'll probably see some error about 'xterm Xt error: Can't open display'

You can test it by running the below in a console
```
$ unset DISPLAY
$ xterm
xterm Xt error: Can't open display: 
xterm:  DISPLAY is not set
```

For background jobs you're better off writing to your own log file, for more detailed information, or using the logger command.

You wouldn't need to modify your existing script, just the cron job to redirect STDOUT to the log file.

Then use the tailf command to watch it write to the log file - e.g. tailf /var/log/mylogs/android_image.log

> **Rih_Ba said:**
> My scripts code under cron.weekly 

```

#!/bin/sh
#
# Command for creating scheduled android image  in xterm


/bin/tcsh -c "xterm -hold -T android_image -e /home/user/bin/android_image.pl"

```
That'll run the script as root, is that what you wanted?

---

### Post by Rih_Ba on 2014-09-21
Thanks everybody, I've got everything sorted out.

---

