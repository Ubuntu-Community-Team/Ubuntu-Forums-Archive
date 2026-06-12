---
title: "Nautilus not opening. Only get error in term when running as sudo..."
date: 2016-12-18
forum: General Help
---

### Post by uRock on 2016-12-18
I have been having some problems with not being able to open Nautilus after the system has been sitting idle for a while. When I try to open Nautilus using sudo via terminal I see an error stating the app is being used by another windows manager. I would've copied and pasted that error, but right-click stopped working as well.

After going through that I restarted the system and went into the log file viewer and found this;```
Dec 18 11:01:52 5FDP systemd[1]: Stopping User Manager for UID 108...
Dec 18 11:01:54 5FDP systemd[2472]: Reached target Shutdown.
Dec 18 11:01:54 5FDP systemd[2472]: Stopped target Default.
Dec 18 11:01:54 5FDP systemd[2472]: Stopped target Basic System.
Dec 18 11:01:54 5FDP systemd[2472]: Stopped target Paths.
Dec 18 11:01:54 5FDP systemd[2472]: Stopped target Sockets.
Dec 18 11:01:54 5FDP systemd[2472]: Starting Exit the Session...
Dec 18 11:01:54 5FDP systemd[2472]: Stopped target Timers.
Dec 18 11:01:54 5FDP systemd[2472]: Received SIGRTMIN+24 from PID 7100 (kill).
Dec 18 11:01:54 5FDP systemd[1]: Stopped User Manager for UID 108.
Dec 18 11:01:54 5FDP systemd[1]: Removed slice User Slice of lightdm.
```
This has me wondering if there is something running on my system that shouldn't be running or if I should be doing a fresh install. I had previously installed and ran Kodi for just enough time to realize it can't be trusted on a desktop system, so I removed it. 

Ubuntu 16.04 64 bit with Unity.

What are your thoughts?

Thanks,
uRock

---

### Post by DuckHook on 2016-12-19
Hi uRock

I've always found the act of removing one of two merged flavours to be fraught with lurking dragons. I am assuming that this is what you mean when you say "installed Kodi". If you dual booted, then I'm off by a country mile.

If the former, then it is entirely possible that a config file was borked, or systemd's new registry was somehow corrupted. I suppose you could chase the problem down given enough time, but how long would that take? I wouldn't even know where to start. I guess you have to compare time and trouble involved in playing detective/bug squasher vs backing up/reinstalling.

Sorry I can't be of more help. :(

---

### Post by uRock on 2016-12-19
> **DuckHook said:**
> Hi uRock

I've always found the act of removing one of two merged flavours to be fraught with lurking dragons. I am assuming that this is what you mean when you say "installed Kodi".I think this is the issue. I believe there are remnants of packages left behind by Kodi that are causing my random problems. >  If you dual booted, then I'm off by a country mile.

If the former, then it is entirely possible that a config file was borked, or systemd's new registry was somehow corrupted. I suppose you could chase the problem down given enough time, but how long would that take? I wouldn't even know where to start. I guess you have to compare time and trouble involved in playing detective/bug squasher vs backing up/reinstalling.

Sorry I can't be of more help. :(
 I am going to go ahead and do a reinstall. Thanks for the input!

---

