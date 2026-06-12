---
title: "Awaken Ubuntu from Sleep/Hibernate, run Cron job"
date: 2006-12-06
forum: General Help
---

### Post by hadiriazi on 2006-12-06
Ok here is the situation:

I want to bring my ubuntu box out of hibernate at a certain time and try to run different programs in a specific order

1.connect to the net (pon dsl-provider) at 3:00 AM
2.run firestarter with root previlges
3.open up amule
4.start download
5.close everything at 7:00 AM

any help will be appreciated

Thanks in advance
Hadi

---

### Post by ciscosurfer on 2006-12-06
Hello, Hadi!

Fellow Ubuntonians, we need to help this guy out! :D  

We have pondered the use of WOL (Wake on LAN) but have chosen not to go this route as his preference is to leave his machines in a state of sleep or hibernation (he has an Ubuntu desktop and an XP laptop...the laptop is connected to a second NIC on his Ubuntu box and is used in this way to provide Internet Connection Sharing -- he used Firestarter to get the ICS up and running -- which, btw, has a really nice one-click ICS feature from within its Firestarter dialog-wizard or preferences.  But I digress). :KS

Hadi has downloaded and likes gnome-schedule, a GUI front-end to cron, as we believe this is the quickest and easiest way to setup tasks that he wants to run.

He basically needs a way of getting out of sleep or hibernate and allowing cron to do it's work.  Anacron is nice, but the cron jobs need to run at the specified times, not at a later time when the machine is woken up (which is what Anacron does). ;)

The possibily of a script that does all of the steps necessary (listed above in his first post, #'s 1-5) would also be cool!! :cool:

---

### Post by ciscosurfer on 2006-12-06
To fellow Ubutuers:
Any script or app will work, KDE or GNOME, it doesn't matter.

---

### Post by crane on 2006-12-06
Do some googling and searching forums for setting up cron jobs. I don't see why you couldn't just set up the jobs in your cron.daily folder.
Just search for ' how to set up cron'
I found [this]("http://www.webmasters-central.com/t/cron.shtml") on a quick search.

---

### Post by ciscosurfer on 2006-12-07
> **crane said:**
> Do some googling and searching forums for setting up cron jobs. I don't see why you couldn't just set up the jobs in your cron.daily folder.
Just search for ' how to set up cron'
I found [this]("http://www.webmasters-central.com/t/cron.shtml") on a quick search.The issue isn't how to set up a cron job, *we know how to do this quite well*.  

The issue is: How do we bring the computer out of sleep or hibernate in order to run these jobs (all automatically, without user intervention, btw).  The computer will be asleep or hibernating before these jobs are executed.

The machine will be sleeping for any amount of time.  It's a matter of getting out of sleep and accomplishing the tasks listed above.

*Is what we want to do even possible?  Considering, we believe, that some process needs to be running in order to do this -- but how would the process be running if we suspend or hibernate?*

---

### Post by hadiriazi on 2006-12-07
Any suggestions or scripts fellow Ubutuers?

---

### Post by ciscosurfer on 2006-12-07
bump...need a solution :-)

---

### Post by rrwo on 2006-12-07
This may have nothing to do with the OS. My guess is that you may need to learn how to program the Power Management system in your computer's BIOS to tell it to wake up at 3.00am.  Then have a cron job that runs at 3.05, does what it needs, and put the computer back to sleep.

Otherwise, just don't put the computer to sleep.  Configure some other power saving features to turn the screen off and stop spinning the hard disk.  I think the latter is more reliable.

---

### Post by tragicglee on 2006-12-07
> **ciscosurfer said:**
> 
The issue is: How do we bring the computer out of sleep or hibernate in order to run these jobs (all automatically, without user intervention, btw).


Forgive me if this is stupid, totally unhelpful and/or has already been tried but... What about BIOS? I've no idea if this is standard but I have an option in my setup that will force the computer to power up at a specified time, no user required.

---

### Post by hadiriazi on 2006-12-07
> **rrwo said:**
> This may have nothing to do with the OS. My guess is that you may need to learn how to program the Power Management system in your computer's BIOS to tell it to wake up at 3.00am.  Then have a cron job that runs at 3.05, does what it needs, and put the computer back to sleep.

Otherwise, just don't put the computer to sleep.  Configure some other power saving features to turn the screen off and stop spinning the hard disk.  I think the latter is more reliable.
Thanks for your reply, but I'm sure we could find a script or a program that does the wakeup job!!

