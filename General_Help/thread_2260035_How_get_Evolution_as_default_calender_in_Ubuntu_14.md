---
title: "How get Evolution as default calender in Ubuntu 14.10?"
date: 2015-01-08
forum: General Help
---

### Post by petermartin2 on 2015-01-08
I've read somewhere that Evolution is supposed to be the default calender of Ubuntu however it did not seem to be included in my distro. I have not removed it and it was not installed so I installed it from Ubuntu Software Center. However when I search for it in unity dash it does not appear after installation. Also it is not an option as calender under system settings -> details -> Default Applications. Right now I have put Orage Calender there but it dosen't do anything, I can't add events or anything. Anyone know how I could install Evolution properly as the default calender?

---

### Post by ian-weisser on 2015-01-09
Make sure you have the following packages installed:
- indicator-datetime (the Unity clock & calendar AppIndicator)
- evolution-data-server (the calendar database, part of Evolution)

In Evolution, make sure you create at least one Calendar to use...or import an .ics file, or a Google Calendar, etc.
Put in a couple dummy events if creating a new calendar in Evolution.
Once the database has a calendar with events, those events should show up automatically in the AppIndicator drop-down calendar. Nothing to click or send. The applications talk to EDS automatically.

---

### Post by petermartin2 on 2015-01-09
I've run
sudo apt-get install --reinstall indicator-datetime
and evolution-data-server is installed according to ubuntu software center but no change. Evolution appears installed in software center but won't appear in dashsearch and when I search the ubuntu drive only seven documents called "evolution"-something are found

---

### Post by buzzingrobot on 2015-01-09
Evolution is a large and complex suite of tools, but basically a mail program that also provides calendaring. Many distributions, including Unity, use its calendaring bits. Those are (or should have been) installed by default in Unity.  The mail components are not installed by default in Unity, where the default mail client is Thunderbird.

The Evolution package you installed provides the mail client.

Make sure you have the Default Applications set appropriately (Systems Settings->Details).

---

### Post by petermartin2 on 2015-01-09
> **buzzingrobot said:**
> Evolution is a large and complex suite of tools, but basically a mail program that also provides calendaring. Many distributions, including Unity, use its calendaring bits. Those are (or should have been) installed by default in Unity.  The mail components are not installed by default in Unity, where the default mail client is Thunderbird.

The Evolution package you installed provides the mail client.

Make sure you have the Default Applications set appropriately (Systems Settings->Details).

It's just the only Calendar option that comes up in sys settings -> details is orage calendar. I can't change it. But what can Evolution do I basically want a Calendar I can open up and add events and stuff. There is a calendar up in the right corner but it dosen't do anything no matter where I click except show the dates and time

---

