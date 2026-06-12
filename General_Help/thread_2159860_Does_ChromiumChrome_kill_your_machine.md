---
title: "Does Chromium/Chrome kill your machine?"
date: 2013-07-04
forum: General Help
---

### Post by wyth on 2013-07-04
For some time now -- at least a good few months -- Chromium and to a lesser degree Chrome has been slaughtering my laptop, locking the entire works up, sometimes for hours, to the point of needing to REISUB just to use the machine again. Both are at versions 28.

I'll give some specifics, but what I want to know is 
A.) Is this happening to anyone else, and 
B.) Is there a fix for it beyond using Firefox?

**Specifics**
This is happening on a Lenovo Y510 laptop with an Intel GM965 graphics card. This has never been a problem in the past, only in the last few months. (And I almost never have these issues with Firefox.) It also happens with extensions enabled or disabled. (This almost never happens on my desktop with a more powerful nvidia card.)

I'm not certain if this is related to flash, and I have click to play enabled. An example of what might happen is: I open say a newspaper web page and maybe a twitter page at the same time, and the entire machine will lock up. The mouse won't move, all cpu and internet activity on the system load indicator stops, and I can't get to any other open applications.

If I'm lucky, I can ctrl-f1 to a terminal and in htop kill any plugin running in Chromium/Chrome, and then ctrl-f7 back to find that the tab killing everything is now dead. Until the past month or so, I was able to do that maybe 30% of the time; the other 70% I've just had to REISUB. Lately, I only have to REISUB about 30% of the time, and if it's so locked up I can't get to a terminal more often than not I can just wait out the stall. However, if I wait out one stall and another happens, it always requires an REISUB. But in all cases -- whether I can wait it out, kill the plugin, or if I have to REISUB -- it happens a few times a day, and only when running Chromium or Chrome. 

Since it's a plugin that seems to be the problem, I'm pretty sure it must be flash, but I'm not positive because it'll happen when I'm opening pages without any flash content running (IO9 will kill it every day, sometimes Disqus, even this page). Since Chrome uses a newer version of flash than Chromium, I'm guessing that's why it has fewer problems, but something in the way Chromium/Chrome is implementing flash seems to send the entire machine into a grand mal seizure. 

I'd file a bug, but there are already bugs for this sort of problem going back a couple years -- not all related to Chromium/Chrome -- and at this point no solutions. The only thing I've narrowed it down to is Chromium (which is the worst, sometimes locking everything up on launch) and Chrome, and probably the way they implement a plugin (most likely flash). 

So I'm just posting this to see if anyone else has either seen this and/or has a solution, rather than file another bug which just yields another 40 "me too's". If there are some things to try with Chromium/Chrome, I'll try them, because overall I like using those browsers a little more than Firefox. But if not, I guess I'll just have to accept going back to Firefox for now. 

Ideas?

---

### Post by Bashing-om on 2013-07-04
wyth; Hello.

I do not know ... For your consideration to (re-)install chrome/chromium:
I have chrome installed onto 3 machines all AMD based,
On the more powerful system no problems at all with chrome with a low quality graphics (ATI) card ... screamingly fast and responsive.
On the next lower end machine .. with a better (Nvidia) card .. Chromium ran with no problems, chrome with several extensions on occasion does lock up, backing out of chrome and restarting restores the operation (Face Book with other pages open that are graphics intensive);
on the Dell laptop ... AMD Nvidia card ... no problems at all . But to this time never pushed as hard as the "lower end machine".

All with broad band access.

[INDENT][INDENT]just my input
[/INDENT][/INDENT]

---

### Post by pqwoerituytrueiwoq on 2013-07-04
try putting [FONT=courier new]pkill -f flashplayer[/FONT] in a cron job and see if that fixes it in chromium (not chrome)
that command will terminal all flash plugins when you run it
if chrome has a way to disable flash try that

---

### Post by VMC on 2013-07-04
> **wyth said:**
> For some time now -- at least a good few months -- Chromium and to a lesser degree Chrome has been slaughtering my laptop, locking the entire works up, sometimes for hours, to the point of needing to REISUB just to use the machine again. Both are at versions 28.

I'll give some specifics, but what I want to know is 
A.) Is this happening to anyone else, and 
B.) Is there a fix for it beyond using Firefox?

**Specifics**
This is happening on a Lenovo Y510 laptop with an Intel GM965 graphics card. This has never been a problem in the past, only in the last few months. (And I almost never have these issues with Firefox.) It also happens with extensions enabled or disabled. (This almost never happens on my desktop with a more powerful nvidia card.)
...
I had this problem with Chrome, using an older version, but I see your using the latest version. Mine froze up the system using somewhere around version 25. I haven't had this problem now for months. Also I have nvidia graphics and amd cpu. Hardware does play a part.

---

### Post by wyth on 2013-07-05
Thanks for the replies -- I'll keep that pkill command handy. And yeah, cleaning everything out/reinstalling does help *some *(as long as the config files are nixed), but the seizures still persist.

---

### Post by Bashing-om on 2013-07-05
wyth; Hey .. I got to looking.

When I installed Google-chrome was a version of chrome that required an old "libudev0_175-0ubuntu13_amd64.deb" library. As version 13.04 did not have that required lib... had to d/l and install it ... That deficiency, I read, was to have been alleviated in chrome with the release of version 28. But I have not seen where it was. (might be an interesting exercise to see if chrome still depends on that old library)

What version of 'buntu are you running and maybe the library is required ?

[INDENT][INDENT]it's a thought
[/INDENT][/INDENT]

---

