---
title: "Evolution reminders wrong timezone"
date: 2005-06-23
forum: General Help
---

### Post by DoomedTX on 2005-06-23
I am using Evolution 2.2.1.1 and have trouble with my reminders. The system timezone is set correctly and Evolution's timezone is set properly as well. When I schedule an appointment with a reminder, the reminder always shows the appointment time as 4 hours earlier (we are GMT-4 here). For example, I have an all-day appointment next week with a 1-week reminder. Tonight at midnight a reminder popped up saying I had an appointment from next Tuesday at 2000 to next Wed at 2000 instead of Wed 0000-2359. It's almost as though Evolution is taking the system time, which is already corrected to the Eastern Time Zone, and applying the correction a second time. I had this same trouble in Mandrake but thought it was supposed to be fixed in the later versions of GNOME that we enjoy in Ubuntu.

Anyone else experiencing this?

---

### Post by intangible on 2005-06-24
Did it grab the correct Time Zone for your computer?  Check under "**Edit->Preferences->Calender and Tasks->Time zone"?**

---

### Post by DoomedTX on 2005-06-24
Yes, as I mentioned Evolution's timezone is set correctly under the calendar preferences. Oddly enough, it seems that appointments at a specific time are shown correctly, but all-day appointments are not. Curiouser and curiouser.

---

### Post by intangible on 2005-06-26
[http://bugzilla.gnome.org/show_bug.cgi?id=304278](http://bugzilla.gnome.org/show_bug.cgi?id=304278)

Look at all the related bugs as well, this seems to be an issue with Evolution

---

