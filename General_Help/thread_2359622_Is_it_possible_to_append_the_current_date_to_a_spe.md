---
title: "Is it possible to append the current date to a specific part of a file?"
date: 2017-04-26
forum: General Help
---

### Post by Roasted on 2017-04-26
Hi friends. I have a series of backup jobs using rsync that run on multiple systems. Those rsync scripts will append a current date/time stamp to a txt file barring that the rsync job completes. This is great in the sense that it allows me to make sure things are running. The catch is, it's appending stamps to multiple txt files (one file per system).

I got to wondering if I could make this a bit simpler with one view to encompass all backup jobs, but it comes with a snag that I'm not sure about. I'd like to brew up my own basic HTML page, something that is hosted internally. That way I hit the bookmark and it comes up with a list of systems and their last backup. Overall, a very rough sketch would look like this.

H1 - Backup Logs /H1
--File Server--
April 26, 10 PM

--Web Server--
April 25, 9 AM

--Personal Laptop--
April 24, 6 PM

What I'm curious is how I can append the current date/time to a specific part of the file. That way, I'm assuming, I could rig up a "destination" in the html file for the date command to target.

Using the above example, let's just say File server, Web server, and personal laptop are $dest1 $dest2 $dest3 respectively. Then for my personal laptop, instead of the typical "date >> logs.html", it would be "date $dest3 >> logs.html" or something of that nature. I'm sure that syntax is wildly incorrect, but for sake of explaining what I'm after I figure that gets the idea across.

The idea is to edit an exact field and only that field, then edit each backup script to reflect where it should place the new date/time stamp for that backup job. I'm just not sure how to target it. Any ideas?

---

### Post by TheFu on 2017-04-26
If you want versioned backups, use **rdiff-backup**. The syntax is very similar to rsync and it uses librsync underneath.
Then all of this goes away.  You can get a list of backups from the back directories directly.

Plus, I really like that a backup takes 1-4 minutes for a complete system. Of course, the 1st backup is like a copy, but after that, it is very fast.  The last backup looks just like an rsync mirror, it is only the older versions which use compressed diff files for any changes.

We shouldn't need to worry about date stuff with our versioned backups, right? Let the tool handle it.

Here's a quick report that I email out every morning for a few systems:
```
=== Time for Backups to spam2 === 
StartTime 1493187064.00 (Wed Apr 26 02:11:04 2017)
EndTime 1493187073.73 (Wed Apr 26 02:11:13 2017)
ElapsedTime 9.73 (9.73 seconds)
TotalDestinationSizeChange 995 (995 bytes)


=== Time for Backups to lubuntu === 
StartTime 1493183707.00 (Wed Apr 26 01:15:07 2017)
EndTime 1493184063.76 (Wed Apr 26 01:21:03 2017)
ElapsedTime 356.76 (5 minutes 56.76 seconds)
TotalDestinationSizeChange 24766085 (23.6 MB)


=== Time for Backups to hadar === 
StartTime 1493184915.00 (Wed Apr 26 01:35:15 2017)
EndTime 1493184935.99 (Wed Apr 26 01:35:35 2017)
ElapsedTime 20.99 (20.99 seconds)
TotalDestinationSizeChange -416482 (-407 KB)


=== Time for Backups to romulus === 
StartTime 1493185511.00 (Wed Apr 26 01:45:11 2017)
EndTime 1493185701.40 (Wed Apr 26 01:48:21 2017)
ElapsedTime 190.40 (3 minutes 10.40 seconds)
TotalDestinationSizeChange 157096 (153 KB)


=== Time for Backups to xen41 === 
StartTime 1493186713.00 (Wed Apr 26 02:05:13 2017)
EndTime 1493186836.02 (Wed Apr 26 02:07:16 2017)
ElapsedTime 123.02 (2 minutes 3.02 seconds)
TotalDestinationSizeChange 8712104 (8.31 MB)


=== Time for Backups to nextcloud === 
StartTime 1493189415.00 (Wed Apr 26 02:50:15 2017)
EndTime 1493189528.69 (Wed Apr 26 02:52:08 2017)
ElapsedTime 113.69 (1 minute 53.69 seconds)
TotalDestinationSizeChange 17120866 (16.3 MB)


=== Time for Backups to cc3550 === 
StartTime 1493179446.00 (Wed Apr 26 00:04:06 2017)
EndTime 1493179919.47 (Wed Apr 26 00:11:59 2017)
ElapsedTime 473.47 (7 minutes 53.47 seconds)
TotalDestinationSizeChange 120871996 (115 MB)

```
It is really just an egrep to filter existing data about the backups.  Tells me what I need to know about the backups today - when, how long, how much.  The 8 min backup is for a netbook over wifi.  If wired ethernet, it would have been about 2 min.

Failures or backups that didn't run, have a blank stanza with the === xxxxxxxx === header. My media server doesn't get backed up daily, so I see those missing stanza.  "Standard Error" is the term we used.

Of course, if you want to keep using rsync, then you'll want to create the date-stamp using bash **touch file-$(date "+%F")-whatever.txt** should get you started.

---

### Post by Roasted on 2017-04-26
> **TheFu said:**
> If you want versioned backups, use rdiff-backup. The syntax is very similar to rsync and it uses librsync underneath.
Then all of this goes away.  You can get a list of backups from the back directories directly.

