---
title: "Hardy - Sunbird 0.8"
date: 2008-06-20
forum: General Help
---

### Post by jeanjean84 on 2008-06-20
Hello everybody,

I have just installed Sunbird 0.8 on Ubuntu Hardy.
Sunbird is in /opt. It works fine except that I have an error when I start it: 

for example from a terminal:

```

$ ./sunbird
recurrence tweaking exception:TypeError: baseDuration has no properties
recurrence tweaking exception:TypeError: baseDuration has no properties
recurrence tweaking exception:TypeError: baseDuration has no properties

```

In Sunbird, the Error Console says: (I have replaced my details by 'xxxx' for obvious reasons!)

```

----------------------------------------------------------------------
Erreur : Assert failed: TypeError: Components.classes["@mozilla.org/calendar/calendar;1?type=" + type] has no properties
1: [file:///opt/sunbird/js/calUtils.js:1369] ASSERT
2: [file:///opt/sunbird/js/calCalendarManager.js:546] cmgr_createCalendar
3: [file:///opt/sunbird/js/calCalendarManager.js:690] cmgr_assureCache
4: [file:///opt/sunbird/js/calCalendarManager.js:666] cmgr_getCalendars
5: [null:0] null

Fichier source : file:///opt/sunbird/js/calUtils.js
Ligne : 1373
----------------------------------------------------------------------calendar/feeds/xx ... blic/basic): TypeError: cal has no properties
Fichier source : file:///opt/sunbird/js/calCalendarManager.js
Ligne : 712
----------------------------------------------------------------------
Erreur : Assert failed: TypeError: Components.classes["@mozilla.org/calendar/calendar;1?type=" + type] has no properties
1: [file:///opt/sunbird/js/calUtils.js:1369] ASSERT
2: [file:///opt/sunbird/js/calCalendarManager.js:546] cmgr_createCalendar
3: [file:///opt/sunbird/js/calCalendarManager.js:690] cmgr_assureCache
4: [file:///opt/sunbird/js/calCalendarManager.js:666] cmgr_getCalendars
5: [null:0] null

Fichier source : file:///opt/sunbird/js/calUtils.js
Ligne : 1373
----------------------------------------------------------------------
Erreur : Can't create calendar for 4 (gdata, [http://www.google.com/calendar/feeds/xx](http://www.google.com/calendar/feeds/xx) ... xxxx/basic): TypeError: cal has no properties
Fichier source : file:///opt/sunbird/js/calCalendarManager.js
Ligne : 712
----------------------------------------------------------------------
Erreur : Assert failed: TypeError: Components.classes["@mozilla.org/calendar/calendar;1?type=" + type] has no properties
1: [file:///opt/sunbird/js/calUtils.js:1369] ASSERT
2: [file:///opt/sunbird/js/calCalendarManager.js:546] cmgr_createCalendar
3: [file:///opt/sunbird/js/calCalendarManager.js:690] cmgr_assureCache
4: [file:///opt/sunbird/js/calCalendarManager.js:666] cmgr_getCalendars
5: [null:0] null

Fichier source : file:///opt/sunbird/js/calUtils.js
Ligne : 1373
----------------------------------------------------------------------
Erreur : Can't create calendar for 5 (gdata, [http://www.google.com/calendar/feeds/xx](http://www.google.com/calendar/feeds/xx) ... xxxx/basic): TypeError: cal has no properties
Fichier source : file:///opt/sunbird/js/calCalendarManager.js
Ligne : 712
----------------------------------------------------------------------
Erreur : Assert failed: TypeError: Components.classes["@mozilla.org/calendar/calendar;1?type=" + type] has no properties
1: [file:///opt/sunbird/js/calUtils.js:1369] ASSERT
2: [file:///opt/sunbird/js/calCalendarManager.js:546] cmgr_createCalendar
3: [file:///opt/sunbird/js/calCalendarManager.js:690] cmgr_assureCache
4: [file:///opt/sunbird/js/calCalendarManager.js:666] cmgr_getCalendars
5: [null:0] null

Fichier source : file:///opt/sunbird/js/calUtils.js
Ligne : 1373
----------------------------------------------------------------------
Erreur : Can't create calendar for 6 (gdata, [http://www.google.com/calendar/feeds/xx](http://www.google.com/calendar/feeds/xx) ... xxxx/basic): TypeError: cal has no properties
Fichier source : file:///opt/sunbird/js/calCalendarManager.js
Ligne : 712
----------------------------------------------------------------------

```

What can I do?
Please help!   ](*,) ](*,) ](*,)

---

### Post by fluteflute on 2008-06-20
Does sunbird 0.7 from the repos work for you?  [Install]("apt:sunbird")

---

### Post by jeanjean84 on 2008-06-20
Hello fluteflute,

Thanks for your reply!

No,  Sunbird 0.7 did not worked anymore (it used to, until recently...):

```
Erreur*: [Exception... "Component returned failure code: 0x804a0001 [calIIcalComponent.startTime]"  nsresult: "0x804a0001 (<unknown>)"  location: "JS frame :: file:///usr/lib/sunbird/js/calItemBase.js :: anonymous :: line 552"  data: no]
Fichier source*: file:///usr/lib/sunbird/js/calItemBase.js
Ligne*: 552
```

A problem with the time zone... I was not even able to see the calendar...

I forgot to say that I synchronize Sunbird with Google Agenda (using GCALDaemon). The problem is there... but I need that!

I do not get this error anymore  with Sunbird 0.8, but...

---

### Post by jeanjean84 on 2008-06-20
That's it! I've got it! :lolflag:
Silly me...

I forgot to delete my previous Sunbird profile...

I have just done it and guess what: Sunbird works like a charm!

:guitar::guitar::guitar:

---

