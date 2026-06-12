---
title: "Deluge scheduler"
date: 2007-12-22
forum: General Help
---

### Post by trash on 2007-12-22
The scheduler keeps changing my global prefs to what the limited speeds are.
I'm on satelite so i need to keep my speeds under the radar, during the day i limit to 10 and at night i let it go crazy at 50... can the scheduler deal with this or do I have to set the global at -0?

---

### Post by trash on 2007-12-24
Ok it seems global has to be set to -1(unlimited) in order for the scheduler to work... which is NOT good for prople who have to watch their bandwidth... which is becoming more common with ISP's clamping down on filesharing.

Scheduler needs multiple speed limits me thinks.

---

### Post by Polygon on 2007-12-24
i think this question is better suited for the deluge forums at [www.deluge-torrent.org](www.deluge-torrent.org), since i don't think markybob checks this forum.

---

### Post by trash on 2007-12-24
> **Polygon said:**
> i think this question is better suited for the deluge forums at [www.deluge-torrent.org](www.deluge-torrent.org), since i don't think markybob checks this forum.

You're so right!
That said, I just need a breather from registering on forums LOL

---

### Post by trash on 2007-12-25
this is too weird, even  with the global prefs set at -1 the scheduler keeps changing them to limited speeds... so it doesn't seem to work at all.

---

### Post by deculpep on 2008-01-11
> **trash said:**
> this is too weird, even  with the global prefs set at -1 the scheduler keeps changing them to limited speeds... so it doesn't seem to work at all.

Well, thats what the scheduler *should* be doing, IMO.
The scheduler does have multiple speed limits, I think you may just be misinterpreting things.

This is how I've got it set up.

First go to Deluge Prefs>Bandwidth and set both max upload and download to -1, then click on the rightmost Plugins tab.  This is needed so only the scheduler controls the bandwidth.
Pull up the Scheduler Prefs.
Set your high download limit (50 in your case?, mine is at 180) and your high upload limit (35 in my case, since you're on satellite yours will need to be quite low).  This is your maximum (nighttime) settings.  Set your low (daytime) limits.  My lower limits are roughly half of my max.
Notice how "high" is in green, and "low" is yellow?  Well, that corresponds to the grid on the top of the dialog, you need to click the boxes yellow when you want it to respect your lower limit.  The green boxes respect your upper limit.  Red stops traffic.  If you really want unlimited, then just set the  limit in the box to -1.  I have mine going at the upper limits from 1am-7am weekdays, and 1am-10am weekends, and the lower limit for the rest of the time.
Click OK and close out all the pref boxes.

Go ahead and give deluge a restart, and the status bar on the bottom of deluge should show your limits for the current time block in parentheses.

If you need a rough idea of your actual download/upload speeds, try [http://www.speakeasy.net/speedtest/]("http://www.speakeasy.net/speedtest/") and divide your results by 8.  (warning, site uses flash)

---

### Post by trash on 2008-01-11
No it is actually a problem that has not been fixed yet. Finally found it talked about on the deluge forum.

The problem is that once the scheduled speed kicks in(and it does at that at the right time) it never changes it back to unlimited, so basically I always have to change it back manually after the scheduled time has passed.


EDIT: I just double checked the plugin and it NOW has high and low scheduler so i'll give that a try and hope!:)

---

