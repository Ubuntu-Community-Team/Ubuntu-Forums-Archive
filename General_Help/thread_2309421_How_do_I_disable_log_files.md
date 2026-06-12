---
title: "How do I disable log files?"
date: 2016-01-10
forum: General Help
---

### Post by chj191 on 2016-01-10
Hi. I am so tired of this logging stuff.
My .xsession-errors file is at 33GB now and I tried to delete it, but that didn't free up space.
Why is this thing enabled at all? Is it a bug or is it suppose to be that way?
How do I fix this so I never have to worry about running out of space?
And don't tell me to reboot. That's annoying. Although it works and is probably the easiest way to get rid of the logs, it still doesn't turn off logging.

---

### Post by deadflowr on 2016-01-10
First things first is you should see what is causing the eating.
More likely than not you have something that is causing it to loop.

But beyond that you can set the file to link to /dev/null, like from here Post#2,
[http://ubuntuforums.org/showthread.php?t=1517991](http://ubuntuforums.org/showthread.php?t=1517991)


 > I tried to delete it, but that didn't free up space.

You probably only moved it to the trash.
Ubuntu defaults to send to trashcan, which you then empty.

---

### Post by matt_symes on 2016-01-10
Hi

> **chj191 said:**
> And don't tell me to reboot

Reboot. You may have deleted (unlinked) the file but the kernel still has an open file descriptor to it and that will not be released until the process that opened the file is closed. i.e Until you reboot (or restart X).

> That's annoying. Although it works and is probably the easiest way to get rid of the logs, it still doesn't turn off logging.

If you want to free up the space then you need to either reboot or restart X. 

Kind regards

---

### Post by CharlesA on 2016-01-10
You would be better off finding out why that log is filling up instead of just sending it to dev/null.

---

### Post by chj191 on 2016-01-10
For starters, if it's possible to turn the logging off, it's easier to stop the logging from happening than looking into the 35GB log file which is impossible to open because it's so big.
And also. I didn't just move the file to the trash. That'd be stupid
I actually removed it and even tried to overwrite the file with a blank document.
So again. How do I disable logging?
In my opinion, this logging thing shouldn't exist on an OS that is suppose to be user friendly.
At least it should be turned off by default.
It can be enabled on Arch Linux and those type of systems.

---

### Post by CharlesA on 2016-01-10
There are many ways to read a file that large.

You could try using tail to see if any of the most recent errors can be resolved.

```
tail -n 50 ~/.xsession-errors
```

---

### Post by matt_symes on 2016-01-10
Hi
> **chj191 said:**
> For starters, if it's possible to turn the logging off, it's easier to stop the logging from happening than looking into the 35GB log file which is impossible to open because it's so big.

Why would you want to open the entire file ?

```
tail -n100 ~/.xsession.errors | less
```

...for the last 100 lines.

> And also. I didn't just move the file to the trash. That'd be stupid
I actually removed it and even tried to overwrite the file with a blank document.

That'll fix it.

> So again. How do I disable logging?

I *really* think you should find out what is creating the errors in the log file and see if it can be fixed.

However, it's your machine so, copy and paste this into the terminal.

```
sudo sed -i 's/^exec >>"$ERRFILE" 2>&1$/#&2/g' /etc/X11/Xsession
```

Enter your password, It will not be echoed to the screen. Then *reboot*.

> In my opinion, this logging thing shouldn't exist on an OS that is suppose to be user friendly.
At least it should be turned off by default.
It can be enabled on Arch Linux and those type of systems.

I disagree. Logging is visibility into what your system is doing.  The fact that you have a log file that is 33G should tell you something about your system immediately.

Arch is a fine distribution. Maybe that's a better distribution for you as you can configure it any pretty way you please.

Kind regards

---

### Post by chj191 on 2016-01-10
I appreciate your help, guys.
But I'm really not interested in doing something that the ubuntu team should have done.
Debugging and programming is not something the user should be doing.
I know ubuntu is free, but seriously.
That stuff gives me a headache.

You know how Microsoft and Apple do these things, right?
They send the errors to the cloud and fix the bugs in their next update.
And that's how ubuntu should be doing it as well.
The fact that these logs are being saved locally on your hard drive in year 2016 is kinda mind blowing and primitive.

> **matt_symes said:**
> I *really* think you should find out what is creating the errors in the log file and see if it can be fixed.
However, it's your machine so, copy and paste this into the terminal.
```
sudo sed -i 's/^exec >>"$ERRFILE" 2>&1$/#&2/g' /etc/X11/Xsession
```
Enter your password, It will not be echoed to the screen. Then *reboot*.

Thank you so much.
I still think the logging should've been disabled by default.
Then if you're a programmer or configure type of guy, you can turn it on.
I'm kinda surprised that the system can't fix these things on its own in the background though.
Oh well.

---

### Post by qamelian on 2016-01-10
Nope, Windows does the same thing (stores logs locally) and if you have a problem that causes those logs to grow out of control, it can lead lead to unexpected behaviours on your Windows PC. Having log files turned on is not primitive. If you give a darn about tracking down and resolving issues on you're own computer, it's pretty much essential, whether you run Linux, Windows, Mac OS, BSD, etc. On Windows, if you are allowing the OS to upload bug reports, log files are often uploaded s part of the report, just like they are on Ubuntu.

---

### Post by chj191 on 2016-01-10
Really? Cuz I have never had that issue on Windows.
Besides. On windows if there's a bug, the program sends an error report.

---

### Post by qamelian on 2016-01-10
I've seen it happen many times on Windows. And you can submit error reports on Ubuntu, as well. Even when error reports are submitted on Windows (or any others), it doesn't necessarily mean the problem gets fixed in the next round of updates. I've submitted error reports to Microsoft for issues that remained outstanding for a number of years, because they simply weren't considered by MS to be a high priority issue. And as I said, when Windows sends a bug report, it includes the necessary log files as part of the report, just like Apport does on Ubuntu.

---

### Post by chj191 on 2016-01-10
They don't report automatically though.
You have to submit them manually. And who's gonna do that? You know.
Either way I think it sucks.
This whole log thing should be cloud now.
And it's more secure too. I mean if you are doing something important and the disk is suddenly full, you're screwed.
Everything freezes, you can't save your file. It's annoying as hell, man.

---

### Post by qamelian on 2016-01-10
And that's exactly the experience I've had when Windows log files get too big. As for who wants to initiate bug reports manually? I do. Especially after catching Microsoft bug reports trying to include confidential information that had no business being in the report. I want full control of that process.

---

### Post by chj191 on 2016-01-10
Yea but you're the type of guy who would do that.
I don't think most people would submit error reports.
When I see a error message pop up I feel annoyed and hit escape.
And I think most people are like that. I think only tech interested people would sit down and submit an error report.
The rest of us wait for the next update and hope for the best or whatever.

---

### Post by QIII on 2016-01-10
Perhaps Ubuntu is not the best OS for you to be using if it causes you such consternation.

Seriously.

---

### Post by chj191 on 2016-01-10
Wouldn't say it causes any consternation. But what do you recommend?
I thought ubuntu was the best linux OS. That's where I've been told at least.
And aside from this log issue thing, I haven't really had any problems with it.
Not compared to windows, which is slow and annoying.

---

### Post by SeijiSensei on 2016-01-10
Logging is an essential feature of *nix systems.  One of the reasons I hate trying to troubleshoot anything in Windows is the lack of extensive log files.

It's been suggested a number of times that you try and determine why the .xsession-errors log is growing so large.  I'll repeat that suggestion.  My .xsession-errors is 171 bytes.

One thing you can do is truncate the file then watch it in a terminal window as you do various things.  Open a terminal and type:
```
cd ~
cat /dev/null > .xsession-errors
tail -f .xsession-errors

```
That will truncate the file and begin listing new entries as they are recorded.  Watch those entries as you do other things to see what is causing the problem.

---

### Post by chj191 on 2016-01-11
> **SeijiSensei said:**
> One of the reasons I hate trying to troubleshoot anything in Windows is the lack of extensive log files.
That shouldn't be your job as a user though.
Even the fact that a person who doesn't get payed by microsoft (or ubuntu in this case) would look into these problems and report them is kinda weird.
That's a weird thing to do. Why would you spend your time on that?
If it's your hobby I can understand, but to do that for free. That's an out of it thing to do.
You know.
So that's why I'm saying. Let all that stuff happen in the background, upload the log to the cloud, report it automatically and let the system try to fix it on its own by using the log or whatever.
I don't know if it's even possible for the system to fix itself like that. But it should be.
That should be like the next thing to focus on, Ubuntu team.

---

### Post by XBNCPRk on 2016-01-11
So really, what you want is an absolutely free, community-maintained operating system, without actually being part of the community. You want a system to do whatever it wants to try and fix itself, even though the devs have no possible way of testing every possible problem and setup, and you still feel comfortable telling the devs that they should focus their efforts on fixing only the (unknown because you wont take 60 seconds to look) problem you have with your one machine rather than the thousands of other things they can do. 

:-({|=  <--- Ill now play my tiny violin while I weep for the death of common sense.

---

### Post by QIII on 2016-01-11
This thread has begun to eat its own tail.

---

### Post by Irihapeti on 2016-01-11
Thread closed. It's turned into an argument about how Ubuntu should be different. I suggest that the discussion should be had with Canonical itself.

---

