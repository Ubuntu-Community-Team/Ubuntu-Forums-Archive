---
title: "google calendar write support in evolution?"
date: 2008-04-25
forum: General Help
---

### Post by python152 on 2008-04-25
hi, all

I thought the google calendar write support in evolution was included with Hardy release, but I can't get it to work. Anyone out there with success?

thanks

oliver

---

### Post by deformation on 2008-04-29
same here, why no one is giving attention to these unfulfilled promises?

---

### Post by AldenIsZen on 2008-05-02
I was wondering if we are doing something wrong. I know MANY of us are looking for a solution just by the views, even though not a lot of replys.. Have all of you updated to Hardy.. new install, still on Gutsy.. I am on Hardy upgraded from gutsy and Feisty myself. I am looking for the bug number on launchpad.. I think I saw one.

---

### Post by uhappo on 2008-05-06
I'm able to see something in Evolution (from my Google Calendar), but all is a bit messed and soon Evolution will crash.

This needs to be fixed!

---

### Post by Hooya on 2008-05-08
I see all sorts of mention on the net that Evolution 2.22 was supposed to have write support for Google Calendars.  I'm running a clean install of Hardy x64 which comes with Evolution 2.22.1 and I'm completely updated.  I can get my IMAP just fine, and the calendar exists on the Google webpage for me, but there is no way for me to add an event to my Google calendar via Evolution.  It is read-only.  I cannot write to the Google calendar.  Extensive Google searching turns up no solutions, only promises that are over a year old or old mentions of how to get read-only access in Ubuntu 6.04 or older.

What gives?!

---

### Post by AldenIsZen on 2008-05-08
> **Hooya said:**
> ... Extensive Google searching turns up no solutions, only promises that are over a year old or old mentions of how to get read-only access in Ubuntu 6.04 or older.

What gives?!

And I know there are many in the exact same boat, wondering the EXACT same thing. Who can we ask this question too???

---

### Post by hugmenot on 2008-05-20
I got it working. I found a patch for it here: [http://bugzilla.gnome.org/show_bug.cgi?id=521921](http://bugzilla.gnome.org/show_bug.cgi?id=521921)

<technobabble>
It seems Google uses a non-conformant redirection when you POST the event to the server and the SOAP library that Evolution uses doesn't handle that. The patch only applied cleanly after I replaced all gdata-google stuff in the source tree of evolution-data-server with the slighly newer sources from the svn repository.
</technobabble>

I wonder now what the best way for you guys to test this is. I uploaded a .diff.gz to my Launchpad PPA and got evolution-data-server 2.22.1.1-0ubuntu4~ppa1 built there. Since the only change is in the libgdata packages I wonder if it's enough to just install those two.

Please, someone **not noobish** who wants this working do the check if methods 1) or 2) work and report back.

1)   &#8212; install 
[LIST]
[*][http://ppa.launchpad.net/.../e-d-s/libgdata1.2-1_2.22.1.1-0ubuntu4~ppa1_i386.deb](http://ppa.launchpad.net/towolf/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.22.1.1-0ubuntu4~ppa1_i386.deb)
[*][http://ppa.launchpad.net/.../e-d-s/libgdata-google1.2-1_2.22.1.1-0ubuntu4~ppa1_i386.deb](http://ppa.launchpad.net/towolf/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.22.1.1-0ubuntu4~ppa1_i386.deb)
[/LIST]
**s/i386/amd64/** is possible
You may want to enable hardy-proposed first to get the latest /official/ e-d-s 2.22.1.1-0ubuntu3.

2)   &#8212;  if only 1) was not enough.
 [Add my PPA repo]("https://launchpad.net/~towolf/+archive") to sources.list and only pull the updates from under the entry of evolution-data-server, i.e., not the other stuff I have there.


Stuff that is still not working:
[LIST]
[*]Only the first calendar is supported
[*]Creating an Appointment in Evo doesn not enable the default reminder (SMS or Email in Google Calendar)
[*]Events are not listed in clock applet (the day number is bold, though)
[*]Editing events seems to not work either?
[/LIST]

---

### Post by AldenIsZen on 2008-05-20
I am "noobish-ish", sorry. But SWEET! I just decided to look into this again after laying it down awhile. Unfortunately I think all the things not working pretty much take all the sweet out of the sugar.

 Thanks for the update Hug, hopefully this will be fixed soon. I imagine there are many looking for this to fully work.

---

### Post by juanhm on 2008-05-27
It works for me just following your method number 1) and adding hardy-proposed.  

Now I can create new events in Google Calendar from Evolution but, as you mention, if I edit an event in Evolution it has no effect in Google Calendar as happens with reminders.

Thanks.

---

### Post by deformation on 2008-05-28
Thanks for the solution, but sadly still its not getting sms and email alarms to work, Does anyone know if Gcaldaemon makes sms and email alerts working?

---

### Post by gcbzzzz on 2008-05-30
evolution 2.22.1.1 and still does not work as intended.

---

### Post by farmorg on 2008-09-17
Hi
Does anyone know if there has been any progress with this?
I have tried the 8.10 (Intrepid) live cd but still no write access to Google calendar.

Thanks
farmorg

---

### Post by _sAm_ on 2008-09-17
I have not tried Evolution + Google calendar, but it works very well in Thunderbird + Lightning and Google calendar.

---

### Post by hugmenot on 2008-09-17
Well, it works for me now. Google support has improved a lot in this iteration, I use Google calendar and contacts as the default now. What still doesn&#8217;t work so well is periodic appointments, but for that I use gcalcli and natural language input.

---

### Post by bLaCkMeTaLL on 2008-11-05
I have Ubuntu 8.10 X86_64 and Evolution 2.24.1 but _still_ I am not able to post updates to my Google Calendar :?

---

### Post by reader4 on 2009-01-02
Works just fine for me in 8.10 32-bit, but not in 8.10 64-bit...

---

