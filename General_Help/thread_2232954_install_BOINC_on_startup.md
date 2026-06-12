---
title: "install BOINC on startup ?"
date: 2014-07-05
forum: General Help
---

### Post by sarahfoxnz on 2014-07-05
Hello.

i've installed BOINC. & the SETI project.

this runs fine when i remember to turn it on :)

Is there a way to automatically start BOINC when Ubuntu starts up ? (even in background - before i even  log in / another user logs in.)

thank you

---

### Post by Gyokuro on 2014-07-05
Hi

You can start boinc as a service (at start up) therefore you should edit: /etc/default/boinc-client in case you are using the packaged version and search for the line:

#BOINC_CLIENT="/usr/bin/boinc"

delete the #sign and change the location of above boinc application wherever you have installed/copied your boinc. Later you start the service:

sudo /etc/init.d/boinc-client start 

- HTH

---

### Post by sarahfoxnz on 2014-07-06
Cool. thanks.

i've done that now - it appeares to be working as i just found this command :-

> 

service --status-all

[ + ]  boinc-client



just 2 more queries (i can ask in the BOINC forum if not appropriate here)

1) How do i limit the number of 'tasks' or packages that are downloaded & to be processed ?

According to BOINC, i've got 75 tasks pending.  (would take me 2-3 weeks to process)

[http://setiathome.berkeley.edu/results.php?hostid=7318427](http://setiathome.berkeley.edu/results.php?hostid=7318427)

2) Is there a special process / programme that i can run, to check on the status of my BOINC service. Do i just run the usual BOINC client - Would that open a  separate process than my 'hidden service' ? (hopefully this makes sense)

---

### Post by QIII on 2014-07-06
Hello!

You can use the BOINC manager to adjust the settings (not at home right now or I'd walk through it with you) or you can do it online with BOINC.  If you only want to commit a small percentage of your computing time, you can reduce it.  Also, your BOINC projects are given a lower priority than what you are doing with your machine, so it won't get in the way of other use.

You will get loaded up with several weeks' worth of work to begin with and will get new tasks as they are completed.  It is a rolling process.  You can keep from adding new tasks by highlighting the project and selecting something like "Do not accept more tasks."  But the point is it's a continuous process.

You can abort tasks if you wish with the BOINC manager.

You can check your stats under one of the tabs in the GUI.

---

### Post by sarahfoxnz on 2014-07-08
Further to my issue: 

I've tested the BOINC system on my computer.

> 
 /etc/init.d/boinc-client status
 * Status of BOINC core client: running
 * Scheduling of BOINC core client: 6994
pid 6994's current scheduling policy: SCHED_OTHER
pid 6994's current scheduling priority: 0
 * OOM killer status for BOINC core client:
PID 6994: adj 0
, score 
2


[http://boinc.berkeley.edu/wiki/Stop_or_start_BOINC_daemon_after_boot#Linux_.28in_general.29](http://boinc.berkeley.edu/wiki/Stop_or_start_BOINC_daemon_after_boot#Linux_.28in_general.29)

However i'm not sure what this status means. (i'm guessing it means BOINC is running / going - but not documented in the wiki as to what the results mean ).

Question:

How do i find out  if its actually processing anything,   10%, 20% - 80% etc processing of a work unit ?

how many work units have i downloaded/uploaded ?

The last contact i had with SETI - is 6th July (2 days ago).  - [http://setiathome.berkeley.edu/show_host_detail.php?hostid=7318427](http://setiathome.berkeley.edu/show_host_detail.php?hostid=7318427)

This contact was before I installed BOINC as a service.

[http://setiathome.berkeley.edu/results.php?hostid=7318427](http://setiathome.berkeley.edu/results.php?hostid=7318427)

(or shall i post this part of my query on a BOINC forum instead ?)

EDIT: i manually sent the "update" - I opened the visual / display of BOINC (i thought it opened up a NEW BOINC session, but it did update all my processing i've done - assuming from the service.)

Only issues now

a) is there a way to auto-update - automatically,  daily ? 

b) How to see the status of the current work - without updating to the server

- Work units on hand
- how many i've got processed
- the status of the "current" work unit (34% done, 87% done etc...)

---

### Post by oldos2er on 2014-07-08
You can view some of the info you want in Boinc manager ```
boincmgr
``` or by logging in to the Seti@Home website. If there is a way to show the info you want in a terminal (and there may or may not be, I don't know), I'd be interested in hearing about it if you find anything.

---

