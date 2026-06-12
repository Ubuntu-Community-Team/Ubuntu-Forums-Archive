---
title: "BOINC doesn't suspend while computer in use"
date: 2007-11-14
forum: General Help
---

### Post by slumcat05 on 2007-11-14
I recently installed BOINC to run Einstein@Home to take advantage of unused CPU time while I'm at work. It booted up fine and downloaded a few files and queued up a task.

Problem is, it started running the task even while I am working on the computer. I have messed with the settings both on the Einstein website and in the boincmgr GUI (in both places it is set to only run after 5 minutes of idle, and the "do work while computer is in use" option is unchecked).

A quick look at "top" confirms that the process "einstein_S5R3_4" is using 90%+ of the CPU, and is owned by the user "boinc". I'm guessing it may have something to do with users... does BOINC assume the PC is idle because the user "boinc" hasn't done anything? (Just in case, I added my username and root to the already existing group "boinc", but it had no effect) That's just a shot in the dark, any ideas or solutions will be greatly appreciated. 

I'd really like to make use of my unused CPU time, but I can't have the CPU maxed out all the time when I have work to do. Again, any input will be appreciated. Thanks.

---

### Post by jmar71n on 2007-11-15
Same problem here!

---

### Post by Skip Da Shu on 2007-12-04
I dont' have an answer... well, my answer is set it to "run always" but first thing you should probably do is see where it's pulling preferences from.  Stop and restart the daemon and in the top of the messages tab on the gui manager or in stdoutdae.txt you'll see something like:

12/4/2007 6:47:05 PM||General prefs: from SETI@home (last modified 02-Dec-2007 22:40:59)
12/4/2007 6:47:05 PM||Host location: home
12/4/2007 6:47:05 PM||General prefs: no separate prefs for home; using your defaults
12/4/2007 6:47:05 PM||Preferences limit memory usage when active to 1740.02MB
12/4/2007 6:47:05 PM||Preferences limit memory usage when idle to 2026.61MB
12/4/2007 6:47:05 PM||Preferences limit disk usage to 23.28GB

---

### Post by utkjamie on 2008-06-11
Did anyone come up with a solution for this?

---

### Post by oldsoundguy on 2008-06-11
open BOINC and go to advanced .. then preferences.  You can set disk and memory limits there.

I have mine set at 50% of memory when computer is in use 90% when idle, you can dial it up or down as much as you like there, among a lot of other tweaks.

---

### Post by Skip Da Shu on 2008-06-11
> **slumcat05 said:**
> I recently installed BOINC to run Einstein@Home to take advantage of unused CPU time while I'm at work. It booted up fine and downloaded a few files and queued up a task.

Problem is, it started running the task even while I am working on the computer. I have messed with the settings both on the Einstein website and in the boincmgr GUI (in both places it is set to only run after 5 minutes of idle, and the "do work while computer is in use" option is unchecked).

A quick look at "top" confirms that the process "einstein_S5R3_4" is using 90%+ of the CPU, and is owned by the user "boinc". I'm guessing it may have something to do with users... does BOINC assume the PC is idle because the user "boinc" hasn't done anything? (Just in case, I added my username and root to the already existing group "boinc", but it had no effect) That's just a shot in the dark, any ideas or solutions will be greatly appreciated. 

I'd really like to make use of my unused CPU time, but I can't have the CPU maxed out all the time when I have work to do. Again, any input will be appreciated. Thanks.

In the Boinc_manager (GUI) in the "activity" tab do you have "run based on preferences"?  Otherwise starting up the GUI will activate the work.

Be aware that once local preferences are set they will override anything done at whichever project site is controlling your preferences (last one changed).

Is this still a current problem?  I ask because I installed Ubuntu v8.04 on wife's desktop a few weeks ago and it was suspending whenever I was on it locally (was not always suspending when I VNC'd into it).  

I since converted that machine to Xubuntu v8.04 (64b) and it seems to suspend based on project site general preferences.

---

### Post by utkjamie on 2008-06-12
I'm still having problems with it. My preferences are for BOINC to only run tasks when my computer has been idle for at least 2 minutes (and activity is set to run based on preferences). I don't know if the problem is that BOINC cannot tell when I'm using the computer or if it simply ignores that I am using the computer.

I've only noticed the problem recently, but that may be because I've been paying more attention. I hadn't taken a look at my BOINC stats in a while and loaded up the manager. In the past, I've mostly just run World Community Grid but I added SETI@home, Climateprediction.net, and Malariacontrol.net. I wouldn't expect that one of these "new" projects would be the culprit given that they run via BOINC, but could one of them be the problem?

UPDATE: I tried suspending SETI@home and Climate Prediction but World Community Grid is still running while the computer is active, sometimes hitting 80% or more of CPU usage.

---

### Post by Skip Da Shu on 2008-06-12
> **utkjamie said:**
> I'm still having problems with it. My preferences are for BOINC to only run tasks when my computer has been idle for at least 2 minutes (and activity is set to run based on preferences). I don't know if the problem is that BOINC cannot tell when I'm using the computer or if it simply ignores that I am using the computer.

