---
title: "Syncing Evolution to Google Calendar, and devices -- How?"
date: 2006-09-12
forum: General Help
---

### Post by pianoboy3333 on 2006-09-12
#1 I recently purchased a Zen Vision:M and was wondering if I could sync my evolution calendar to it, does anyone know of a way?

#2 I have searched on Google, but I haven't found a useful site that showed me how to synchronize Evolution to Google Calendar, such a site, or a howto would be much appreciated.

---

### Post by John.Michael.Kane on 2006-09-12
This may offer some help [http://www.opensync.org/wiki](http://www.opensync.org/wiki)

---

### Post by lassegs on 2006-09-23
I have vision:m too, and i would really like to do this. Did you find a solution? I'll look for some and post any result

---

### Post by JesusXP on 2006-09-25
I got evolution and Google calendar to sync, problem is, the calendar is read only.. Just get into the calendar, and create a new calendar from the web, use the google ical address for your google calendar and your set!

any more clarification needed msg me, happy to help. Yes this might be old, but I was searching around and just found out how to as well.

---

### Post by neuromusic on 2006-09-26
I am currently trying to set this up (two-way sync with google calendar) on a windows machine with outlook. I am hoping to do a full switch to Ubuntu in the next couple of weeks.

ScheduleWorld ([http://www.scheduleworld.com/](http://www.scheduleworld.com/)) allows two way sync with google calendar and (it seems) with Evolution...

Here is the guide for the setup on windows. No promises, as I am trying it right now.
[http://engtech.wordpress.com/2006/08/11/the-holy-grail-of-synchronization-how-to-synchronize-microsoft-outlook-multiple-locations-google-calendar-gmail-ipod-and-mobile-phone-with-funambol-scheduleworld/](http://engtech.wordpress.com/2006/08/11/the-holy-grail-of-synchronization-how-to-synchronize-microsoft-outlook-multiple-locations-google-calendar-gmail-ipod-and-mobile-phone-with-funambol-scheduleworld/)

Let me know how it goes, as I will be trying this soon with Evolution

Justin

---

### Post by Zhukov on 2006-09-28
The ScheduleWorld / Evolution relationship is quite ok, altough there are some problem when syncronizing with a sync4j client as well, but only with the calendar. I'm searching for a solution now, but the scenario doesnt look good.

---

### Post by Zhukov on 2006-11-23
All fixed.
I'm happy now. :) :D

---

### Post by padre999 on 2007-01-17
There's a new tool called GCALdaemon that acts a s a localhost between your calendar app and Google calendar. It works fine with Sunbird for me. I don't know if it also works with Evolution.

[http://gcaldaemon.sourceforge.net/](http://gcaldaemon.sourceforge.net/)
[http://sourceforge.net/projects/gcaldaemon](http://sourceforge.net/projects/gcaldaemon) 

Then there is also Calgoo for Linux now but it is not OSS and might cost one day.

[http://www.calgoo.com/](http://www.calgoo.com/)

---

### Post by lollikerwin on 2007-01-18
My 1st post!  :)  (Please excuse my n00biness.)

I set up GCALDaemon with Evolution using the Sunbird installation instructions (since none exist yet for Evolution), replacing [www.google.com](www.google.com) with localhost:9090 in the ical address.  The google calendar items show up in evolution but are still read-only, so there is nothing to be gained over just setting up a web calendar using the google ical address.  Has anyone been able to sync Evolution and Google Calendar yet using GCALDaemon?

---

### Post by tom333 on 2007-01-25
lollikerwin:

check your log file's content (gcal-daemon.log)!
I think you user name or password is incorrect, or perhaps you copied the public iCal address instead of your private iCal address...

---

### Post by lollikerwin on 2007-01-25
Hmmn, I deleted everything after it didn't work, so I'll have to try again and check the log file.  But I specifically remember putting in the private ical addresses and changing the user and pwd directly in gcaldaemon's cfg file (using the password encryption provided).  Does this mean that you've gotten it to work?  If so, I will keep trying till I figure out what I've done wrong...

---

### Post by lollikerwin on 2007-01-25
Oh wait!  I think I put in the usr and pwd in cfg when I was fiddling with the instructions for Rainlender after the instructions for Sunbird didn't work with Evolution!  So maybe that was it.  Let me fiddle some more...

---

### Post by lollikerwin on 2007-01-27
So, alas, my solution has been to just install Thunderbird with the Lightning extension instead of Evolution, which I actually like better than Evolution and works great with GCALDaemon (can even retrieve email addresses via LDAP)...  No matter what I tried, I still couldn't get the webcals on Evolution to be not read-only.  Thanks for your help anyway!!

---

### Post by Ares139 on 2007-01-29
I tried putting the iCal addresses into Evolution and it worked, but the entries disappear after a few minutes.  If I uncheck one, then recheck it, the entries will appear momentarily in Evolution and in the Gnome widget, but then disappear.  What am I doing wrong??

---

### Post by psi36 on 2007-02-19
Here's an explanation on how to sync Evolution Calendar with Google Calendar:
[http://ubuntu.wordpress.com/2006/12/18/sync-evolution-calendar-with-google-calendar/](http://ubuntu.wordpress.com/2006/12/18/sync-evolution-calendar-with-google-calendar/)

And here's how to synchronize Google Calendar and some devices like an iPod (this link was posted here already by someone else): 
[http://engtech.wordpress.com/2006/08/11/the-holy-grail-of-synchronization-how-to-synchronize-microsoft-outlook-multiple-locations-google-calendar-gmail-ipod-and-mobile-phone-with-funambol-scheduleworld/#holygrail](http://engtech.wordpress.com/2006/08/11/the-holy-grail-of-synchronization-how-to-synchronize-microsoft-outlook-multiple-locations-google-calendar-gmail-ipod-and-mobile-phone-with-funambol-scheduleworld/#holygrail)

Hope that helps.

---

### Post by Zhukov on 2007-02-19
Nice links, but I'm afraid the first one is read-only.
And related to the second, this truly works :)
I believe I told something about it before, but only now I realize I was not very explicit :D
The only way I could actually *two-way* synchronize evolution and google calendar was using syncevolution to synchronize with sheduleworld and then configure scheduleworld to synchronize with google calendar. Be advised that there is a limited number of events/updates that can be performed.

Best of lucks and thanks for the links. :)

Syncevolution:
[http://www.estamos.de/projects/SyncML/](http://www.estamos.de/projects/SyncML/)

---

### Post by AldenIsZen on 2008-04-20
You have to be running Hardy... [http://ubuntuforums.org/showthread.php?t=740925&highlight=evolution+google+calendar](http://ubuntuforums.org/showthread.php?t=740925&highlight=evolution+google+calendar)

 OR a direct link: 

[http://lifehacker.com/software/linux-tip/automatically-subscribe-to-your-google-calendar-297960.php](http://lifehacker.com/software/linux-tip/automatically-subscribe-to-your-google-calendar-297960.php)


Go to your Google Calendar and find out your private ICAL URL (This can be found after clicking Manage Calendars > Your Calendar Name)
Now, open a terminal and type :
/usr/lib/evolution-webcal/evolution-webcal YOUR_PRIVATE_ICAL_URL


 I used [http:///wwww.google.com](http:///wwww.google.com) and all.... It seems to working to some extent!

---

### Post by Ampulse on 2008-05-19
Hello,

we are in the process of managing our bands concerts and stuff via google calendar and I'm the only ubuntu guy.
The (read-only) syncing went perfectly well, but I have some troubles
accepting the invitations.
When I receive an invitation to an event it doesn't show up as the usual html-google-message but instead the buttons "accept" "cancel" etc show up - no problem there. If I press accept the event IS copied to my local calendar, but my acception doesn't show up in the google calendar.

So, is there any way to fix this or at least to display the html mail instead of the ics-stuff?

Thx in advance

Edit: I'm running a fresh Hardy.

---

### Post by AldenIsZen on 2008-06-06
> **AldenIsZen said:**
> You have to be running Hardy... [http://ubuntuforums.org/showthread.php?t=740925&highlight=evolution+google+calendar](http://ubuntuforums.org/showthread.php?t=740925&highlight=evolution+google+calendar)

 OR a direct link: 

[http://lifehacker.com/software/linux-tip/automatically-subscribe-to-your-google-calendar-297960.php](http://lifehacker.com/software/linux-tip/automatically-subscribe-to-your-google-calendar-297960.php)


Go to your Google Calendar and find out your private ICAL URL (This can be found after clicking Manage Calendars > Your Calendar Name)
Now, open a terminal and type :
/usr/lib/evolution-webcal/evolution-webcal YOUR_PRIVATE_ICAL_URL


 I used [http:///wwww.google.com](http:///wwww.google.com) and all.... It seems to working to some extent!

 IWas wrong about this.. it doesn't work two way sync. Sorry peoples!

---

### Post by CA_Warren on 2008-06-09
I'm sure syncing with devices depends on the device itself, but the following three links (in order) worked for me:

[http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)
[http://www.synce.org/moin/SynceSetup/SyncEngine](http://www.synce.org/moin/SynceSetup/SyncEngine)
[http://www.synce.org/moin/SynceSetup/OpenSync](http://www.synce.org/moin/SynceSetup/OpenSync)

OpenSync has plugins to sync with Evolution, Kontact, Google Calendar, etc. So a 3-way sync with your device, g-cal, and evolution shouldn't be too tough.

That said, the Google Calendar plugin doesn't support recurring events right now (though there are [patches]("http://www.nabble.com/-PATCH--google-calendar-recurrency-support-p9781043.html") that try to fix that).

Best of luck!

---

