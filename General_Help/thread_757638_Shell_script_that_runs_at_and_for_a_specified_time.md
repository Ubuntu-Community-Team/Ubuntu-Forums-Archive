---
title: "Shell script that runs at and for a specified time"
date: 2008-04-17
forum: General Help
---

### Post by frankerooney on 2008-04-17
Hi. Looked around quite a bit but can't find what I want
I would like to be able to run a script "x" that runs at a specific time, for a specific time, thus

x 13:30 60

so x would run at 13:30 (1:30pm) for 60 minutes

Can someone help? I'm quite new at this scripting stuff...
Thanks,
Andy.

By the way can't use cron as the time isn't fixed.

---

### Post by Sukarn on 2008-04-17
The starting time for a script can be fixed in cron, and the finishing time can be fixed by issuing a "killall [script name].sh" command in cron at the time when you want the script to finish

eg, if i want program "a" to start at 1530 hours (3:30 PM) and to be stopped at 1720 hours (5:20 PM) everyday then I can put this in cron (crontab -e)
```

30 15 * * * a
20 17 * * * killall a

```

---

### Post by frankerooney on 2008-04-17
Thanks for that. I don't want to use cron as the script needs to be run at short notice with little or no setup, and straight from the command line. Any ideas?
I was thinking of getting the current time, then working out the difference between that and the time I've specified, and adding the second parameter - time script needs to run onto it. It's easy enough to do 
sleep x
do command &
sleep y
killall command
(end script)
just need to work out how to do the time differencing thing..
Thanks
Andy

---

### Post by Sukarn on 2008-04-17
The command that you're trying to run, does it have to be run just once, or is it repeatedly run in a loop?

---

### Post by frankerooney on 2008-04-17
It just runs once - it's basically to run a script which records from the tv through a av-dv converter. There may be programs already out there to do this but I'd like the flexibility of being able to run whatever scripting I put in the shell script.

So script will start with arguments of something like

recordtv 20:20 21:50 test.mpeg

which would record from 20:20 to 21:50 and output to file test.mpeg

or recordtv 20:20 90 test.mpeg to record 90 mins from 20;20 onwards

something like that.

Was thinking I just need to find the difference between the start and end times, wait until the start time happens, and then sleep between them, killing the process that runs at the end...

---

### Post by Sukarn on 2008-04-18
Well, if I were you, I would just make a cron entry for starting **recordtv** at the desired time, and then a **killall recordtv** entry for stopping it.

But then again, this would be just because I don't know much shell scripting.

---

### Post by kpkeerthi on 2008-04-18
If you want it to run just once, you may use the **[at]("http://unixhelp.ed.ac.uk/CGI/man-cgi?at")** command

Something like this...
```
at 20:19 /usr/bin/recordtv 20:20 21:50 /home/<user>/test.mpeg
```
```
at 20:51 killall recordtv
```

---

### Post by frankerooney on 2008-04-19
Oh, the AT thing sounds the best solution. I guess I could have a script to record more than one program at once

AT 21:00 record tv program a
AT 21:40 killall mencoder or whatever I use to record
AT 21:50 record tv program b
AT 22:30 killall mencoder ...
Will give it a try! Thanks to all who replied.
Andy

---