Plus, I really like that a backup takes 1-4 minutes for a complete system. Of course, the 1st backup is like a copy, but after that, it is very fast.  The last backup looks just like an rsync mirror, it is only the older versions which use compressed diff files for any changes.

We shouldn't need to worry about date stuff with our versioned backups, right? Let the tool handle it.

But regardless of which mechanism I use to back up, rdiff, rsync, etc., I want to set up a way that I can physically see the machine completed a backup. Otherwise the backup process is entirely transparent to the end user. I have the backup jobs running via systemD upon resume from suspend/fresh boot/etc. Because it's systemD, there didn't seem to be any way I could tie in desktop notifications in userland. That was kind of the point behind this idea, just so I had a handle on being able to determine "oh wow, that system hasn't backed up in 2 weeks, what's up with that?"

---

### Post by TheFu on 2017-04-26
I was updating my first reply when you posted. Please re-read it.

Completely understand the desire for positive feedback on success AND failures.  Agree that is almost as important as actually getting the data and doing periodic test restores. Backups without validated restores aren't really backups. They are "hope", not "a plan."  I prefer email over a web interface, but that's just me.  I barely use web stuff and email has been central to my server monitoring for decades.  I get logwatch reports daily too, BTW.

I wouldn't use systemd.  I'd use anacron.  @daily or @weekly as the periodic option.  Then it is up to cron when backups actually run. It works very well, but you have to allow time for the backups to actually happen.

If you run a daily script that looks for backups, then emails that result to people - Backup done/not done.  Here's another report, that the tool can make.

```
# rdiff-backup --list-increment-sizes cc3550
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed Apr 26 00:04:06 2017         21.3 GB           21.3 GB   (current mirror)
Tue Apr 25 00:04:05 2017         13.4 MB           21.3 GB
Mon Apr 24 00:04:05 2017         11.2 MB           21.3 GB
Sun Apr 23 00:16:15 2017          174 GB            196 GB
Sat Apr 22 00:04:06 2017          132 MB            196 GB
...
Thu Mar  2 00:04:04 2017         42.9 MB            201 GB
Tue Feb 28 07:30:56 2017         12.7 MB            201 GB
Mon Feb 27 00:04:05 2017         10.8 MB            201 GB
Sun Feb 26 00:04:05 2017          497 MB            201 GB
Sat Feb 25 00:04:05 2017          289 MB            201 GB
```
As you can see, the machine, cc3550, didn't get backed up every day. It is a chromebook running Ubuntu, so when it isn't on my network, backups don't happen.  That report above is created from that exact command.  Can run it for any other system.  I keep backups all on a backup server under /Backups/${hostname}/   The backups go to a single disk, no RAID, 1.5TB in size.  Media backups are handled separately - to different storage.  

Anyway, this works for me AND I've restored after disk failures a few times. Takes about 45 min to get a system working again.

---

### Post by Roasted on 2017-04-26
It's something I'll have to tinker with. Right now I'm doing raw data rsync backups, which I like, because raw files are just raw files. Given rsync is so quick and by default it does incremental updates it works out rather efficiently. I understand that this is different than rdiff as rdiff will create a series of slices of the new data changes. It has its benefits for sure. It's just not something that I've leveraged.

I thought about using email, but truth be told I have a lot going through my email as-is. I'd really just like to leverage a singular place that I manually check to see what updated and what didn't. That's where the custom HTML file came into mind.

I questioned whether or not I should be using systemD for the backup procedure, but in the end I had difficulty justifying to not use it. By leveraging systemD to run a quick rsync after every resume from suspend/boot, it ensures that systems are getting checked at least once, sometimes multiple times a day. That part is kind of cool to me. In the last month that I've been using it I've been very happy with how it handles it. I think it'd have to be a pretty compelling case against systemD to cause a change in how I currently use it, as right now it does the job well. I've looked into anacron but I was driven by wanting to ensure a backup ran when the maximum allotted time was available. When I resume my laptop, I may be on it for 5 minutes, or 5 hours, it's difficult to say. In either scenario, by leveraging the backup to run 1 minute after the system wakes up (I just have sleep 1m in the backup script) allows me to utilize the maximum available time for that session for the backup to run. That's just my view on it, though. I know there's a bit more I can do to maximize the use of backups, but right now the raw data after resuming/boot up is consistent, quick, and works well for what it is.

---

### Post by TheFu on 2017-04-26
Did my $(date ...) command help?

BTW, rdiff and rdiff-backup ARE NOT THE SAME.

---

### Post by Roasted on 2017-05-05
Just wanted to follow up. Sorry on the delayed response, had some life events happening.

I found a workable alternative (workable for me anyway). Basically I just installed Apache on my file server and rigged up a folder called backup_logs. Inside there I have things broken out, i.e. a folder for each system/server. The idea is simple -- when the backup scripts complete, they simply touch a file with the service name, date, and time. I set Apache to sort newest up top, so the most recent backup entries appear at the top. This gives me a backlog as well, but offers me a quick glance to see the last backup with the most recent being listed up top.

A reminder that the way I rigged up these scripts, it only creates these files if the rsync process completed with error code 0 (success). 

I also set up an mtime script which deletes all files older than 90 days in the backup_logs directory. That way it offers some degree of automated cleanup.

It may not be glorious, but it's functional. It's only hosted internally, but it allows me to hit a bookmark and see what all happened, which was really my goal.

Embedding the image URL didn't seem to work, so here's a direct link: [http://imgur.com/a/epIuF](http://imgur.com/a/epIuF)

---

