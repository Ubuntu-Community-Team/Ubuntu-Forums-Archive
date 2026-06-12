---
title: "Evolution shared salendar help (caldav)"
date: 2007-06-28
forum: General Help
---

### Post by LuckyDevil on 2007-06-28
Hello

For some reason, I don't seem to be able to get my shared calendar working with Evolution.

I have a webdav directory setup with a test.ics file.  I can access the directory fine, and I've been able to use the calendar correctly with mozilla-sunbird.  However, I'd really like to setup in Evolution as that is my preferred client.

When I setup new calendar, choose caldav, enter address, the calendar is added to my calendars under CALDAV group in evolution.  But when I check it to enable it, it quickly says "Getting calendar..." or something of the sort, then the box is unchecked.  So I can't enable it...

I saw one other user (with FC4, i believe) having the same issue when I googled it, but he had no resolution.

Any ideas?

Also, does anyone know of a good web application to view/edit iCalendars?  The goal is to have the same calendar synced between evolution and a web calendar to view when away from my pc.  I've tried phpicalendar and webcalendar.  PHPiCalendar doesn't allow me to add events, allow view.  Webcalendar doesn't really sync with that iCal file, it just loads the events in and adds it to the calendar...so I have to reload the webdav ics file every time I view the calendar.


Thanks a lot for any help!

Rich

---

### Post by nocturn on 2007-06-28
> **LuckyDevil said:**
> Hello

For some reason, I don't seem to be able to get my shared calendar working with Evolution.

I have a webdav directory setup with a test.ics file.  I can access the directory fine, and I've been able to use the calendar correctly with mozilla-sunbird.  However, I'd really like to setup in Evolution as that is my preferred client.

When I setup new calendar, choose caldav, enter address, the calendar is added to my calendars under CALDAV group in evolution.  But when I check it to enable it, it quickly says "Getting calendar..." or something of the sort, then the box is unchecked.  So I can't enable it...

I saw one other user (with FC4, i believe) having the same issue when I googled it, but he had no resolution.

Any ideas?

Also, does anyone know of a good web application to view/edit iCalendars?  The goal is to have the same calendar synced between evolution and a web calendar to view when away from my pc.  I've tried phpicalendar and webcalendar.  PHPiCalendar doesn't allow me to add events, allow view.  Webcalendar doesn't really sync with that iCal file, it just loads the events in and adds it to the calendar...so I have to reload the webdav ics file every time I view the calendar.


Thanks a lot for any help!

Rich

WebDav is not CalDav.  Evolution can read calendars on WebDav, but not write them.
CalDav is supported fully, though it is still quite rough as there are very few servers that support it.

---

