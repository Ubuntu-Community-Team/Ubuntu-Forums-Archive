---
title: "Calendar App Suggestions for Ubuntu Server?"
date: 2017-01-07
forum: General Help
---

### Post by Robert_Boutin on 2017-01-07
Can anyone suggest a calendar app that I can install on Ubuntu Server?  The feature I am looking for is something I can set to email me a reminder say every year on a specific date, not just show a pop-up reminder. I want to install in on a server so it will just run constantly in the background, emailing me as needed.  I don't want to put reminders on my phone because I have one of the last remaining BlackBerry BB10 phones in existence and I'm going to have to bite the bullet sometime this year and switch (they left me, I didn't leave them...).  And I don't use an email client like Outlook or Thunderbird because I rarely open my laptop (although if that's the only solution, then perhaps I'll need to).

Any thoughts?

Thanks as always

---

### Post by ian-weisser on 2017-01-07
Perhaps something as simple as 'at', which is already part of Ubuntu Server?
Or, perhaps cron for recurring notifications?

---

### Post by Robert_Boutin on 2017-01-08
Thanks, I guess that may be my only option.  I've been trying to find a calendar or reminder that will send me an email at a specified time but so far no such luck.

---

### Post by mastablasta on 2017-01-09
> **Robert_Boutin said:**
>   I don't want to put reminders on my phone because I have one of the last remaining BlackBerry BB10 phones in existence and I'm going to have to bite the bullet sometime this year and switch (they left me, I didn't leave them...). 

i am puzzled. what does one have ot do with the other?

there are a few calendar services.: [SIZE=2]https://www.linux.com/learn/five-best-open-source-calendar-servers-linux
[/SIZE]

but i am not really sure what you are after. 

recurring event email can easilyl be done in chron.

---

### Post by Robert_Boutin on 2017-01-09
I just want to be able to set reminders for myself such that I will be sent an email saying, for example, "Your quarterly self-employment tax is due on X".  For some things, I need a reminder every 24 or 36 months, which is why I don't want to actually use my phone.  I could change phones by then, change OS, etc and can't be sure I could transfer everything to a new phone.  But I know regardless of what phone I have, I can always get email on it.  So if I set up a virtual server that will function only to email out reminders to me, I know I'll not have to worry which device I carry.  I do most of my work by phone, it's my lifeline.  I rarely open my laptop so if I just use my Outlook calendar for example, I will definitely miss reminders.

Instead, is there a calendar app that I can install to actively sync my phone to?  Something I can install onto Ubuntu Desktop? I'm sure Google has something but I'm committed to keeping as much of my information and my clients' information out of Google's hands as possible.   Thanks again.

---

### Post by Robert_Boutin on 2017-01-15
I found a solution.  I installed Nextcloud on my server and installed the Calender app.  The Calendar app will send an email reminder to my phone and since it's always running, I never have to worry about periodically opening my laptop, changing phones, etc.

I can't see how to mark this as "solved" though.

---

### Post by bearlake on 2017-01-15
> **Robert_Boutin said:**
> I found a solution.  I installed Nextcloud on my server and installed the Calender app.  The Calendar app will send an email reminder to my phone and since it's always running, I never have to worry about periodically opening my laptop, changing phones, etc.

I can't see how to mark this as "solved" though.

This is likely help. [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") ;)

---

### Post by mastablasta on 2017-01-16
> **Robert_Boutin said:**
> The Calendar app will send an email reminder to my phone and since it's always running, I never have to worry about periodically opening my laptop, changing phones, etc.


Google calendar does that (for example). you don't even need a phone, just an email address.

---