I've only noticed the problem recently, but that may be because I've been paying more attention. I hadn't taken a look at my BOINC stats in a while and loaded up the manager. In the past, I've mostly just run World Community Grid but I added SETI@home, Climateprediction.net, and Malariacontrol.net. I wouldn't expect that one of these "new" projects would be the culprit given that they run via BOINC, but could one of them be the problem?

UPDATE: I tried suspending SETI@home and Climate Prediction but World Community Grid is still running while the computer is active, sometimes hitting 80% or more of CPU usage.

Are your mouse and keyboard wireless?

If not, Can you do this:

```
sudo /etc/init.d/boinc-client restart
```

and then from the file /var/lib/boinc-client/stdoutdae.txt post the lines (about 15 or 20 down from the restart) that look something like this:

```
10-Jun-2008 22:58:12 [---] General prefs: from ABC@home (last modified 25-May-2008 00:44:26)
10-Jun-2008 22:58:12 [---] Host location: home
10-Jun-2008 22:58:12 [---] General prefs: no separate prefs for home; using your defaults
10-Jun-2008 22:58:12 [---] Reading preferences override file
10-Jun-2008 22:58:12 [---] Preferences limit memory usage when active to 778.44MB
10-Jun-2008 22:58:12 [---] Preferences limit memory usage when idle to 963.32MB
10-Jun-2008 22:58:12 [---] Preferences limit disk usage to 1.88GB
```

---

### Post by utkjamie on 2008-06-12
Here's what I've got...

> 12-Jun-2008 12:42:53 [---] General prefs: from World Community Grid (last modified 10-Jun-2008 18:40:59)
12-Jun-2008 12:42:53 [---] Host location: none
12-Jun-2008 12:42:53 [---] General prefs: using your defaults
12-Jun-2008 12:42:53 [---] Reading preferences override file
12-Jun-2008 12:42:53 [---] Preferences limit memory usage when active to 404.34MB
12-Jun-2008 12:42:53 [---] Preferences limit memory usage when idle to 758.13MB

---

### Post by Skip Da Shu on 2008-06-12
> **utkjamie said:**
> Here's what I've got...

I have an idea but it's a bit of a shot in the dark.

Go to the SETI project page, your account, general preferences and change something, suggest two changes, change idle delay from 2 min to 1 min and change your memory usage while computer is in use up by 5%.  Hit the update button and head back into boinc manager.  Select SETI on projects tab, click UPDATE.  Check messages tab and you should get something about 'new preferences from SETI on today's date, a few minutes ago'.  exit the manger, restart the daemon, open up the gui manager again. Check to see that the memory allowed for usage while user is active did in fact go up by 5%.  Check Tasks tab... hoping you will now see tasks suspended - user active.

My theory (well, maybe better, wild *** guess) is that since WCG is not a 'true' boinc project as it it does not really operate on a 'normal' boinc server it may not pass preferences correctly to your client (I know there are some issues with it and using a boinc account manager, such as it will not accept an resource change from the BAM).  I am hoping by making SETI (nearly always the most current version of the server side software) the 'holder' of your preferences they will get passed to your client better.

Well I said it's a shot.  

Lemme know, Skip

---

### Post by utkjamie on 2008-06-12
No luck. The BOINC Manager retrieves the SETI@home settings but doesn't recognize that the computer is in use. I don't know what has changed recently to cause this problem because it's never seemed to be a problem before. At least BOINC appears to be playing nice with the CPU cycles so that I really don't notice that it is running while I am using the computer but it frustrates me nonetheless because it isn't working the way it supposed to. Argh. ;-)

---

### Post by Skip Da Shu on 2008-06-12
> **utkjamie said:**
> No luck. The BOINC Manager retrieves the SETI@home settings but doesn't recognize that the computer is in use. I don't know what has changed recently to cause this problem because it's never seemed to be a problem before. At least BOINC appears to be playing nice with the CPU cycles so that I really don't notice that it is running while I am using the computer but it frustrates me nonetheless because it isn't working the way it supposed to. Argh. ;-)

Is your keyboard/mouse PS2, USB or wireless of any fashion?

Yea with the default install and the 'child rescheduling' it does appear to be very low impact in background now.

---

### Post by utkjamie on 2008-06-13
> **Skip Da Shu said:**
> Is your keyboard/mouse PS2, USB or wireless of any fashion?

No, this is a laptop.

---

### Post by Skip Da Shu on 2008-06-13
> **utkjamie said:**
> No, this is a laptop.

Sorry, I had missed that.  I'd read that some laptops required some  configuring of power monitoring or something to get BOINC to recognize non-use but I'm afraid I don't know any more about that.  

You might try the forums on Berkeley's site.  Sorry, Skip

PS: BTW, on my 'work' laptop (winxp) I don't have it suspend on activity but I run Threadmaster to limit it's CPU usage during the day (mostly for heat reasons).  However Threadmaster works quite a bit differently than the 'throttling' that's built into the newer BOINCs.

---

