---
title: "alarms in evolution 2.22.1.1 on Hardy - wrong time"
date: 2008-06-04
forum: General Help
---

### Post by midgemiles on 2008-06-04
I am in timezone Australia / Brisbane.  The alarm notification for appointments in evolution reports the appointment time at 14 hrs earlier than the time set in the evolution calendar.  I have set timezone in both Ubuntu and Evolution to GMT+10.00, but the appointment alarms seem to be working to another time!

Ubuntu Hardy Heron, Evolution 2.22.1.1

Any Ideas? :(

---

### Post by shaggorama on 2008-12-08
Hi,

I'm super green to this whole ubuntu thing, so I can't really give you any useful thuoghts on what's causing your problem, but I did have the same problem and managed to fix it by accident (intrepid ibez, close enough):

For some reason, My clock in general would default to california time, even when I adjusted the time. it would flip back to california upon restart and my appointment times would always be set to cali time even though I had set a different appointment time than was displayed.

My permanant fix to the clock issue was setting the computer time with the command 'sudo dpkg-reconfigure tzdata' and then configuring to my time zone. The appointments just clicked back to what they're supposed to be. 

Don't know if this will work for you, but i was pleasantly surprised myself!

---

### Post by midgemiles on 2009-03-17
Hi,
thanks for your reply, and sorry not to have seen it earlier.  The problem fixed itself, but the general issue of syncing phone and evolution calendars remains a touchy one.  I also tried and had working for a while syncing evolution calendar with an online google calendar that I share with my family so they know what my schedule is in case I forget to actually tell them - using gcaldaemon.  Then it stopped working properly.  gcaldaemon isn't officially supported by Ubuntu, so maybe I have failed due to lack of appreciation of the finer points of configuration etc.

---

