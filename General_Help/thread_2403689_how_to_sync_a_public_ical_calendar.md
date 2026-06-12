---
title: "how to sync a public ical calendar"
date: 2018-10-15
forum: General Help
---

### Post by slbsnl on 2018-10-15
Hello,
I try to add a public Google calendar to my Ubuntu calendar (3.28.2), but after adding the link the app keeps on asking for a password... anyone can help please?

---

### Post by speartip on 2018-10-15
How are you adding the calendar?
As far as I know, you need to Log into your Google account online. Add the calendar on googles official Calendar app, then add a new calendar that way. It should then show up in your Ubuntu Calendars.

edit... I've just tried it & it works fine that way.

---

### Post by slbsnl on 2018-10-15
I'm adding the calendar with the 'public ical' link from Google calendar. I do not want to add this account to Ubuntu (it isn't even my account).

---

### Post by speartip on 2018-10-15
So from within Google. Clicking "Add other Calendars" / "From URL". Then copy/pasting the Calendar Address does not work?
Please be step by step specific with what you have tried.

---

### Post by slbsnl on 2018-10-15
I tried:
- go to agenda settings
- add through URL
- enter the path of the public calendar
- app asks me for a user/pass

---

### Post by speartip on 2018-10-15
Is it just asking for your Google password?
Have you tried doing it through the Google Calendar app as in my previous post?

---

### Post by slbsnl on 2018-10-15
I don't know, it just says 'login:' and 'password:'....

This is not my Google account, it is a calendar the owner wants to share with me. So I can't add the Google account to my Ubuntu install

btw, the public link works fine in my Nextcloud web calendar, and also on the calendar app I use on my Android phone

---

### Post by speartip on 2018-10-15
I've never done this, but as far as I know, you can only add someone else's Public Google Calendar to your account, from within you're own Google account, using the steps I posted above from within your Google Calendar.
It should then show up in your Calendar within Ubuntu, as long as your logged in to Google through your "online accounts"

---

### Post by slbsnl on 2018-10-15
There are a lot of public ical's with national holiday's or footbal competions, for example:
[COLOR=#333333][FONT=&quot]https://www.google.com/calendar/ical/spielplan.1.bundesliga%40gmail.com/public/basic.ics 

Adding this to the nextcloud web calendar: works fine
Adding this to my Android calendar app (not Google calendar): works fine
Adding this to the Ubuntu GNOME calendar: nothing happens (no password needed, just nothing happens)

Btw, I tried to ad a Google calendar with the 'secret ical' link Google provides.. so strictly spoken the calendar is not public. But same thing, it works fine in every app exept Ubuntu calendar[/FONT][/COLOR]

---

### Post by slbsnl on 2018-10-15
> **speartip said:**
> How are you adding the calendar?
As far as I know, you need to Log into your Google account online. Add the calendar on googles official Calendar app, then add a new calendar that way. It should then show up in your Ubuntu Calendars.

edit... I've just tried it & it works fine that way.
Ok I tried this also
Had to reactivate my Google account for it ;)
Now the calendar show up in calendar.google.com under 'other calendars', I added my Google account to Ubuntu Calendar, but the shared calendar does not show up....

---

### Post by speartip on 2018-10-15
No. You're right. I just tried with the Calendar from your link. Works fine online with Google, but doesn't appear in the Gnome Calendar list.
It seems that Gnome Calendar is at fault.
[https://gitlab.gnome.org/GNOME/gnome-calendar/issues/287](https://gitlab.gnome.org/GNOME/gnome-calendar/issues/287)

---

### Post by speartip on 2018-10-15
Just a crude workaround you might be interested in. If you use an email client like Thunderbird, I tried adding the Calendar from your link & it works fine, as long as you have xul-ext-lightning installed.

---