---

### Post by hadiriazi on 2006-12-07
> **tragicglee said:**
> Forgive me if this is stupid, totally unhelpful and/or has already been tried but... What about BIOS? I've no idea if this is standard but I have an option in my setup that will force the computer to power up at a specified time, no user required.
No, you are right, I believe there is an option in the setup menue which forces the computer to wake up, but we were looking into a more GUI way of doing this or should I say ubuntu based, so all tasks will be done inside ubuntu and there will be no need for logging in....
you know more of a full automation thing

*If you could suggest an app to do this or an script it would be awesome*

Thanks anyway

---

### Post by ciscosurfer on 2006-12-08
> **tragicglee said:**
> Forgive me if this is stupid, totally unhelpful and/or has already been tried but... What about BIOS? I've no idea if this is standard but I have an option in my setup that will force the computer to power up at a specified time, no user required.We'll have to check and see whether or not an option exists in the BIOS to allow for this sort of behavior.  If so, then great!  If not, we're back where we left off.

---

### Post by pallaire on 2007-10-23
I am also looking for a solution to this problem. anybody found a solution ? 

I know its doable, because, I can do it in Windows :rolleyes: I can setup a task in the scheduler ( i setup a backup with SyncBackSE) and the computer wakes up in the night to run the backup... so we should be able to do the same in Ubuntu.

I want my computer to be running at 8h am and to go to hibernation at 10h pm ... the sleep part is easy, but I dont know on to wake it up.

---

### Post by Herman on 2007-11-25
> We'll have to check and see whether or not an option exists in the BIOS to allow for this sort of behavior. If so, then great! If not, we're back where we left off.
Hello ciscosurfer,
nikoPSK, aslso asked about BIOS settings for booting up at a pre-set time, in this thread: [Stupid Computer Tricks]("http://ubuntuforums.org/showthread.php?t=622368").
Hello nikoPSK :)

Some computers have this feature in their BIOS and others don't. All we can do is look around for it and see if we can find it.

My PC Chips 'Book PC' had an Award Modular BIOS v6.00PG which has lots of features, and it has the setting in 'Power Management Setup' -->'Resume by Alarm.
I just need to set 'Resume by Alarm' to [Enabled], and then, looking down one or two lines, I can set the day of the month and the time of day.
If I leave the 'Date (of Month) Alarm set to 0, it will boot up every day at whatever time I set in the 'Time (hh:mm:ss) Alarm setting.

My Acer laptop has a very simple Pheonix BIOS and it doesn't have any settings like that.

My wife's Acer Desktop  has a Pheonix Award Bios and in her computer's CMOS (BIOS), you go into Power Management'-->'PM Wake Up Events', and press 'Enter'.
In that page you can find similar settings as already described above.

I'll continue this when I shut down the machine I'm typing from now to take a look around in the BIOS.

Regards, Herman :)

---

### Post by Herman on 2007-11-25
I'm back! :)

My Custom made computer which I assembled myself has an ASUS M2T TVM motherboard with a v02.58 American Megatrends BIOS, and it was hard to find the feature I was looking for. I wasn't obvious, but I did find it in a reasonably short time.
I went into 'Power'-->'APM Configuration'-->'Resume on RTC Alarm'.
It was only after setting that to [Enabled] that the next settings became visible.
I set 'RTC Alarm Data (Days) to [Every Day]
I set 'System Time' to [03:30:30], (I wake up at 04:00 every day). 

That's three out of four of the computers I have plugged in right now that I was able to find this feature in.

I wonder if crontab (for my alarm to go off), will still run if no-one is logged in though?

Are you with me,  nikoPSK?
Did that help you find that feature in yours? 

Regards, Herman :)

---

### Post by jal on 2007-11-25
I'm sorry, I don't have an answer, just want to clarify something.

The BIOS on my old machine (from last century) turns it on at a specific time every day, and I could run a script at that point.

However, I don't think that answers the original posters question.

The question from OP was:
"Awaken Ubuntu from Sleep/Hibernate."

If the machine is powered off it is not running any OS. The next thing to run must be the a cold start BIOS->boot sequence. So there is no way for  a cron to lurk. 

If it is in "sleep" mode however, I'm guessing that the OS, or a portion of it, is still loaded, and presumably ticking over slowly, waiting on the wakeup signal.

