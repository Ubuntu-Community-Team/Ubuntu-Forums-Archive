---
title: "Does anyone have any clever power saving scripts.?"
date: 2022-06-29
forum: General Help
---

### Post by comfysofa on 2022-06-29
Hi to all. Joined here quite a while ago and while ive, in the past tended to "dabble" in linux - last year i changed my job which now is now 50 50 between linux and windows..... ive just been asked if i could work out a way of saving power in our lab as we have over 50 linux servers running and a fair chunk dont get used all of the time, so, i wondered if there was a way i could check to see when a user was last logged in (say 48 hour threshold) and if not, put the machine to sleep.....90% of our servers are centos 7 and the remaining are current Ubuntu server (18.04) from recollection.

Oh - and just to say that weve got the bios's set in a way that when they are running theyre running full tilt so i cant use the normal power management tools to put them to sleep...

Im not anywhere near the heady heights of creating scripts from scratch but to save reinventing the wheel wondered if someone else has done anything like this?

Cheers to anyone that chips in.

PS - my join date is this month...weird as i joined this forum years ago....probably where ive not logged in for ages...but ive a feeling ill be here a lot more often!

---

### Post by Doug S on 2022-06-29
In recent years the power management group within the linux kernel project have made considerable progress towards the objective of minimal power consumption when idle while maintaining rapid response time for step function load demands. Tell us more about your systems, in particular what processors are used and what default CPU frequency scaling drivers and governors? Idle energy consumption can be very low even when using the "performance" governor, depending on the processor. Do you limit idle state depths? What exactly do you mean by "we've got the bios's set in a way that when they are running they're running full tilt" and why do you do that?

---

### Post by HermanAB on 2022-06-29
Well, the ultimate power saving script would be ‘shutdown -now’.

---

### Post by comfysofa on 2022-06-30
Thanks for the reply. Processors: We were running intel only and most tend to be ice lake and cascade lake cpu's - The reason theyre set to max out is were using them as mobile phone basestation testbeds the reason is pretty well most of the time under normal usage they need to be maxed out for maximum data transfer at 5g speeds - essentially we have a "cell tower" in our lab which boxes of mobile phones connect to to load the system hence the question that if one of our users isnt logged in the server can be put to sleep...

---

### Post by comfysofa on 2022-06-30
> **HermanAB said:**
> Well, the ultimate power saving script would be ‘shutdown -now’.

Yep - thats fine...but im trying to work out how to instigate that shutdown command by interogating the server to see when the last user logged on, set a threshold of say 48 hours and the sleep (or power off) - if powering off is easier thats fine as our engineers have access to the ipmi to power it back up again...

---

### Post by HermanAB on 2022-06-30
Hmm, you can use a cron job to send an email message to all users saying: ‘The server will shut down in ten minutes.’ Then in true BOFH style, after nine minutes, shut it down.  If the users don’t check their mail and don’t know how to cancel the cron job, it will go down.

The above is far better than trying to figure out whether a logged in user is alive and kicking, or went home without logging off.

---

### Post by ActionParsnip on 2022-06-30
You can use the "last" command to see when users logged in. You can also use the "w" command to see who is logged in as well.

---

### Post by comfysofa on 2022-06-30
> **HermanAB said:**
> Hmm, you can use a cron job to send an email message to all users saying: ‘The server will shut down in ten minutes.’ Then in true BOFH style, after nine minutes, shut it down.  If the users don’t check their mail and don’t know how to cancel the cron job, it will go down.

The above is far better than trying to figure out whether a logged in user is alive and kicking, or went home without logging off.

Ok - playing devils advocate (how i tend to learn) - thats the server saying it will shut down but, i want to leave a window of hours since, the last user was using it....am i right in saying that this is the cron job just saying its shutting down as apose to the server waiting for usage to go "quiet" then, shut down..?

As i say - compared to you guys i would class myself as "thick at best" with linux! so my steps are...

1. Work out how to instigate the behavior what commands to use.
2. Then work out how to script it (ideally id like to run it from one of our servers thats on 24/7) - if i have to (im not too sure yet if its something that can run independently on each server.)

Not too sure if theres anything after that...if i can run from the one machine then if i want to make adjustments i can do it from the one...

Look forward to any insight, opinion and help.

Thanks for the replies so far...!

---

### Post by HermanAB on 2022-07-01
The problem is that it is very difficult to detect missing users that just walked away, or users that are actually sitting there reading a manual, etc.

It is far easier to tell users that the machines will attempt to shut down at specific times of day (say 12 noon and 6 pm) and if they want to keep working and overrule that behaviour, then they need to run a command to prevent it.

The prevention can simply be a file called something like ‘/tmp/nosleep’ which the cron job can look for and then delete.  The user can create the file with ‘touch /tmp/nosleep’ and the machine will then keep going till the next cron event.

---

