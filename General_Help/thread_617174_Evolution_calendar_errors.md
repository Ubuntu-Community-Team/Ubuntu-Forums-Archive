---
title: "Evolution calendar errors"
date: 2007-11-19
forum: General Help
---

### Post by reskerix on 2007-11-19
Hi, using evolution->calendar, when I try to create a 'cita' (appointment?) or note there is not result (no window open), Trying start evolution from console i get this errors than seems a programation error:

```
myuser@myuser-desktop:~$ evolution
CalDAV Eplugin starting up ...
Loading Spamassasin as the default junk plugin
** (evolution:1668): DEBUG: mailto URL command: evolution %s
** (evolution:1668): DEBUG: mailto URL program: evolution
(evolution:1668): e-data-server-DEBUG: Loading categories from "/home/myuser/.evolution/categories.xml"
(evolution:1668): e-data-server-DEBUG: Loaded 28 categories

(evolution:1668): libecal-CRITICAL **: e_cal_get_static_capability: assertion `ecal != NULL' failed

(evolution:1668): libecal-CRITICAL **: e_cal_get_static_capability: assertion `ecal != NULL' failed

(evolution:1668): calendar-gui-WARNING **: Default client not loaded 
```

googling i found this [bug]("http://bugzilla.gnome.org/show_bug.cgi?id=320489") and this answer *This has been fixed in cvs HEAD. This happens since EDS does not get started on evolution startup. The fix was committed on september 26 in evolution-data-server by harish.*

Any suggestions, help?

Thanks a lot!

---

### Post by reskerix on 2007-11-22
Hi to everybody, I replay me to say that this error seems to be fixed (in my evolution). 
I think that one of the evolution update that has been published last week have fixed it.

An alternative answer is that changing the Ubuntu language to english and change again It to my defaut language (catalan) fixed the problem but I think that it's casual. I did It for other reason.

bye.

---

