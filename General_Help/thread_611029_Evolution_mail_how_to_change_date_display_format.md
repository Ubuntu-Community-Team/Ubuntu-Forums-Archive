---
title: "Evolution mail: how to change date display format"
date: 2007-11-12
forum: General Help
---

### Post by rpinwelly on 2007-11-12
I have set the time format in Calendar & Task Preferences to  24 hours.  However, Evolution displays the date as "yesterday, 6.50 AM", "today, 3.45 pm", and older mail as "Nov 05, 8.07pm".  that is a really irritating and inconsistent format :( 

How do I get Evolution to display date and time consistently in the following format: 

dd/mmmm/yy,  followed by time in 24 hour format.

Thanks for any suggestions!

---

### Post by rpinwelly on 2007-11-13
Any takers? Help would be greatly appreciated!:)

---

### Post by vanadium on 2007-11-15
I think the short answer is that you can't. Evolution takes the settings from your locale (Syatem - Administration - Language). There seem few possibilities to customize a system wide locale either, alt least from within the gnome graphical tools.

---

### Post by DrDaveHPP on 2007-11-18
This doesn't seem to be the case with my Gutsy setup. My login screen gives the time and date in UK format (19 Nov 2007, 11:09). (Mind you, this is progress: up until a recent update (last week?) my login screen was displaying time and date in US format (Nov 19 2007, 11:09 AM).) However, when I open Evolution my emails are listed using 12-hour clock times, although dates appear in UK order (day-month-year). So something's still not quite right.

---

### Post by rpinwelly on 2007-11-19
Thanks guys; no progress here either - looks like I'll just have to live twith this for the time being.

---

### Post by damko on 2007-12-27
same problem here.
As far as I know this a very old issue. 
evolution's date format is hardly linked to the system settings. in my opinion it's not a great idea.

anyway there is a trick helpful for some situation described [here]("http://mail.gnome.org/archives/evolution-list/2006-December/msg00049.html")

try this: 
open a terminal as a common user and type

```
LANGUAGE=it_IT.UTF-8 LC_TIME=it_IT.UTF-8 /usr/bin/evolution
```

your view will have the italian date standard and will be localized in italian

I know that it's not what u r searching for ... but maybe it will be helpful

enjoy
Dam

---

### Post by damko on 2007-12-27
I wrote an email to the evolution mailing list, just to know if they plan to modify the customization of the view
[URL="http://mail.gnome.org/archives/evolution-list/2007-December/msg00115.html"]
http://mail.gnome.org/archives/evolution-list/2007-December/msg00115.html[/URL]

---