I'm just wondering, what happens to running bg scripts when dropping into hibernate? Is the scheduler still running? Could it be as simple as having a "sleep $t; getstuff.sh" in a shell script? Probably not, otherwise it would have been mentioned.

By the way, I am running Gutsy on a thinkpad and it  doesn't wake up from hibernate/sleep at all, I need to use the power button and re-start from cold.

---

### Post by Herman on 2007-11-25
I just tried a few experiments with cron and as long as the computer will boot to the login screen, some cron jobs will run, others won't. 
I think it's mainly anything to do with a GUI probably. SOme things won't work without the user logging in first, but I'm not certain, more experiments will be needed.

For example, my CD/DVD drawer will open and close okay from the eject : eject -t commands, but I can't get totem to play my music for my alarm to wake me up in the morning. I also tried play, (there is a program called play that can be used to play some sound files from the command line). That didn't work for me either.

> If the machine is powered off it is not running any OS. The next thing to run must be the a cold start BIOS->boot sequence. So there is no way for a cron to lurk. 
 Yes, that's what I think too. I think the only way is to use the BIOS to boot the machine first, then the machine can run a cron job once it's booted.
> If it is in "sleep" mode however, I'm guessing that the OS, or a portion of it, is still loaded, and presumably ticking over slowly, waiting on the wakeup signal. Well my computer normally is left running all night and I use a cron job to open the CD drawer to turn on the kettle for me and then cron starts totem to play me music to wake me up in the morning, link: [SIZE=2][http://picasaweb.google.com/herman543/HowMyComputerMakesCoffee](http://picasaweb.google.com/herman543/HowMyComputerMakesCoffee) [/SIZE]

[SIZE=2]Now I'm wondering if the computer can do that even if it has been turned off to save electricity.

I don't know very much about hibernate mode, I haven't tried that out enough, maybe I should.
[/SIZE] 
[SIZE=2]Regards, Herman 
[/SIZE]

---

### Post by nikoPSK on 2007-11-25
> **Herman said:**
> Hello ciscosurfer,
nikoPSK, aslso asked about BIOS settings for booting up at a pre-set time, in this thread: [Stupid Computer Tricks]("http://ubuntuforums.org/showthread.php?t=622368").
Hello nikoPSK :)

Some computers have this feature in their BIOS and others don't. All we can do is look around for it and see if we can find it.

My PC Chips 'Book PC' had an Award Modular BIOS v6.00PG which has lots of features, and it has the setting in 'Power Management Setup' -->'Resume by Alarm.
I just need to set 'Resume by Alarm' to [Enabled], and then, looking down one or two lines, I can set the day of the month and the time of day.
If I leave the 'Date (of Month) Alarm set to 0, it will boot up every day at whatever time I set in the 'Time (hh:mm:ss) Alarm setting.

My Acer laptop has a very simple Pheonix BIOS and it doesn't have any settings like that.

My wife's Acer Desktop  has a Pheonix Award Bios and in her computer's CMOS (BIOS), you go into Power Management'-->'PM Wake Up Events', and press 'Enter'.
In that page you can find similar settings as already described above.

I'll continue this when I shut down the machine I'm typing from now to take a look around in the BIOS.

Regards, Herman :)

> **Herman said:**
> I'm back! :)

My Custom made computer which I assembled myself has an ASUS M2T TVM motherboard with a v02.58 American Megatrends BIOS, and it was hard to find the feature I was looking for. I wasn't obvious, but I did find it in a reasonably short time.
I went into 'Power'-->'APM Configuration'-->'Resume on RTC Alarm'.
It was only after setting that to [Enabled] that the next settings became visible.
I set 'RTC Alarm Data (Days) to [Every Day]
I set 'System Time' to [03:30:30], (I wake up at 04:00 every day). 

That's three out of four of the computers I have plugged in right now that I was able to find this feature in.

I wonder if crontab (for my alarm to go off), will still run if no-one is logged in though?

Are you with me,  nikoPSK?
Did that help you find that feature in yours? 

Regards, Herman :)
Well, I'm not going to try this now, as I have to leave soon but thanks alot!

---

### Post by jal on 2007-11-26
> **Herman said:**
> I 
 Well my computer normally is left running all night and I use a cron job to open the CD drawer to turn on the kettle for me



I never thought that I would use the acronym Herman, I'm one of these old fashioned people that spell out texts with punctuation.

When I read that, well, I ROFL.

---

