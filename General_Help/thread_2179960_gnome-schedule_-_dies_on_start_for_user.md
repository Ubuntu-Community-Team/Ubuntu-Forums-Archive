---
title: "gnome-schedule - dies on start for user"
date: 2013-10-10
forum: General Help
---

### Post by bAs3YGM on 2013-10-10
I have been using the gnome-schedule application for several months.  Today I tried to add a job that I scheduled for the future (roughly one year) so I could just test it now and then copy what I needed into another ready-made job.

As soon as I clicked the Add button it was done.  I can no longer open gnome schedule on that user.  I get the following error:
[EMAIL="user@server:~$"]user@server:~$[/EMAIL] gnome-schedule
Traceback (most recent call last):
  File "/usr/share/gnome-schedule/gnome-schedule.py", line 74, in <module>
    mainWindow = mainWindow.main(debug_flag, False, pr, manual_poscorrect)
  File "/usr/share/gnome-schedule/mainWindow.py", line 257, in __init__
    self.schedule_reload ()
  File "/usr/share/gnome-schedule/mainWindow.py", line 308, in schedule_reload
    data = self.at.read ()
  File "/usr/share/gnome-schedule/at.py", line 514, in read
    array_or_false = self.parse (line)
  File "/usr/share/gnome-schedule/at.py", line 174, in parse
    if script[-1] == "\n":
IndexError: string index out of range
[EMAIL="user@server:~$"]user@server:~$[/EMAIL] 

If I run as root I can switch user to my user, but it pops up a box that says "No such user".  It does, however, load the jobs for that user, but only gets part of the descriptions correct.

I have tried:
  running crontab -r as the user.  It clears the jobs, but gnome-schedule still doesn't work.
  running crontab -u user -r as root.  It clears the jobs, but gnome-schedule still doesn't work.
  I checked /etc/group and made sure my user was in the crontab group
  I have also uninstalled and reinstalled gnome-schedule

Any advice for me here?  I know the problem happened when I tried to add a one-time task far in the future, but how to I find and get rid of that task?

---

### Post by bAs3YGM on 2013-10-10
I found my answer on launchpad after searching for a few hours (but quickly after I posted).

As follows:
[TABLE]
[TR]
[TD]GauteHope (eg)            wrote             on 2009-08-27:
[/TD]
[TD="class: bug-comment-index"][ #1]("https://bugs.launchpad.net/ubuntu/+source/gnome-schedule/+bug/419471/comments/1")
[/TD]
[/TR]
[/TABLE]
This happens when you create a one-time task in gnome-schedule 2.0.2 and try to open it in 2.1.0. There is a bug in the parser of the data files.
This has been fixed in upstream and will be included in the next minor release; to manually delete your old tasks. Do in the terminal:
$ atq # to display all tasks, the first number is the job id
 $ atd [number] # on all the numbers that showed up in atq
go to the gnome-schedule data dir:
 $ cd ~/.gnome/gnome-schedule/at/
 $ rm * # delete all files in the directory
- gaute

So the quick version is remove things in ~/.gnome/gnome-scheduler/at
You can also clear the descriptions if you clear out the ~/.gnome/gnome-scheduler/crontab
this will NOT affect the actual jobs in CRON.

---

