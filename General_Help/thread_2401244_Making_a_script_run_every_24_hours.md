---
title: "Making a script run every 24 hours"
date: 2018-09-15
forum: General Help
---

### Post by webmiester on 2018-09-15
Hi, I want to have a particular script to run every 24 hours (or any interval for that matter).  Or to make it run at a specific time everyday
  How do I do this?

I was thinking of something like this:

Make a script called 24h.sh

Contents of 24h.sh

#!/bin/bash

echo "This will run once a day" &
sleep 24h
24h.sh &

Do you think this script will work?  Is there a better way to do this, or should I just use the cron file?

Thanks

---

### Post by TheFu on 2018-09-15
Use cron or anacron.  Google "crontab howto" ... 

That sleep 24h is a terrible idea, IMHO.

You've been asking many basic questions that are covered in **any** Linux book.  Many are online.  
 [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) Some you can buy in a bookstore or online store if you prefer.   Cron would be covered in a basic Unix class.  LPI has lots of training materials.  [https://www.lpi.org/how-to-get-certified/free-training-materials](https://www.lpi.org/how-to-get-certified/free-training-materials)  I use the LPI materials in my classes and ... 

They all expect an intermediate-level Unix skills, which cannot be skipped over.  Get to that with a book like this:
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - grab the PDF. Read the first 250 pgs, then skim the rest of the book so you know what is possible.  In an afternoon of reading, many things will "click" and this will save you time.  Plus Shotts explains things a little deeper so you'll get the "why" with the "what do I type".

Don't get me wrong, easy answers are fine on these forums, but pretty much anything you think you need has already been created.  Usually there is a solution pattern for 99% of what we'd need.  

For the rest, the online documentation already on your system has the answers.  We aren't supposed to tell people to use the manpages here, but for server stuff, it really is the best source to understand all the options.

For example, you'd like to schedule a task to happen daily or hourly or monthly ... or on the 3rd Tuesday of the month ... 
```

$ man -k schedule
cron (8)             - daemon to execute scheduled commands (Vixie Cron)
....
```
or
```
$ man -k periodic
anacron (8)          - runs commands periodically
...
```
Each has important caveats, so reviewing those in the manpages is smart.  Anancron only allows control at daily or longer intervals.  We don't get to say exactly when a job runs during the day, just that it does, if the machine is on.  With cron, we have 1 minute or longer resolution, but if the machine isn't on at that exact time, it won't run until the next scheduled time, if the machine is on.   Both have multiple locations where tasks are scheduled.  These files have slightly different formats, so knowing each is useful.

And if you are using sudo with either cron or anacron scripts, then you are doing it wrong, almost always.

People to get tripped up making cron scripts work because they assume things that cannot be assumed, usually some environment variables. When/if that happens, feel free to ask for help, but there are 50 threads here about that subject too.  Searching for answers is always preferred.

---

