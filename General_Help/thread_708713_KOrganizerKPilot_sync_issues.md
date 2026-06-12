---
title: "KOrganizer/KPilot sync issues"
date: 2008-02-26
forum: General Help
---

### Post by CSMatt on 2008-02-26
KOrganizer is great, although KPilot seems to need its settings changed before every sync.  However there seems to be a problem.  When I sync my appointments and tasks to my Palm Z22, the Location fields don't sync.  When I check off a completed task on the PDA that wasn't checked in KOrzaniser, KPilot/KOrganizer makes a duplicate of the completed task instead of updating the one already in the calender.  Also, when I delete a recurring event from the PDA, KPilot completely ignores the deletion and it isn't reflected in KOrganizer.

Is there any way I can fix this?

---

### Post by CSMatt on 2008-02-28
Bump.

---

### Post by premodern on 2008-02-29
]
Similar problem here with my Tungsten E2. After the sync My tasks are duplicated in KOrganizer and the calendar entries are duplicated both in Korganizer and in my Palm. This is very annoying. Hope there is a fix to this.

---

### Post by premodern on 2008-02-29
The other funny thing is, when I try to delete one of the extra To-do entries, I cannot select one of the duplicates. When I choose one, the other is automatically selected.

---

### Post by premodern on 2008-02-29
:guitar:

I have found a solution:

System settings -> Advanced -> KDE resources 

Remove the duplicate Default Korganizer resources entry there. !

Also in the Korganizer settings, do not choose "standard calendar" etc but the file below it.

---

### Post by CSMatt on 2008-03-09
What are the instructions for GNOME users?

---

### Post by CSMatt on 2008-03-17
Bump

---

### Post by YosemiteSam on 2008-05-07
**For GNOME users** "System Settings > Advanced > KDE resources > Calendar" is not available. Instead open Kontact, click on Calendar to display the calendar view, go to Settings > Sidebar and make sure Show Resource View is selected.  Then you should see the Calendar Resources on the left sidebar with two Default KOrganizer resource entries. Delete the second one and this should fix the duplicate to-do problem.

---

