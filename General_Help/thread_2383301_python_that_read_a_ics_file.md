---
title: "python that read a ics file"
date: 2018-01-23
forum: General Help
---

### Post by cazz on 2018-01-23
Hi
I have install icalendar lib from here
[http://icalendar.readthedocs.io/en/latest/](http://icalendar.readthedocs.io/en/latest/)

and I have search and have find some example but have almost never got it to work.

I just want to print out to a textfile todays event from a ics file

---

### Post by slickymaster on 2018-01-23
*Thread moved to **General Help**.*

---

### Post by cazz on 2018-01-23
Have almost got it to work

```
from icalendar import Calendar, Event
g = open('file.ics','rb')
gcal = Calendar.from_ical(g.read())
for component in gcal.walk():
    if component.name == "VEVENT":
        print "---------------------------------"
        print component.get('summary')
        print component.get('dtstart').to_ical()
        print component.get('dtend').to_ical()
g.close()
```

---

