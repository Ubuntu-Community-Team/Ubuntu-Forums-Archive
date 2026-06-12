---
title: "Problem running mythfilldatabase"
date: 2006-07-12
forum: General Help
---

### Post by Mateo on 2006-07-12
I have major problems when setting up mythtv (doesn't everyone!).  First I had problems with the database downloaded off of synaptic.  But eventually i was able to solve that.  i have granted privileges to user mythtv via kmysqladmin.  But when I try to run mythfilldatabase I get this error:

[http://rafb.net/paste/results/XQssQJ91.html](http://rafb.net/paste/results/XQssQJ91.html)

anyone know what could be causing it?  thanks.

---

### Post by Mateo on 2006-07-16
Since the above expires, here's the last little bit of the error (which repeats over and over).  I have tried deleting and reinstall the database off of synaptic several times.

```
DB Error (Inserting into program table):
Query was:
INSERT IGNORE INTO program (chanid, starttime, endtime, title, subtitle, description, showtype, category, category_type, airdate, stars, previouslyshown, stereo, subtitled, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, programid) SELECT chanid, starttime, endtime, title, subtitle, description, showtype, dd_genre.class, category_type, airdate, stars, previouslyshown, stereo, subtitled, hdtv, closecaptioned, partnumber, parttotal, seriesid, originalairdate, colorcode, syndicatedepisodenumber, dd_v_program.programid FROM dd_v_program LEFT JOIN dd_genre ON (dd_v_program.programid = dd_genre.programid AND dd_genre.relevance = '0');
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.dd_v_program' doesn't exist

DB Error (Inserting into programrating table):
Query was:
INSERT IGNORE INTO programrating (chanid, starttime, system, rating) SELECT chanid, starttime, 'MPAA', mpaarating FROM dd_v_program WHERE mpaarating != '';
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.dd_v_program' doesn't exist

DB Error (Inserting into programrating table):
Query was:
INSERT IGNORE INTO programrating (chanid, starttime, system, rating) SELECT chanid, starttime, 'VCHIP', tvrating FROM dd_v_program WHERE tvrating != '';
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.dd_v_program' doesn't exist

DB Error (Inserting into credits table):
Query was:
INSERT IGNORE INTO credits (chanid, starttime, person, role) SELECT chanid, starttime, person, role FROM dd_productioncrew, dd_v_program, people WHERE ((dd_productioncrew.programid = dd_v_program.programid) AND (dd_productioncrew.fullname = people.name));
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.dd_v_program' doesn't exist

DB Error (Inserting into programgenres table):
Query was:
INSERT IGNORE INTO programgenres (chanid, starttime, relevance, genre) SELECT chanid, starttime, relevance, class FROM dd_v_program, dd_genre WHERE (dd_v_program.programid = dd_genre.programid);
Driver error was [2/1146]:
QMYSQL3: Unable to execute query
Database error was:
Table 'mythconverg.dd_v_program' doesn't exist

Adjusting program database end times...
0 replacements made.
Marking repeats...found 0
Unmarking repeats from grabber that fall within our new episode window...found 02006-07-16 21:03:09.731 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
Connection timed out.
You probably should modify the Master Server settings
in the setup program and set the proper IP address.
error resceduling id -1 in ScheduledRecording::signalChange
matthew@matthew-desktop:~$

```

---

### Post by NT4usB on 2006-07-16
are you running Mythtv 0.18 and mysql 5?
they don't play well together. either run myth 0.19 or mysql 4.

---

