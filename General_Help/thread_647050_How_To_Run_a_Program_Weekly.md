---
title: "How To Run a Program Weekly"
date: 2007-12-21
forum: General Help
---

### Post by wayfarer51 on 2007-12-21
OK, I've waded through manuals, examples online, etc, and I'm SEVERELY confused.  I want to run the following weekly: 

```
/usr/bin/tv_grab_na_dd > ~/listings.xml
```

Anacron, cron, what do I use and how do I do it?  Also, anacron is running as a service, but should cron be running too (it doesn't appear on the service list now)?  If so, how do I start it?

Sorry, lots of questions.  I just need a howto procedure to run the prog weekly.

Thanks for your help.

Neill

---

### Post by dcstar on 2007-12-21
> **wayfarer51 said:**
> OK, I've waded through manuals, examples online, etc, and I'm SEVERELY confused.  I want to run the following weekly: 

```
/usr/bin/tv_grab_na_dd > ~/listings.xml
```

Anacron, cron, what do I use and how do I do it?  Also, anacron is running as a service, but should cron be running too (it doesn't appear on the service list now)?  If so, how do I start it?

Sorry, lots of questions.  I just need a howto procedure to run the prog weekly.

Thanks for your help.

Neill

Have a look in your /etc/cron.weekly directory for examples of how other things are run.

---

### Post by wayfarer51 on 2007-12-22
Well, you see, that's part of the problem.  I should probably have posted this in the beginner forum.  The other things in the /etc/cron.weekly directory are incomprehensible to me, thus my request for a howto or a tutorial.

I appreciate your response though.

Neill

---

### Post by IcemanV9 on 2007-12-22
Here's a very good [[COLOR="DarkOrange"]wiki[/COLOR]]("https://help.ubuntu.com/community/CronHowto") on crontab stuff.

---

### Post by capink on 2007-12-22
1. Create a script that contain the command you wish to run and then place the script in /etc/cron.weekly. Here is the command to do these two steps.

```
{ echo '#!/bin/bash'
echo '/usr/bin/tv_grab_na_dd > ~/listings.xml' ; } | sudo tee /etc/cron.weekly/tvgrab
```


2. Make the script executable.

```
sudo chmod a+x /etc/cron.weekly/tvgrab
```

---