### Post by mc4man on 2016-12-19
nautilus in 16.04 does suffer from a sporadic issue where it can't be opened. So may or may not be what you've seen.
(- as I remember "nautilus" from a terminal would report that nautilus is already running
[https://ubuntuforums.org/showthread.php?t=2343615](https://ubuntuforums.org/showthread.php?t=2343615)
In this case killing the process does allow it to open. Here I used to see about once a week or so though now not for that last several weeks.

So your issue may be different or different cause as never saw anything about a different windows manager ..

---

### Post by #&amp;thj^% on 2016-12-19
> **mc4man said:**
> nautilus in 16.04 does suffer from a sporadic issue where it can't be opened. So may or may not be what you've seen.
(- as I remember "nautilus" from a terminal would report that nautilus is already running
[https://ubuntuforums.org/showthread.php?t=2343615](https://ubuntuforums.org/showthread.php?t=2343615)
In this case killing the process does allow it to open. Here I used to see about once a week or so though now not for that last several weeks.

So your issue may be different or different cause as never saw anything about a different windows manager ..

+1  Seen it also...thought that running release to release may have been the bad side effect...but after a fresh clean Re-install...still is seen.
"killall nautilus" makes it right again...but shouldn't have to use that.

---

### Post by DuckHook on 2016-12-19
Hmmm...

Does invoking nautilus from CLI tell you anything at those times that it acts up?

---

### Post by uRock on 2016-12-19
> **mc4man said:**
> nautilus in 16.04 does suffer from a sporadic issue where it can't be opened. So may or may not be what you've seen.
(- as I remember "nautilus" from a terminal would report that nautilus is already running
[https://ubuntuforums.org/showthread.php?t=2343615](https://ubuntuforums.org/showthread.php?t=2343615)
In this case killing the process does allow it to open. Here I used to see about once a week or so though now not for that last several weeks.

So your issue may be different or different cause as never saw anything about a different windows manager ..
I've just finished reinstalling. I'll report back if I see this happen again. Thanx!

> **1fallen said:**
> +1  Seen it also...thought that running release to release may have been the bad side effect...but after a fresh clean Re-install...still is seen.
"killall nautilus" makes it right again...but shouldn't have to use that.
I will keep this trick in mind if I should see the issue again. I'm hoping the reinstall fixed this issue.

Cheers & Beers,
uRock

---

### Post by uRock on 2016-12-19
> **DuckHook said:**
> Hmmm...

Does invoking nautilus from CLI tell you anything at those times that it acts up?

I would only get an error about another DM currently using Nautilus when trying to run it as root. If I tried without using sudo, then I'd just get a blinking cursor with no response.

I had lost my sense of security after watching the effects of running a Kodi device on my network and after seeing how heavy it was on this system.

That said, I feel much better after reinstalling the system.

---

### Post by #&amp;thj^% on 2016-12-19
> **DuckHook said:**
> Hmmm...

Does invoking nautilus from CLI tell you anything at those times that it acts up?

Mine just reports nautilus is already running...
wonder if this will be the same reply the others have also seen?

---

### Post by bearlake on 2016-12-19
Likely the answer is above already but using sudo to run Nautilus is incorrect. ( so i have been told )

Usually it's "pkexec nautilus" isn't it?

---

### Post by mc4man on 2016-12-19
> **DuckHook said:**
> Hmmm...

Does invoking nautilus from CLI tell you anything at those times that it acts up?
In regards to the sporadic nothing of value, something along the lines of 'nautilus is already running'
In a ubuntu session that's not 'unique' news as nautilus is handling the desktop so it's always running from login on..

Could be some obscure by-product of mixed gnome versions being used in a 'unlike gnome' session (ubuntu session

---

### Post by mc4man on 2016-12-19
> **bearlake said:**
> Likely the answer is above already but using sudo to run Nautilus is incorrect. ( so i have been told )

Usually it's "pkexec nautilus" isn't it?
It's not a good idea verbatium (sudo nautilus) though uRock posted "as sudo", not 'with sudo' so exact implementation is not clear..

By default pkexec nautilus isn't enabled but the nautilus-admin package will provide it. Otherwise sudo -H nautilus is ok.

---

### Post by bearlake on 2016-12-19
> **mc4man said:**
> It's not a good idea verbatium (sudo nautilus) though uRock posted "as sudo", not 'with sudo' so exact implementation is not clear..

By default pkexec nautilus isn't enabled but the nautilus-admin package will provide it. Otherwise sudo -H nautilus is ok.

Thanks

---

### Post by uRock on 2016-12-19
I was running it as "sudo nautilus", though I wouldn't have done that for any reason other than invoking an error message. There are much better ways to gain access to the file system.

---

