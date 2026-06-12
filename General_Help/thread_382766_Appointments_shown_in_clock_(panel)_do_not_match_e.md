---
title: "Appointments shown in clock (panel) do not match evolution calendar"
date: 2007-03-12
forum: General Help
---

### Post by Lord Darth Vader on 2007-03-12
I used to see the very same set of appointments whenever I clicked on clock in the gnome-panel. Since yesterday, after the daytime saving took effect, the appointments are not matched with their correspondents in Evolution calendar. System time is correct, appointment times are right in evolution but not in clock. 

Any idea?

---

### Post by encompass on 2007-03-12
Sounds like a bug... did you look for something similar in launchpad's bug list?  If you couldn't find anything there... post a bug.

---

### Post by IcemanV9 on 2007-03-12
Yep, I have a same problem here, too. There is no bug in launchpad. (I hope you already report a bug.)

---

### Post by Lord Darth Vader on 2007-03-12
I have not reported the bug yet. How do I report a bug in Ubuntu?

---

### Post by jlm3030 on 2007-03-13
I have the same problem it seems to have something to do with day light savings time because all the dates before last Saturday are correct and after daylight savings they are all an hour off.

---

### Post by bapoumba on 2007-03-13
Hello, please check this bug and see if it applies to you all (it may not, sorry in that case. If it does, you can comment in it):
[http://bugzilla.gnome.org/show_bug.cgi?id=392170]("http://bugzilla.gnome.org/show_bug.cgi?id=392170")
[https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/73650]("https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/73650")

---

### Post by IcemanV9 on 2007-03-13
@bapoumba - thanks for pointing out these bugs, but not quite right one.

This [[COLOR="Orange"]**bug**[/COLOR]]("http://bugzilla.gnome.org/show_bug.cgi?id=301363") is the one that causes the problem. I modified America/Chicago.ics and it worked. Now, I am surprised that Ubuntu did not update evolution-data-server (dapper, edgy) with a patch (updated timezones)!

edit: I just added my comment to the [[COLOR="Orange"]**bug**[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/79323") as well. Hopefully, they'll submit it to the updates repo for Dapper/Edgy soon!

---

### Post by maddentim on 2007-03-14
Hello,
I am having trouble with Evolution Mail and the calendar.  The system shows the correct time now on DST, but the Evolution Calendar has it still on standard time...  Not sure how to fix.  Anybody have any thoughts?

Thanks!

---

### Post by IcemanV9 on 2007-03-14
There is a [[COLOR="Orange"]**thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2292038#post2292038") on this problem (bug).

---

### Post by maddentim on 2007-03-14
> **IcemanV9 said:**
> There is a [[COLOR="Orange"]**thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2292038#post2292038") on this problem (bug).
Thanks!

---

### Post by bapoumba on 2007-03-14
Thread merged.

---

### Post by muguwmp67 on 2007-03-15
I had the same problem, and was able to fix it from the information in the bug reports.    The information on the bugzilla page was described in a very arcane fashion though.

For other laypersons, like myself,  here is what I needed to do:

[LIST=1]
[*]locate the .ics file for your timezone in /usr/share/evolution-data-server-1.8/zoneinfo/ directory.  It will be in one of the subdirectories of this folder.


[*]Open the file:
```
sudo gedit /usr/share/evolution-data-server-1.8/zoneinfo/America/Detroit.ics
```

[*]Edit the file to include a new timezone section.  My changs (additions) are in boldface:
```
BEGIN:VCALENDAR
PRODID:-//Ximian//NONSGML Evolution Olson-VTIMEZONE Converter//EN
VERSION:2.0
BEGIN:VTIMEZONE
TZID:/softwarestudio.org/Olson_20011030_5/America/Detroit
X-LIC-LOCATION:America/Detroit
BEGIN:STANDARD
TZOFFSETFROM:-0400
TZOFFSETTO:-0500
TZNAME:EST
DTSTART:19701025T020000
RRULE:FREQ=YEARLY;BYMONTH=10;BYDAY=-1SU
END:STANDARD
BEGIN:DAYLIGHT
TZOFFSETFROM:-0500
TZOFFSETTO:-0400
TZNAME:EDT
DTSTART:19700405T020000
RRULE:FREQ=YEARLY;BYMONTH=4;BYDAY=1SU
END:DAYLIGHT
[B]BEGIN:STANDARD
TZOFFSETFROM:-0400
TZOFFSETTO:-0500
TZNAME:EST
DTSTART:20070101T020000
RRULE:FREQ=YEARLY;BYMONTH=11;BYDAY=1SU
END:STANDARD
BEGIN:DAYLIGHT
TZOFFSETFROM:-0500
TZOFFSETTO:-0400
TZNAME:EDT
DTSTART:20070101T020000
RRULE:FREQ=YEARLY;BYMONTH=3;BYDAY=2SU
END:DAYLIGHT[/B]
END:VTIMEZONE
END:VCALENDAR

```

The changes for Detroit are in boldface, but you may need to modify them for other locations.  I'm not positive, but I suspect that the TZOFFSETFROM and TZOFFSETTO are the settings that would most likely need to be modified.  Make sure that they match the TZOFFSETFROM and TZOFFSETTO used in the original portion of the file.


[*]It may not be necessary, perhaps a login/logout would do it, but I rebooted the machine.  Afterwards the times were synchronized.
[/LIST]
I hope these instructions help other CLI-phobes like myself.

---

### Post by IcemanV9 on 2007-03-16
@muguwmp67 - Actually, you only NEED to change two lines for daylight and standard are DTSTART and RRULE.

Daylight
```
DTSTART:19700308T020000
RRULE:FREQ=YEARLY;BYMONTH=3;BYDAY=2SU
```
Standard
```
DTSTART:19701101T020000
RRULE:FREQ=YEARLY;BYMONTH=11;BYDAY=1SU
```

---

