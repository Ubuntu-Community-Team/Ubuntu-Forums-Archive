---
title: "Time is off"
date: 2016-01-27
forum: General Help
---

### Post by ChristmasPi on 2016-01-27
I just finished a fresh install of Ubuntu 14.04 LTS and noticed that the time on my install is behind by 8 hours.  I've checked that the clock is set to my home city and it is set to get the time "automatically from the internet".  It's been like this for about 2 days now.

Is there any way to force it to update rather than having to manually adjust the clock?

Thank you

---

### Post by buzzingrobot on 2016-01-27
So-called "time servers" exist on the internet that do nothing else but provide the time when asked.  "Automatically from the internet" means periodically check one of those servers. A server may be down or unreachable for other reasons.

There's no harm in setting the time manually.

---

### Post by Marcaitus on 2016-01-27
It could be because your router is setup to block the NTP port which is  what is used to set the date and time automatically. You can try to  manually do it by first installing the ntpdate package then running it against Ubuntu's time server.

```

sudo apt-get install ntpdate
sudo ntpdate ntp.ubuntu.com

```

You could of course set it manually as well if you prefer.

---

### Post by QDR06VV9 on 2016-01-27
Just one more thing to add or check is the CMOS battery on the mother board..

---

### Post by Bashing-om on 2016-01-27
ChristmasPi; Hello ;

> 
noticed that the time on my install is behind by 8 hours.


'Nother thought, are you dual booting with Windows, such that Windows controls the hardware clock  (adjustable) ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-01-27
Oh Yes Yes..Forgot all about the dual boot option, as I do not dual boot with windows(anyway).
Just a quick show of how to do that for those that do not know.

.To fix the UTC / local time difference between Ubuntu and Windows from Ubuntu by making Ubuntu use local time, you must edit the /etc/default/rcS file and replace "UTC=yes" with "UTC=no" (both without the quotes). To do this automatically, simply copy/paste the following command in a terminal:
```
sudo sed -i 's/UTC=yes/UTC=no/' /etc/default/rcS

```

And then reboot.
To Revert back if necessary
```
sudo sed -i 's/UTC=no/UTC=yes/' /etc/default/rcS

``` 
Hope this is helpful.
Regards

---

### Post by ChristmasPi on 2016-01-27
Thank you everyone for your suggestions and tips, I am going to bookmark this thread.

The time has been off for the past two days, but of course, Murphy's Law, today the time is bang on.  The only thing different was there was a prompt for an update which I completed.

I wonder if it was as simple as just a time server being down.  I don't think my router blocks this service because it has worked in the past and of course is working again today.

Thank you again everyone for your time.

---

### Post by Bashing-om on 2016-01-28
ChristmasPi; Ho Kay !

Pleased that the situation has a happy conclusion. We mark this one up
(r)eason (f)or (o)utage : unknown, suspect at the distant end.

However:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]we look forward to another time
[/INDENT][/INDENT]

---

