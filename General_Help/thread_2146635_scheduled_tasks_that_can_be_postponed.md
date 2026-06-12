---
title: "scheduled tasks that can be postponed?"
date: 2013-05-19
forum: General Help
---

### Post by EntropyReduction on 2013-05-19
I've been working on a utility for my own use, wonder if it would be of more general interest.

Basic idea is an action that should be run every so many days.  But the task might be intrusive; might require my intervention, or use substantial resources.

So I run a programme once a day that keeps a database of such tasks.  It pops up a reminder when something's due; if I click ok, it does it, and updates "LastDateRun" for the item.

If I click "postpone", same item comes up next day, when the programme runs again.  

Of course if I'm busy I can also keep the reminder message box on screen, and click it later on when I've got a mo.

Lot's of bells and whistles, but that's the essence.

So far I have a crude version in bash (using a csv file) and a fancier version in progress in python (using an ini file).  

So:  (a) am I reinventing the wheel?  Can this already be done with an existing programme?  (b)  would programme be of use to others?

---

### Post by Zill on 2013-05-19
> **EntropyReduction said:**
> ...So:  (a) am I reinventing the wheel?  Can this already be done with an existing programme?  (b)  would programme be of use to others?
This functionality already exists in some, if not all, existing calendar applications.

For example, I currently use [ReminderFox]("http://www.reminderfox.org/"), which is a Firefox add-on.  This has many of the attributes you have suggested, including setting tasks ([reminders]("http://www.reminderfox.org/documentation-userguide-reminders/")) with repeat options defined by the number of days, weeks, months etc.  This can then give reminders on a regular basis until the task is completed.  HTH.

---

### Post by EntropyReduction on 2013-05-22
> **Zill said:**
> This functionality already exists in some, if not all, existing calendar applications.

For example, I currently use [ReminderFox]("http://www.reminderfox.org/"), which is a Firefox add-on.  This has many of the attributes you have suggested, including setting tasks ([reminders]("http://www.reminderfox.org/documentation-userguide-reminders/")) with repeat options defined by the number of days, weeks, months etc.  This can then give reminders on a regular basis until the task is completed.  HTH.

I just installed ReminderFox.  Very nice.  But unless I'm missing something, it can't be used to launch a task when you accept the reminder.   (A ReminderFox reminder can have a url associated with it, but as far as I could see there's no way to luanch that url when the reminder gets accepted?  Or ever, except from within the reminder editor?

I probably should have titled my question differently.  What I'm looking for is sort of cron/anacron but with user intervention.  Schedule a task, but ask before you run it.  Ask again if the offer to run refused.  

Another way to think of it: the task I'm scheduling is *an offer* to do something.  If the offer is refused, the task (offering) is resecheduled to run again.  

Alan

---

### Post by Zill on 2013-05-22
EntropyReduction:  Thanks for the clarification.  Unfortunately, I don't believe that ReminderFox, or probably any other calendaring application, will do what you want. :-(

These calendar-type applications simply show a *visual* reminder to do something at one or more specified times or intervals.  If the reminder requires an action then it is up to the user to do this manually.

I can't think of any existing application that will do what you wish but others may advise on this.  In my view, this would require considerable scripting and this is well beyond my capabilities. ;-)

Good luck and please keep us advised if you make any progress.

---

### Post by EntropyReduction on 2013-05-23
Hi Zill,

> **Zill said:**
> Unfortunately, I don't believe that ReminderFox, or probably any other calendaring application, will do what you want. :-(

These calendar-type applications simply show a *visual* reminder to do something at one or more specified times or intervals.  If the reminder requires an action then it is up to the user to do this manually.

I can't think of any existing application that will do what you wish but others may advise on this.

There's remind ([http://www.roaringpenguin.com/products/remind](http://www.roaringpenguin.com/products/remind), also in repositories); it will run a task, but no way to postpone (the man page is...rather complicated, I asked developer).

> **Zill said:**
> In my view, this would require considerable scripting and this is well beyond my capabilities. ;-)
Good luck and please keep us advised if you make any progress.

Well, as said I got a bash script that works, driven by csv file; I trigger it via cron to run every 20 minutes, which means it actually puts up invitations to run tasks within 20 minutes of first run each day; it remembers if it's already run (stored in .periodicLastRun file) that day and immediately quits every time it runs subsequently same day.  My python script, still under test, is driven from an ini file and has lots more options.  Both require proper documentation, but it anyone wants to see what I got already, let me know.

---

### Post by HiImTye on 2013-05-23
seems pretty decent, sounds like something I'd make with bash and zenity

---

### Post by Habitual on 2013-05-23
> **Zill said:**
> I currently use [ReminderFox]("http://www.reminderfox.org/"), which is a Firefox add-on.  This has many of the attributes you have suggested, including setting tasks ([reminders]("http://www.reminderfox.org/documentation-userguide-reminders/")) with repeat options defined by the number of days, weeks, months etc.  This can then give reminders on a regular basis until the task is completed.  HTH.an Excellent add-on!

---

