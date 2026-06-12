---
title: "Google Calendar 2-way sync with Evolution"
date: 2008-04-09
forum: General Help
---

### Post by mlyons16 on 2008-04-09
Due to recent frustrations with Thunderbird, I've been taking another look at Evolution. My biggest concern is, does it have the ability, whether by default or extension, to sync 2 ways with Google Calendar?

I also think I want to use the default PIM in Ubuntu, especially if I'm going to be synchronizing with a PDA.

---

### Post by xarquid on 2008-04-09
You have quite a few options. The most popular being ScheduleWorld (which I highly recommend) and is the easiest. Please check out:

[http://www.scheduleworld.com/](http://www.scheduleworld.com/)

For details.

Secondly, many also enjoy and love GCalDaemon. Please see:

[http://gcaldaemon.sourceforge.net/index.html](http://gcaldaemon.sourceforge.net/index.html)

It takes a little bit of setting up, but works great. It's Java based. Just reply in this thread if you need any assistance or ask on their site :-) They have an excellent guide.

Third, I recommend you read:

[http://johnnyjacob.wordpress.com/2006/04/30/google-calendar-in-evolution/](http://johnnyjacob.wordpress.com/2006/04/30/google-calendar-in-evolution/)

Also for your P.D.A. needs have you heard of GooSync? It would be your PDA need...completely.

[http://www.goosync.com/](http://www.goosync.com/)

The. Best.

Sincerely,

Craig Huffstetler
xq on freenode irc

---

### Post by mlyons16 on 2008-04-09
Are all of these desktop based synching solutions? I don't want to be synching over the air. I'd like to be able to connect via bluetooth or USB to sync.

---

### Post by xarquid on 2008-04-09
GoogSync is the only "over the air" one since you mentioned the P.D.A...I use it just to sync my Google Calendar to my Blackberry. I personally use Mozilla Thunderbird Lightning Extension and sync with Google Calendar (2 way) using it. Then Goog Calendar syncs back forth....then Goog Sync goes with my P.D.A. so everything is -always- synced up. I love it.

However, the OTHER applications I listed ARE desktop applications, of course. Not over the air...

**The rest are desktop based to sync with your calendar (Evolution to Google Sync and back [2 way]). **

Sincerely,

xq

:-)

---

### Post by mlyons16 on 2008-04-09
Ya, basically, I'm in between phones right now. I'm looking at maybe getting a new Sony Ericsson or Nokia. I want to have my Google calendar 2 way synced with Evolution or Thunderbird, have my contacts in Evolution or Thunderbird, and be able to plug my phone into my linux computer via USB and sync it up nicely. This is quite a daunting task on linux, and I see why a lot of people fall in love with Microsoft Outlook and their phones proprietary PC Suite.

---

### Post by BillGod on 2008-04-09
Hardy Heron 8.4 version of evolution has this feature built in.  For some reason I get an error when I use it but it is now a drop down option.  And yes it does allow for editing.

---

### Post by mlyons16 on 2008-04-09
> **BillGod said:**
> Hardy Heron 8.4 version of evolution has this feature built in.  For some reason I get an error when I use it but it is now a drop down option.  And yes it does allow for editing.

Oh nice! What are your sources for that, I'm just curious. This is the first I'm hearing of that. I think I'm starting to like Evolution better than Thunderbird. I'll see how my feelings change when Thunderbird 3 is released, but for now, I think I'm going to switch to Evolution. Evolution is a pretty secure mail client correct?

Nevertheless, that's great to hear they are pre-packaging that in the next Hardy Heron. I can't wait till Gmail supports LDAP for contacts.

---

### Post by mlyons16 on 2008-04-09
One more question, can Evolution handle RSS feeds?

---

### Post by AldenIsZen on 2008-04-20
> **BillGod said:**
> Hardy Heron 8.4 version of evolution has this feature built in.  For some reason I get an error when I use it but it is now a drop down option.  And yes it does allow for editing.

You have to be running Hardy... [http://ubuntuforums.org/showthread.php?t=740925&highlight=evolution+google+calendar](http://ubuntuforums.org/showthread.php?t=740925&highlight=evolution+google+calendar)

 OR a direct link: 

[http://lifehacker.com/software/linux-tip/automatically-subscribe-to-your-google-calendar-297960.php](http://lifehacker.com/software/linux-tip/automatically-subscribe-to-your-google-calendar-297960.php)


Go to your Google Calendar and find out your private ICAL URL (This can be found after clicking Manage Calendars > Your Calendar Name)
Now, open a terminal and type :
/usr/lib/evolution-webcal/evolution-webcal YOUR_PRIVATE_ICAL_URL


 I used [http:///wwww.google.com](http:///wwww.google.com) and all.... It seems to working to some extent! Setting it up inside Evolution did not work for me and the username disappeared, unless I did it this way.

---

### Post by AldenIsZen on 2008-04-25
> **mlyons16 said:**
> Oh nice! What are your sources for that, I'm just curious. This is the first I'm hearing of that. I think I'm starting to like Evolution better than Thunderbird. I'll see how my feelings change when Thunderbird 3 is released, but for now, I think I'm going to switch to Evolution. Evolution is a pretty secure mail client correct?

Nevertheless, that's great to hear they are pre-packaging that in the next Hardy Heron. I can't wait till Gmail supports LDAP for contacts.

 I think I would use Thunderbird if I could replace the timeclock on the gnome panel the way it comes default in Ubuntu and then see I have events on certain dates. That is the biggest teaser.. I know the potential is there.. no one has done it yet and made it easy. That is a shame considering how popular Google and Google Calendar is.

 I have tried GCal Deamon but I couldn't get it to work.

---

### Post by mlissner on 2008-04-29
I have been trying to get evolution 2.12 to sync with google calendar for quite some time now. The GCALDaemon program worked like a charm, even though it's supposedly built into this version of evolution. 

Thanks for the link.

---

