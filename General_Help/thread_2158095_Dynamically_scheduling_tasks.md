---
title: "Dynamically scheduling tasks"
date: 2013-06-27
forum: General Help
---

### Post by fairysdad on 2013-06-27
Hi all,

I'm working on a way of recording (logging) a radio station's output. At the moment, software is used that records in hour-long segments, which is absoutely fine for archiving purposes, but when presenters want to take their programmes and do things with it (ie, cut it down for podcasts or 'best-of's) then it gets a little awkward if a programme is over two files (for instance, the logger software cuts its file at the top of the hour, but the programme is broadcast between quarter to and quarter past the hour). It would be much more useful if the logger logged the output on a per-programme basis. I intend to use ALSA's 'arecord' to record the file - at the moment I've been playing with using 'streamripper' as the 'track' title changes depending on the programme (rather than the track being played) so that works fine to record, it just seems a little silly given that at the moment, the same computer that's running streamripper to do the logging is the one that's having the audio fed into it to send to the streaming servers!

The schedule is held in a mySQL database, and, as you'd expect, contains the start and end times of the programmes. However, it is not necessarily a standard time for recording. At the moment, a cron task runs a PHP script that connects to the database to update the website and the stream titles as well as collect listener statistics. This runs every ten minutes, so it's already extracting the data it needs.

However, how can I get 'arecord' to run at the correct time with the correct paramaters? So, if on the ten-minute cron task, I find that the next programme starts at 10.30, and is 45 minutes long, I'll need to set up 'arecord' to record at 10.28 for 49 minutes (I also want to add a couple of minutes either side just in case - on community, RSL, and student stations, presenters don't often keep to time!). But the next day, the 10.30 show may be 60 minutes long, or the show that started at 10 may run until 11. The PHP scrupt that runs every ten minutes gets all of this data, but how can I use that to schedule?

A scour of the Internet came up with two options, one was to get PHP to write to crontab, the other - that seemed closest to what I want - was [from here]("http://stackoverflow.com/questions/6711366/how-can-i-trigger-events-in-a-future-time-in-php"), but that involves running a cron task every minute... surely that can't be a good way to do it? (The scour wasn't too successful, mostly because I wasn't entirely sure what I was exactly searching for!)

Any help would be gratefully received!

---

### Post by ricomoss on 2013-06-27
I would use Python with psychopg2 (depending on your DB) and the datetime library.  Pull out the datetime and determine the timedelta of the programme.  Then use Python's subprocess functionality to kick off a process with the appropriate time parameters.

---

### Post by fairysdad on 2013-06-28
I'm quite a beginner when it comes to Python, but knowing about programming languages and suchlike I've managed to put together a Python script that gets the programme information from the mySQL database, calculates what time to start the recording (2 minutes before the programme starts), generates the filename and runs the relevant arecord command.

However, I'm still at a loss when it comes to working out how to use the start time as the time to start the recording. So far, what I've done I could quite easily have done using PHP (which although a web language, I have used as a programming language in the past) so generally today's exploits have been more one of learning than of necessity - not that it's not been useful, I've been wanting to learn Python and for me it's better to have an actual task to code rather than the pointless tasks that beginners books makes you do!

I realise there's a scheduler of sorts within Python, but again it's the practicalities of doing what I want to do. The way it seems at the moment with this is that I would have this script running from a point in the current programme waiting for the start of the next programme for it to start recording. If this is the case, it still doesn't answer my original question, as I'd still have to run the script - whether PHP or Python - at 'random' points during the day (I say 'random'; there's no way of making the times algorithmic) without knowing exactly when except in the scripts.

So how can I dynamically schedule tasks to run?

---

### Post by fairysdad on 2013-06-29
Okay, apologies for the double post. I managed to get a bit of a work around for this in editing the PHP script that runs every 10 minutes to check if the next programme starts before the next time the script will run, and if it does I run the Python script. So now I'm just testing it out to see if it works.

However, this does seem to be a fix that works rather than an actual way of doing this. Surely there MUST be a way of scheduling tasks depending on their time in a database (or elsewhere) allowing for the fact that the times may change and won't be static (so putting them in crontab isn't really suitable)?

So although I've worked my way around the problem to a solution (hopefully), is there an actual way of doing this? Anybody?

---

