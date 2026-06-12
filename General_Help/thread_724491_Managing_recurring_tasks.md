---
title: "Managing recurring tasks"
date: 2008-03-14
forum: General Help
---

### Post by Joe Jarvis on 2008-03-14
Does anyone know a program for managing recurring tasks?  I'm desparate for a program to help me manage chores and maintenance, e.g., do X chore every Monday or do Y maintenance once per year?

I was recently shocked to discover that neither Evolution nor Sunbird support recurring tasks.  Evolution just outright doesn't (not sure how people don't consider this a critical feature gap), and Sunbird let's you create them, but when you complete a task, it doesn't automatically generate the next instance of the task.

Sunbird and Google Calendar support recurring events, but I don't want to pollute my calendar.  Besides, many of my tasks don't have due dates, so a calendar view would only show the event on the day it appears, not afterward; I would have no way to see outstanding incomplete tasks.

I looked at GNOME Planner and OpenProj, but they're more about project and resource planning and use.

I feel like I must be missing something obvious since this seems like such a basic functionality that lots of others would need.  Thanks.

---

### Post by HermanAB on 2008-03-14
Well, cron of course.

Basically, you need to write a little script and put it in /etc/cron.hourly, /etc/cron.daily, weekly, monthly, yearly whatever...

You can also run a script at whatever time and date you please using crontab.

...and yes, you need to Google and read up on cron a bit, but it isn't rocket science.

Cheers,

Herman

---

### Post by Joe Jarvis on 2008-03-14
> **HermanAB said:**
> Well, cron of course.

Basically, you need to write a little script and put it in /etc/cron.hourly, /etc/cron.daily, weekly, monthly, yearly whatever...

You can also run a script at whatever time and date you please using crontab.

...and yes, you need to Google and read up on cron a bit, but it isn't rocket science.

Cheers,

Herman

Thanks Herman.  I'm familiar with cron, but I'm not sure this will help.  To clarify, I'm not talking about maintenance on a computer, but rather real-world chores/maintenance, like remembering to change my furnace filter or go to the dentist.  I'm looking for something simple with a GUI and some kind of alarm and summary view/checklist.

---

### Post by centyx on 2008-04-01
I feel the same way. You may want to file a bug/enhancement report at bugzilla.mozilla.org wrt sunbird's recurring task behavior. 

I have just begun using Sunbird and was also disappointed that the recurring instances disappeared after I completed the first instance of the task. I modified the task and they appeared, but the upcoming tasks were "hidden" because I had checked "hide completed tasks." 

Please post here if/when you do find a viable solution.

Thanks!

---

### Post by centyx on 2008-04-02
Sunbird's recurring tasks feature appears to work to my satisfaction in 0.8. You should check it out.

---

### Post by Joe Jarvis on 2008-04-07
> **centyx said:**
> Sunbird's recurring tasks feature appears to work to my satisfaction in 0.8. You should check it out.

I was using version 0.5 from the Gutsy repositories.  Per your post, I tried 0.7 from the Hardy development repositories and then 0.8 from Mozilla directly.  In all three versions, whenever I mark a  task complete, Sunbird does not generate the next instance of the task.  How are you using 0.8 successfully?  Am I missing something obvious?  Thanks.

---

### Post by Joe Jarvis on 2008-04-07
> **centyx said:**
> I feel the same way. You may want to file a bug/enhancement report at bugzilla.mozilla.org wrt sunbird's recurring task behavior.

It appears that several developers are aware of the issue (for example, Mozilla bugs [155889]("https://bugzilla.mozilla.org/show_bug.cgi?id=155889") and [373775]("https://bugzilla.mozilla.org/show_bug.cgi?id=373775")).  It's just frustrating as an end-user that the issue is still unresolved.

---

### Post by niteshifter on 2008-04-07
Hi,

True, Evolution does not have recurring tasks. It does have recurrence in Calender - and you can have more than one Calender.

---

### Post by Joe Jarvis on 2008-04-07
> **niteshifter said:**
> [Evolution] does have recurrence in Calender - and you can have more than one Calender.

Thanks for the suggestion.  As I mentioned in the first post, I had looked into recurring events as a workaround.  It's a pretty kludgy solution.  I can't designate an item complete.  Many of my tasks have start dates only, and there's no way to make an event open ended until it's complete.  And if a task is overdue, there's no way to tell; it only appears on the day it's due.

Paradoxically, support for recurring appointments seems common.  Besides Evolution, Sunbird and Google Calendar support them too.  I'm not deep into development, but I don't understand why the code for recurring events couldn't be adapted for recurring tasks.

---

### Post by Joe Jarvis on 2008-04-07
> **centyx said:**
> You may want to file a bug/enhancement report at bugzilla.mozilla.org wrt sunbird's recurring task behavior.

I noticed the Evolution bug you filed on this today.  Thanks for the effort.  If finding the right bug were easier, I think a lot more end users would comment.  For the benefit of others, I thought I'd post the relevant (eight year old!) bug:[ #200907]("http://bugzilla.gnome.org/show_bug.cgi?id=200907").

---

### Post by r m h on 2008-04-07
I'm searching to see if xvtdl has been ported from OpenWindows.

If it has been ported it will meet your needs.  I used it well over a decade ago on different architectures and unices.  Here's an excerpt from the .readme I have:

   * You can manage multiple todo lists; lists can have sublists.
   * Each todo list item is prioritized; each list can be displayed in 
     a combination of priority, chronological, and alphabetical 
     order.
   * List items, if you do not "check them off", will propagate from 
     one day to the next.  
   * List items can be recurring items, i.e., items that will 
     automatically pop up weekly, biweekly, monthly, etc.  These items
     will propagate like "normal" list items.
   * List items can have deadlines associated with them, with several
     types of actions that execute on or after a deadline.
   * List items can have annotations associated with them.  Annotations
     are edited with a "normal" text editor.
   * You can set list items on any day, with easy calendar management.
   * Lists can be printed on a "plain" or Postscript printer.
   * Printing/display supports ISO 8859.1 character set.
   * List items can be logged when checked on/off with optional comments
     added to the log file.
   * List items can be retained or deleted when checked off. 
   * Multiple lists can be combined for viewing or printing.
   * Multiple lists from multiple files can be manipulated.
   * Changes to the todo list can be made and are detected by the running
     programs.


Update:  
XView libraries needed for xvtdl appear to have been ported to Linux.  See [http://www.physionet.org/physiotools/xview/](http://www.physionet.org/physiotools/xview/)
Next get the xvtdl-5.2msj.tar.gz sources from [http://step.polymtl.ca/~coyote/XView/apps/xvtdl/](http://step.polymtl.ca/~coyote/XView/apps/xvtdl/) 
Then, you *should* be able to compile it against the XView libraries

If I get some free time in the next day or two I'll try and get this built on my Ubuntu 64-bit Gutsy install on my T61p.

Hope this helps

---

### Post by GJDitchfield on 2008-04-08
The KDE PIM suite supports recurring tasks.  The KOrganizer package contains the task editor.  Kontact is a shell that embeds the other PIM programs, and it has a Summary page that can display uncompleted tasks.

---

