---
title: "Evolution and Palm Sync"
date: 2005-03-22
forum: General Help
---

### Post by scottish on 2005-03-22
I'm using Ubuntu 5.04, Evolution 2.2.1.1 and a Palm T3 and I've the following problem.
I've sync my Palm and Evolution for several days without any problems. Today I ad a task in Evolution and sync. After syncing I've more than 3000 empty tasks in Evolution and on my Palm. About 2990 more then before. I delete the 2990 tasks and sync again. After syncing I've 10 tasks in Evolution and 3000 on my Palm. With other words, the ToDo conduit didn't sync anymore.
On the Palm I deleted the todo database and set in pilot settings the sync action to sync to palm. Sync again but without any results. Everything I do give the same result, the ToDo conduits didn't sync anymore.

Is there anyone wth the same problem and is there a solution?

Thanks,

Harry

---

### Post by Leif on 2005-03-22
I can only commiserate. I haven't been able to get tasks working properly either, getting hundreds of duplicates, crashes and all, so I've disabled the task conduit.

---

### Post by nocturn on 2005-03-23
[QUOTE=scottish]I'm using Ubuntu 5.04, Evolution 2.2.1.1 and a Palm T3 and I've the following problem.
I've sync my Palm and Evolution for several days without any problems. Today I ad a task in Evolution and sync. After syncing I've more than 3000 empty tasks in Evolution and on my Palm. About 2990 more then before. I delete the 2990 tasks and sync again. After syncing I've 10 tasks in Evolution and 3000 on my Palm. With other words, the ToDo conduit didn't sync anymore.
On the Palm I deleted the todo database and set in pilot settings the sync action to sync to palm. Sync again but without any results. Everything I do give the same result, the ToDo conduits didn't sync anymore.

Is there anyone wth the same problem and is there a solution?

Thanks,

Harry[/QUOTE]

I have similar problems on Warty. (Thousands of empty TODO items)

---

### Post by mike998 on 2005-03-23
I hate to say it, but me too.
I can get my contacts to sync but I can't get anything else to sync.

---

### Post by rorzer on 2005-06-22
hoary, evolution 2.2.1.1, gnome-pilot 2.0.12-1.1ubuntu4, Palm Vx

Same problem.  Seems to mostly happen when I haven't modified any tasks on evolution between syncs.  Also when a task is deleted on evolution.

Is anyone working on this?  Has it been properly listed as a bug?

---

### Post by nbcthreat on 2005-08-23
Jpilot could be a stopgap solution until this starts working.
Multisync is also an option.

---

### Post by nocturn on 2005-08-24
Me too, the problem already existed in Warty (but less frequent).  It worked fine on Gentoo though.

I can most of the time recover by deleting the fakes on Evolution and set one time sync to 'copy to pilot'.  After a couple of syncs, the problem returns.

---

### Post by Niiico2 on 2005-08-25
Well, I have the same problem  :(

---

### Post by mattruby on 2005-09-29
I'm also running Ubuntu5.04/Evolution2.2.1.1, with a (USB) Treo 600. I just want to sync my Treo and Evo contacts/calendars. I had contacts working (mostly) and calendars (a little) at first, but have lost ground. Contacts got corrupted (many duplicates, lost contacts, all phone#s lost but one which was put into "Email"). Calendar synced one item per day max from Treo to blank Evolution, then wouldn't sync again. That was when it was "working".

I reinstalled Evolution, multisync, conduits, and now can't even get Multisync to read my username/id from the Treo in its config. And Multisync routinely deletes the /dev/ttyUSB* symlinks I make to Ubuntu's /.dev/ttyUSB* files, and changes group or other metadata on new device nodes I make in /dev after deleting the /.dev ones. What is that /.dev dir anyway?

Is there a simple How-To from scratch I can use to just get these items to sync? Multisync looked like the way to go, but I don't care. I just want to press the Sync button on the Treo and share the calendar/contacts with Evolution. Why is that so elusive?

---

### Post by jdkron on 2005-09-29
I've never had success either with my treo 600 so I just use Jpilot which certainly is no frills but seems very dependable and gets the job done.

I'd love it if the issue was resolved though.

---

### Post by Foaming Draught on 2005-10-06
Same here. Palm synching is a killer app for me, and Evolution or gnome-pilot (don't know which is the culprit) just still does not work. Tasks appear in unsorted order in calendar view and panel-clock-dropdown, annual repeating events (eg birthdays) randomly spread over 2 days, gnome-pilot or evolution almost always crashes before a synch is complete  -  I could go on.
JPilot doesn't look very swish, but it works flawlessly every time with pilot-link.
I use Thunderbird mail.
Interestingly, multisync works flawlessly between Evolution contacts (I've disabled the useless calendar and task list) and my Sony-Ericsson K750i.
 The upshot? I use Evolution contacts for backing up my mobile phone and for the useful panel drop-down and for phone-manager sms numbers, but JPilot as my desktop calendar and for synching with my Palm.

---

