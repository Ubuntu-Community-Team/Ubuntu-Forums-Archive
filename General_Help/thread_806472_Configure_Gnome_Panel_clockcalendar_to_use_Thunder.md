---
title: "Configure Gnome Panel clock/calendar to use Thunderbird/Lightning"
date: 2008-05-25
forum: General Help
---

### Post by komputes on 2008-05-25
I use Thunderbird and lightning-extention as a calendar (please note that firefox's xpi file for thunderbird does not work well, use "apt-get install lightning-extention"). I find this much more stable and usable than evolution. Is there a way of getting a calendar in the panel which works with lightning/thunderbird instead of evolution. Are there any alternate date and time applets?

I found a closed thread from 2006 requesting the same thing:

[http://ubuntuforums.org/showthread.php?t=150188](http://ubuntuforums.org/showthread.php?t=150188)

			 			 		   		 		 		I was just wondering if there was a way to bind GNOME panel clock/calendar to Sunbird/Thunderbird instead of Evolution. What source files would need to be modified? Has anyone tried doing this?

---

### Post by swordphsh on 2008-05-31
> **komputes said:**
> I was just wondering if there was a way to bind GNOME panel clock/calendar to Sunbird/Thunderbird instead of Evolution. What source files would need to be modified? Has anyone tried doing this?



I've also been looking around for a way to do this. If anyone has any information on it, it would be great.

---

### Post by komputes on 2008-06-02
I think we should attempt to bring all the people who want this together and see if we can create a blueprint on Launchpad for this project. There are quite a few threads asking for this so if we can get some good ideas together that would be great, perhaps we can have out Lightning Panel Applet for Ibex.

---

### Post by tamias on 2008-06-03
I would be very interested in this capability.

---

### Post by xak on 2008-06-06
Yes!  This would be fantastic!  Please please please! [-o<

---

### Post by tamias on 2008-06-06
From reading around various other wish-lists and Ubuntu blueprints, it looks like the best idea may be to add a provider -- like the Google calendar provider in Thunderbird, or perhaps a separate daemon process -- which can read the Lightning calendar data and add it to evolution-data-server. Another option is to extend the clock applet so that it can be written-to by any registered calendar application.

A workaround to achieve this behaviour in a round-about way may be possible: [GCalDaemon]("http://gcaldaemon.sf.net") could be used to synchronise Lightining and Evolution. If Evolution is set not to display its own alarms (so as to avoid duplicate popups for each alarm which rings), it can just be a 'pass-through' mechanism for e-d-s to read calendar data and update the panel clock.

---

### Post by sancho panza on 2008-06-06
I'm all for integration of thunderbird email and calendaring into gnome. Am sorry I'm not into coding though.

---

### Post by komputes on 2008-06-06
Tamias, please don't get sidetracked. I don't use Google Cal because I keep my calendars private and I am offline many times so I'm sorry but this does not meet the stated use case.

Please treat this thread as a petition for the idea/concept, if you want to encourage the development of this panel, your two cents are welcomed. Half-baked workarounds which require network services are not as welcomed. We need this to be clean and simple for Grandma Ubuntu Everyuser.

> Another option is to extend the clock applet so that it can be written-to by any registered calendar application.You second comment did interest me and therefore I have added it to the blueprint below:

[https://blueprints.launchpad.net/ubuntu/+spec/lightning-extention-panel](https://blueprints.launchpad.net/ubuntu/+spec/lightning-extention-panel)

---

### Post by tamias on 2008-06-06
> **komputes said:**
> Tamias, please don't get sidetracked. I don't use Google Cal because I keep my calendars private and I am offline many times so I'm sorry but this does not meet the stated use case.


Please take note, I never specified the use of Google calendars. This would be a non-starter for a number of reasons: reliance on Google, reliance on presence of an Internet connection, ownership of a Google account, etc.

My suggestion was based on the fact that Thunderbird's Google provider is a good grounding for development of what you could call, for want of a better name, an evolution-data-server provider. That is, a plugin for Thunderbird which reads calendar data from Lightning and pipes it to e-d-s *in the same manner* as the Google provider does so for Google calendars.

That's only useful if you want to use evolution-data-server, of course. Another option is to extend the clock panel applet's API so it can accept input from any arbitrary data server. Then the user could choose Lightning, Evolution, gnome-calendar, etc.
> You second comment did interest me and therefore I have added it to the blueprint below:

[https://blueprints.launchpad.net/ubuntu/+spec/lightning-extention-panel](https://blueprints.launchpad.net/ubuntu/+spec/lightning-extention-panel)

Thanks, looks good.

Mark

---

### Post by komputes on 2008-06-06
So we want to minimize our dependency on other products/services. You have mentioned Google Calendar and the the Internet, but if we are relying on Evolution to stay the same, isn't that just as bad? Here is my example of issues your e-d-s idea may have:

-If developers change something in the back end of evolution, this "lightning-extention-panel" that we are proposing to develop will perhaps break, meaning it will have to change as well. Developers on this project will need to be familiar with both programs in that case.

-If the user has completely eradicated evolution (creating a minimal system for example) from their system and only run TB, then good luck with this. Too many dependencies. See what I mean?

---

### Post by tamias on 2008-06-09
> **komputes said:**
> So we want to minimize our dependency on other products/services. You have mentioned Google Calendar and the the Internet, but if we are relying on Evolution to stay the same, isn't that just as bad? Here is my example of issues your e-d-s idea may have:

-If developers change something in the back end of evolution, this "lightning-extention-panel" that we are proposing to develop will perhaps break, meaning it will have to change as well. Developers on this project will need to be familiar with both programs in that case.

Ok, but how exactly is this different from relying on any other application (such as the current clock panel applet) that provides an API? Good programming principles will ensure that APIs are kept consistent; this is standard practice.

To clarify my position, to my mind there are three solutions:

1. Develop a new clock applet from scratch for Thunderbird (pointless duplication of effort).

2. Hook into the current evolution/clock applet system by using e-d-s as an interim data provider to the clock applet; Lightning updates e-d-s, e-d-s updates the clock applet. This requires the least amount of development effort, but as you point out, maintains the current dependency on Evolution.

3. (Preferred option) Extend the current clock applet to provide an API for Evolution, Lightning, and anything else that wants to use it. This is the best solution, but requires potentially quite a lot of reworking to decouple Evolution and e-d-s from the clock applet.

In addition, all three options will still require development of a provider to sit inside Thunderbird and update the GNOME applet.

> -If the user has completely eradicated evolution (creating a minimal system for example) from their system and only run TB, then good luck with this. Too many dependencies. See what I mean?

Agreed. Which is why I proposed the idea of extending the clock applet to give a universal calendar API.

---

### Post by SmokinJuan on 2008-06-12
What's the point of 
/desktop/gnome/applications/calendar
in gconf-editor?

I found that key (before I found this thread).  It was set to Evolution by default.  I changed it to sunbird with no effect.

---

### Post by milkandhoney on 2008-06-20
There is a really easy workaround.
API's an such are all there since both, thunderbird and evolution support the ICS calendar format.

I use the same file in both the products, so the clock-applet gets updated anyway.

```
evolution -force-shutdown

mv /home/user/.evolution/calendar/local/system/calendar.ics /home/user/.evolution/calendar/local/system/original_calendar.ics

ln -s /home/user/.mozilla-thunderbird/aabbccnnn.default/ical_user.ics /home/user/.evolution/calendar/local/system/calendar.ics

evolution &  

```

I move evolution's default calendar out of the way and create a symlink to my thunderbird ics-calendar file instead.

---

### Post by komputes on 2008-06-20
I can't seem to find my Thunderbird ics file. How did you get it there?

---

### Post by sancho panza on 2008-06-21
komputes, i think milkandhoney is referring to the sunbird calendar file. That file calendar .ics file can easily be created anywhere you like by using the save option in the sunbird menu.

---

### Post by swordphsh on 2008-06-21
> **sancho panza said:**
> komputes, i think milkandhoney is referring to the sunbird calendar file. That file calendar .ics file can easily be created anywhere you like by using the save option in the sunbird menu.

Is there any way to do this with the lightning extension calender?

---

### Post by denham2010 on 2008-06-22
Hi,

If you are running Xfce (or Gnome, as I believe you can use Xfce applets in the Gnome panel), try Orage.

Orage is the Xfce default calendar application, and you can configure it using the GUI Exchange Data option to read any .ics file you wish!

I currently have it set to read my Sunbird/Lightning calendar.

Cheers.

---

### Post by IanW on 2008-06-22
> **komputes said:**
> -If the user has completely eradicated evolution (creating a minimal system for example) from their system and only run TB, then good luck with this. Too many dependencies. See what I mean?

Whilst tweaking Hardy on my EeePC, I found that the only part of Evolution I could not remove was evolution-data-server, as it is a dependency of the clock/calendar applet.

The rest of Evolution was easily removed with no issues, as it too depends on e-d-s, not vice-versa.

Perhaps piping Lightning/Sunbird through e-d-s may be the answer after all?

---

### Post by komputes on 2008-06-23
> komputes, i think milkandhoney is referring to the sunbird calendar file. That file calendar .ics file can easily be created anywhere you like by using the save option in the sunbird menu.

I would have to save an ics copy of my calendar every time i make a change, unacceptable. :-|

At this point I'd be happy with either type of integration.

@ IanW: Some of those bundled gnome packages are a pain to take out.

---

### Post by aldeby on 2008-06-29
lightning stores calendar events in a storage.sdb database file... 

I wish GNOME developers get their hands in this, evolution sucks too much and a desktop environment shouldn't be tied so tightly to the default mail client and PIM.

---

### Post by w0ng on 2008-08-02
*bump*

Any updates on any kind of development with this?

---

### Post by CParticle on 2008-08-13
The simple solution is to switch over to using ics as the default calendar type in Thunderbird.  This way the ics file is stored locally.  Any updates go directly to that file.  No need to continually export ics files.  From there you can hook the ics file into Evolution and your events should show up in the Gnome Panel calendar app.  This would be for display purposes only and you would still need the Evolution Data server so that it could work correctly but for those who just want to have the information displayed it should work.  Also any click to go to the event would bring up Evolution and not Thunderbird.

So it doesn't solve the problem of evolution vs Thunderbird on your system but you can at least see your calendar in the panel and still use Thunderbird as you primary calendar app.

CParticle

---

### Post by swordphsh on 2008-08-13
> **CParticle said:**
> The simple solution is to switch over to using ics as the default calendar type in Thunderbird.

How would one do this?

---

### Post by merlyn on 2008-08-16
> **swordphsh said:**
> How would one do this?

At present, Lightning does not support .ics other than to export a calendar or to publish a calendar on the web.

Apparently Thunderbird 3.0 due out later this year, (sometime), will include a calendar feature (lightning) by default.

Whether or not there are plans to implement .ics for local calendar storage or not I cannot say. But I'm going to keep on snuffling around on the net to see what I can find out.

I too would like to see the capability of integrating lightning calendar into the desktop, i.e. to be able to view and add events / tasks via the clock applet.

Cheers.

---

### Post by ions on 2008-08-23
Just wanted to add another name to the list of those that desire this functionality: mine.

---

### Post by zasq on 2008-08-24
Yeah! mine too!\\:D/

---

### Post by Ms_Angel_D on 2008-08-26
I would love to see a calendar applet for gnome that works with lightning!

---

### Post by boombox1387 on 2008-09-12
Just wanted to throw my name on this list.  GNOME seems to work so hard to give users options; it seems strange that such a useful part of the desktop environment is tied so closely to a single application.

---

### Post by Chamith on 2008-09-18
<<tamias's>> solution to sync via Google Calendar is a quick workaround for those using internet based services but it works well- THANKS!

Another hat into the ring for more choice on email / PIM applications in Gnome.

---

### Post by Aearenda on 2008-09-18
I use GCalDaemon to sync Sunbird to Google, and as a side-effect I have a script to copy the ics file to Evolution so I can get clock integration. But I find that Evolution does not understand Sunbird's calendar exceptions for repeating items, so the clock calendar sometimes shows me things that aren't really there - specifically, repeating items that have been removed or modified just for one occurrence.

---

### Post by lipinski on 2008-09-23
For all those that are questioning the .ics usage in Lightning (and possibly Sunbird, I cannot answer that - I use Lightning), there is a bit of a trick in Lightning.

If you add a new Calendar, and select "On My Computer", then your calendar entries will be stored in your profile's storage.sdb file - which is an SQLite database.  This isn't much help outside of Lightning nor for sharing calendars between apps.

However, if you add a new Calendar, and select "On the Network", then select Format (iCalendar), then for location place a reference to where you want (or already have) an .ics file with all your calendar entries.  This is intended for server-based storage of .ics files, i.e., WebDAV server, or whatever, but the trick is that a location of "file://<path>/<file>.ics" also works for locally stored files.  I use "file:///home/username/Calendar/calendar.ics"

Long story, but after messing with the Darwin Calendar Server, and fighting with authentication, extended file attributes, etc., I scratched the DCS idea, and found this handy method of using .ics files for Thunderbird.  No exporting/importing necessary, you can use the .ics files in other apps, users can share them, etc.

By using standard Linux file/directory ownership and permissions, you can control shared calendars, read-only calendars, etc.

Also, as was previously mentioned in this post, using Thunderbird with .ics files (as opposed to storage.sdb), you can symbolically link your Thunderbird-managed .ics files to other applications as well (i.e., Evolution).

Of course, this won't help with some .ics compatibility issues between different applications (I think someone mentioned Evolution vs Lightning regarding Recurring events)...

---

### Post by Aearenda on 2008-09-23
Lipinski's way of getting Lightning to work with .ics files does work for me with Sunbird, but it is quite slow with a complex calendar - and this is so with Sunbird 0.9 rc2 as well as all previous versions. It takes 2 minutes to open Sunbird on my 1GHz Pentium-M laptop, with 2 calendars (my own and my wife's)! In comparison, Evolution opens within a few seconds.

---

### Post by lipinski on 2008-09-23
> **Aearenda said:**
> Lipinski's way of getting Lightning to work with .ics files does work for me with Sunbird, but it is quite slow with a complex calendar - and this is so with Sunbird 0.9 rc2 as well as all previous versions. It takes 2 minutes to open Sunbird on my 1GHz Pentium-M laptop, with 2 calendars (my own and my wife's)! In comparison, Evolution opens within a few seconds.

Does Evolution open within a few seconds using the same .ics files as was used on Sunbird/Lightning?
Also, just out of curiosity, when you say it takes 2-min to open Sunbird, does this mean Sunbird is unusable for the 2-min, or Sunbird does not display your calendar events for two min?  (The reason I ask is that I have seen problems with Thunderbird refreshing Calendars on startup).

---

### Post by Aearenda on 2008-09-24
Yes, for me Evolution opens in seconds with a copy of the same file as Sunbird takes 2 minutes to open. And Sunbird does display it's cached version of the calendar if the 'experimental' caching option is on, but the calendar remains unusable until Sunbird has finished doing whatever it is doing. If caching is off, then nothing shows. Once Sunbird is running, just moving from one week to the next in week view is sluggish compared to Evolution, which is pretty much instant.

---

### Post by Aearenda on 2008-09-25
I should add that the new Sunbird 0.9 released version DOES seem to go faster, but it is still slower than Evolution. With the experimental caching turned off, it still takes 8 seconds to move from one week view to the next in Sunbird. Evolution takes 2 seconds at the most.

---

### Post by komputes on 2008-10-06
> Apparently Thunderbird 3.0 due out later this year, (sometime), will include a calendar feature (lightning) by default.

@merlyn - from a post on the TB Developers mailing list, I got the idea that a notification daemon was not something they were currently working on:

> "[FONT=monospace]
[/FONT]> There is a default mail client named "Evolution" which[FONT=monospace]
[/FONT]> comes with is integrated with gnome's clock/calendar panel applet. I was[FONT=monospace]
[/FONT]> wondering if Thunderbird 3 (now with Lightning integrated by default)[FONT=monospace]
[/FONT]> will have a panel applet and event daemon of its own to allow users to[FONT=monospace]
[/FONT]> quickly view daily tasks and get alarm notifications (even if[FONT=monospace]
[/FONT]> Thunderbird is not running). Another possibility would be to use the[FONT=monospace]
[/FONT]> current Gnome clock applet. There is a discussion concerning this issue[FONT=monospace]
[/FONT]> here: [http://ubuntuforums.org/showthread.php?t=806472](http://ubuntuforums.org/showthread.php?t=806472)

Most likely, this could be done effectively by integrating Mozilla as a 
backend to the Evolution data server. See 
[<https://bugzilla.mozilla.org/show_bug.cgi?id=410076>]("https://bugzilla.mozilla.org/show_bug.cgi?id=410076") for the calendar 
side and [<https://bugzilla.mozilla.org/show_bug.cgi?id=408158>]("https://bugzilla.mozilla.org/show_bug.cgi?id=408158") for the 
address book.

Could it be done in time for TB 3? Probably not." 

So I started trying out the workaround, and technically it does the job for now. Here are the instructions which worked for me. Thanks to :KS lipinski and :KS milkandhoney for their help. 

**Creating the ICS**
-Open Lightning/Sunbird
-Backup you calendar/mail folders in case something ugly happens
-Export calendar to file:///home/username/Calendar/calendar.ics
-Add a Network calendar from file:///home/username/Calendar/calendar.ics
[B]
Getting the gnome-calendar-applet to read the ICS[/B]

In a terminal (Applications > Accessories > Terminal)
```
$ evolution --force-shutdown
$ mv ~/.evolution/calendar/local/system/calendar.ics ~/.evolution/calendar/local/system/calendar.ics.bak
$ ln -s ~/Calendar/calendar.ics ~/.evolution/calendar/local/system/calendar.ics
$ evolution &
```


There are two things that bother me with this setup:

1) Low priority: Double clicking on a meeting calendar applet, Evolution comes up, not Thunderbird/Sunbird. 

2) High priority: I find that changes are not made immediately to the Local-masquerading-as-Network calendar. Does anyone know how to have more sync/refresh polls between EDS and Lightning/Sunbird to have the latest modification reflect in the applet.

---

### Post by Aearenda on 2008-10-06
Re 2): I think Evolution does not poll the file except at startup.

I say this because I use both Sunbird and Evolution with GCALDaemon, and it says that in GCALDaemon's instructions; it agrees with what I observe in action. 

Also, you will find discrepancies with exceptions to recurring appointments - Sunbird records these in UTC, using the "Z" suffix to the time string in EXDATE lines, but Evolution interprets them in local time, ignoring the "Z" and therefore the whole EXDATE line. I have an ugly script that converts the times, but it is way too ugly to publish!

Also, I find Sunbird is much slower working directly from a file like this if your calendar is at all complex.

---

### Post by tamias on 2008-10-07
I just came across this, linked from the Gnome website: 
"[Evolution Data Server's] extensible architecture, allows the addition of plugins to manage different kinds of calendar/tasks/addressbook sources, by just writing a shared library, which will be loaded by evolution-data-server on startup." ([http://www.go-evolution.org/EDS_Architecture](http://www.go-evolution.org/EDS_Architecture))

And: 
"Calendar backends deal with the communication between evolution-data-server and specific calendar servers/types. Thus, a backend must be written for any different calendar source (file backend for local files, webcal backend for HTTP, Groupwise, Exchange, etc)." ([http://www.go-evolution.org/EDS_Architecture#Calendar_backends](http://www.go-evolution.org/EDS_Architecture#Calendar_backends))

Therefore it appears that all that needs writing is a calendar backend for Lightning/Sunbird to communicate with EDS. It may be that the gnome-panel clock applet's calendar plugin needs to be replaced with a simple sunbird calendar plugin, but the mechanism for updating EDS is the hard part, IMHO.

How do we track down developers who are familiar with both Evolution Data Server and the Gnome clock applet?

---

### Post by komputes on 2008-10-07
tamias, this is good links to have on this thread. 

It gives me an idea, but I am not a great programmer yet so I will need some help. From the links you have sent, does this mean that there is a way to start up EDS, telling it to update every X minutes? 

Otherwise, is there a way I can create a cron that will run every X minutes and send a "get_changes" message to EDS, forcing it to load a newer copy?

---

### Post by tamias on 2008-10-13
> **komputes said:**
> 
It gives me an idea, but I am not a great programmer yet so I will need some help. From the links you have sent, does this mean that there is a way to start up EDS, telling it to update every X minutes? 

Otherwise, is there a way I can create a cron that will run every X minutes and send a "get_changes" message to EDS, forcing it to load a newer copy?

I'm not sure that this is how EDS works. As I understand it, it's started during Gnome start-up anyway (so that's not an issue), but communications are achieved via CORBA, which is a "behind-the-scenes" messaging protocol. So to make use of this, you need to implement a CORBA component (call it an EDS data provider plugin for Thunderbird) to interface between Lightning and EDS, which will handle the communications for things like getting and setting changes. There isn't just some "magic command" you can run from a bash prompt.

Unfortunately, whilst I am a programmer myself, I don't have any experience with CORBA, or indeed the rest of the way Gnome works. If I ever find myself a few spare weeks/months, I may be able to teach myself the relevant bits and begin work on something, but that time could be years away, if ever. That's why I said we need to track down developers who are familiar with both Evolution Data Server and the Gnome clock applet.

---

### Post by Thelasko on 2008-11-17
> **komputes said:**
> So I started trying out the workaround, and technically it does the job for now. Here are the instructions which worked for me. Thanks to :KS lipinski and :KS milkandhoney for their help. 

**Creating the ICS**
-Open Lightning/Sunbird
-Backup you calendar/mail folders in case something ugly happens
-Export calendar to file:///home/username/Calendar/calendar.ics
-Add a Network calendar from file:///home/username/Calendar/calendar.ics
[B]
Getting the gnome-calendar-applet to read the ICS[/B]

In a terminal (Applications > Accessories > Terminal)
```
$ evolution --force-shutdown
$ mv ~/.evolution/calendar/local/system/calendar.ics ~/.evolution/calendar/local/system/calendar.ics.bak
$ ln -s ~/Calendar/calendar.ics ~/.evolution/calendar/local/system/calendar.ics
$ evolution &
```


There are two things that bother me with this setup:

1) Low priority: Double clicking on a meeting calendar applet, Evolution comes up, not Thunderbird/Sunbird. 

2) High priority: I find that changes are not made immediately to the Local-masquerading-as-Network calendar. Does anyone know how to have more sync/refresh polls between EDS and Lightning/Sunbird to have the latest modification reflect in the applet.

That completely broke Thunderbird, thanks!:lolflag:

Seriously, I opened Thunderbird after an alarm went off and it froze.  It froze so hard it almost locked up my whole system.  I had to restart the machine.  I also should note that Gnome didn't display the correct time for my appointments.

Luckily, I simply deleted the calendar.ics file and everything went back to normal.

P.S. Despite the failure, keep it up.  I long for the day when Thunderbird is integrated with the desktop.

---

### Post by Maverick1712 on 2008-11-18
I'd like to throw my hat in the ring on this one.

It is not a huge issue for me, since I usually keep thunderbird open on it's own workspace (please don't yell at me for being innefficient), butthis is more a matter of convenience and options, as well as cleaning up my system by removing unused packages. Unfortuneately, I don't have the programming knowledge required for this either. Will continue to research and help where I can.

Cheers

---

### Post by Bakkoda on 2008-11-21
I found that the symbolic link was being broken on every login. I simply added the evolution calendar as a network calendar in Lightning and its worked wonders since. Sharing the calendar works well as I can add things using Evolution via the calendar and Thunderbird while checking email.

---

### Post by meastp on 2008-11-21
I'm also interested in this.

---

### Post by fatblueduck on 2008-11-28
I really just want to rant here... so here it goes.

I have never liked evolution. Try to print a weekly calendar and the small numeric calendar in the upper-right hand of each page is formatted incorrectly. I always check to see if the bug is still there, and for several years now, no matter what machine or distro I'm on, that bug is still there.

Novell is not a great company and unfortunately they have been responsible for the direction of the gnome all-in-one PIM. Relying on Novell to release good software is a terrible spot to be in.

---

### Post by meastp on 2008-11-28
> **fatblueduck said:**
> I really just want to rant here... so here it goes.

I have never liked evolution. Try to print a weekly calendar and the small numeric calendar in the upper-right hand of each page is formatted incorrectly. I always check to see if the bug is still there, and for several years now, no matter what machine or distro I'm on, that bug is still there.

Novell is not a great company and unfortunately they have been responsible for the direction of the gnome all-in-one PIM. Relying on Novell to release good software is a terrible spot to be in.

I use evolution, but there are some issues. I'll try to make mockups of usability-enchanchements and file bugs when I have time.

I think you are a bit unfair, though. Did you do anything more than check that the bug exists? Just finding the bug-report and confirming that it is still there, helps.

It is a shame that development in Evolution is so hard. I did read about developing plugins in Python, but there was never a howto, or tutorial.

I would like to see more activity from the Evolution crowd on Planet Gnome or Gnome News...

But, this thread is about evolution-data-server, not evolution.

---

### Post by zwol on 2008-11-30
Hi.
I've found this little Thunderbird addon:
[Evolution Mirror]("https://addons.mozilla.org/en-US/thunderbird/addon/9656")
It makes Thunderbird - Evolution sync a lot easier.

---

### Post by Thelasko on 2008-12-01
> **zwol said:**
> Hi.
I've found this little Thunderbird addon:
[Evolution Mirror]("https://addons.mozilla.org/pl/thunderbird/addon/9656")
It makes Thunderbird - Evolution sync a lot easier.

Will it work on 64-bit?

---

### Post by tamias on 2008-12-02
> **zwol said:**
> Hi.
I've found this little Thunderbird addon:
[Evolution Mirror]("https://addons.mozilla.org/pl/thunderbird/addon/9656")
It makes Thunderbird - Evolution sync a lot easier.

Fantastic, this looks like it will do the job. Not quite as complete as extending Gnome's clock applet to work with any 'system calendar', but probably the next-best solution.

The English page, for anyone who wants it: [https://addons.mozilla.org/en-US/thunderbird/addon/9656](https://addons.mozilla.org/en-US/thunderbird/addon/9656)

---

### Post by Thelasko on 2008-12-04
When I install this add-on it says "requires additional items" any idea what that means?

---

### Post by swordphsh on 2008-12-04
> **zwol said:**
> Hi.
I've found this little Thunderbird addon:
[Evolution Mirror]("https://addons.mozilla.org/en-US/thunderbird/addon/9656")
It makes Thunderbird - Evolution sync a lot easier.

AWESOME. Exactly what I needed. :D

---

### Post by Rockiger on 2009-01-15
> **komputes said:**
> 
There are two things that bother me with this setup:

1) Low priority: Double clicking on a meeting calendar applet, Evolution comes up, not Thunderbird/Sunbird. 

There is a dirty solution:

Just create a file "evolution" place 
```
sundbird
``` or ```
thunderbird
```
in it. Then 
```
chmod evolution +x
sudo cp evolution /usr/bin/
```
Then it will work. I personally find this solution together with the Evolution-Mirror working very well.

Rockin' Regards,
Marco

---

### Post by kylea on 2009-01-27
Worked very nice - thanks

---

### Post by Rockiger on 2009-01-28
The Problem is that evolution-alarm-notify does not work anymore. I removed evolution. I try to find a solution for that.

Rockin regards,
Marco

---

### Post by Rockiger on 2009-01-28
Does anybody knows a way to isolate evolution-alarm-notify from the rest of evolution or knows an alternative to evolution-alarm-notify?

Rockin regards,
Marco

---

### Post by Lucre on 2009-03-28
Rockiger:

Where do you put the "evolution" file?  Is this just for if you've already removed evolution?

---

### Post by Rockiger on 2009-03-29
> **Lucre said:**
> Rockiger:

Where do you put the "evolution" file?  Is this just for if you've already removed evolution?

Yeah, it is assumed, that you removed evolution. But I personally changed back to evolution, the integration is works better for me

---

### Post by krevuru on 2009-04-12
Can you please elaborate the steps taken to get the GNOME-Applet to display Thunderbird appointments?
I had earlier uninstalled evolution components as much as possible. (After a point if you try to uninstall any of the most-necessary evolution components it says it will install the UBUNTU desktop as well, till that point).
After seeing this post, I checked the evolution components that I had and I saw that I only have evolution-data-server-common and not the  evolution-data-server as described on the addon site. 
I tried to reinstall the evolution and then installed the extension to my TB2. 
But I still do not see appointments in my GNOME-Applet. Any step I am missing here?
Please reply. Thanks in advance.

---

### Post by Teester on 2009-04-13
Krevuru,

Make sure that you've run Evolution at least once.  Evolution has a number of things to do to Evolution data server the first time that it runs such as setting up default calendars and address books.  If that isn't done, then requests by Evolution Mirror to do stuff to the default calendar get ignored (because there's no default calendar).  Try altering an event in Thunderbird then and see if it shows up in the clock applet.

Another thing you may want to do is set Evolution Mirror back to "first run" state (where it adds all the events to the Evolution Data Server on its first run).  Go to **Edit > Preferences > Advanced > General > Config Editor** in Thunderbird.  Click **I'll be careful, I promise** and then type **evolution** into the filter box.  Double click on **extensions.evolutionmirror.firstrun** to change it's value to **true** and restart Thunderbird.  All your existing events should get added to the clock applet then.

Praying to something while you're doing this will probably do no harm either :)

---

### Post by krevuru on 2009-04-19
[COLOR="Black"]**_Thanks Teester, this works and works perfectly._**[/COLOR]
One thing I want to ask you is I installed Evolution and did exactly as you said - Ran Evolution, to set up Calendar preferences, and other alarm display options.
I want to ask you one more thing here. Do I need to keep Evolution installed after doing the initial configuration or can I un-install it later.
[COLOR="Black"]**_BTW, Thanks a kilo for this extension, it helps migration to Ubuntu worth one more._**[/COLOR]

---

### Post by Teester on 2009-04-19
> **krevuru said:**
> [COLOR="Black"]
I want to ask you one more thing here. Do I need to keep Evolution installed after doing the initial configuration or can I un-install it later.[/COLOR]


I've never tried uninstalling Evolution, but by the sounds of what Rockiger did, as long as evolution-data-server is still around, then the items should show up in the clock applet.  The only problem he had was that evolution-alarm-notify won't work without Evolution, so alarms would not show up unless Thunderbird is running.

---

### Post by unikuser on 2009-05-13
I am using "Evolution Mirror" and is working. 

But, it is having problem with timezone. If the event is in another timezone, then it is adding the event "as it is" without converting the event in the my timezone.

Anyone know of any fix for this?

---

### Post by jeremy on 2009-07-16
I also have noticed the timezone problem. It would be nice to have an option to chamge that, ie, all appointments show at eg. +2 (or -11) hours.

---

### Post by de_mts on 2009-08-07
Hi

I like the lightning addon but is it possible to use the edit button to make changes in the calendar? Or like it is with evolution when you dubble click it te calender opens?

---

### Post by M20554443 on 2009-11-02
Anyone running this with Karmic's evolutuion? For me it does not work (Sunbird 0.9 and Evolution Mirror 0.2.1); the calender items do not appear in evolution calender / clock applet.

---

### Post by M20554443 on 2009-11-04
Evolution Mirror: sorry, I forgot to install python-gnome2-desktop. It works again - nice addon!

---

### Post by zasq on 2009-11-07
Hi M...,
I am trying to use this with karmic and have python-gnome2-desktop installed but it still doesn't work. It used to work with jaunty though. I have a 64-bit-system. Could that be the problem?

---

### Post by M20554443 on 2009-11-07
Hi zasq,

just to be sure, you didn't remove evolution, did you? Did you already try the hints from one of the previous posts by Teester (author of the addon btw)?

> Make sure that you've run Evolution at least once. I am pretty sure you also need the default calender in evolution, so don't delete it (I did before running evo mirror the first time ;)).

> Another thing you may want to do is set Evolution Mirror back to "first run" state (where it adds all the events to the Evolution Data Server on its first run). Go to **Edit > Preferences > Advanced > General > Config Editor** in Thunderbird.  Click **I'll be careful, I promise** and then type **evolution** into the filter box.  Double click on **extensions.evolutionmirror.firstrun** to change it's value to **true** and restart Thunderbird.  All your existing events should get added to the clock applet then.If that doesn't help, maybe it is an issue with 64-bit, I don't know (am running 32-bit system)
Good luck!

---

### Post by Teester on 2009-11-07
Zasq,

You may also want to make sure that python-evolution is installed on your system.

---

### Post by Ubunthree on 2009-11-08
I have run into an issue with Lightning's calendar, on two separate installations, which limits my confidence in it until I can understand why it happens and, ideally, how to fix it. I started a thread on this here, with a screenshot of what's happening:

[http://ubuntuforums.org/showthread.php?t=1313735](http://ubuntuforums.org/showthread.php?t=1313735)

No replies there as I write this. Anyone have any thoughts?

Edit:
My calendar issue appears to be fixed in Lightning 1.0, which works with Tbird 3 Beta. Until both are out of Beta, though, I think I'll continue using Evolution.

---

### Post by october1917 on 2009-11-19
Hello.

I think we should all vote for [this entry](http://brainstorm.ubuntu.com/idea/22356/) at ubuntu brainstorming

---

### Post by kimharding on 2009-11-20
> **Teester said:**
> Zasq,

You may also want to make sure that python-evolution is installed on your system.

> **M20554443 said:**
> Hi zasq,

just to be sure, you didn't remove evolution, did you? Did you already try the hints from one of the previous posts by Teester (author of the addon btw)?

I am pretty sure you also need the default calender in evolution, so don't delete it (I did before running evo mirror the first time ;)).

If that doesn't help, maybe it is an issue with 64-bit, I don't know (am running 32-bit system)
Good luck!

Thanks that works for me in Karmic... :D

---

### Post by el cameleon on 2010-01-01
Hi,
This add-on seems great but I couldn't succeed to have my events store in Lightning replicate on Evolution, and consequently to the Gnome Clock Applet.

I use Ubuntu Karmic, Thunderbird 3.0 and Lightning compilation from the 30 December.
Is there anything I can test to be sure that the add-on is functional?

Note that I see this error message in terminal after Thunderbird start:
> Traceback (most recent call last):
  File "/home/vincent/.thunderbird/sqjerkx8.Vincent/extensions/{531b5d09-9f8e-452b-8681-2fc03c9c150e}/chrome/content/eventcreate.py", line 5, in <module>
    import evolution
ImportError: No module named evolution

It could explain why it doesn't work, but I wonder how to fix it...

---

### Post by el cameleon on 2010-01-02
My problem has been solved with the help of the add-on developper: it is requested to install  "python-evolution" package with Synaptic on Ubuntu Karmic (seems it was not the case before).

---

### Post by 69dragons on 2010-01-15
I get this error when I start TB3.

"Error: uncaught exception: [Exception... "Component returned failure code: 0x8000ffff (NS_ERROR_UNEXPECTED) [nsIPrefBranch.getBoolPref]"  nsresult: "0x8000ffff (NS_ERROR_UNEXPECTED)"  location: "JS frame :: chrome://emirror/content/overlay.js :: setupCalendar :: line 15"  data: no]"

And I get no appointments in the system clock panel. I am somewhat of a n00b to Ubuntu, but tried all of the solutions here since Karmic has been released and still no luck.

---

### Post by kkinder on 2010-02-01
I thought I would chip in and add my voice to the users who are a little unimpressed with somehow syncing Thunderbird to evolution and having calendar events show up that way. If you aren't using Evolution and you are using Thunderbird/Sunbird, you should be able to apt-get remove evolution and not look back.

OT: You should be able to launch the event-creation GUI from the calendar applet, be it a GUI in Thunderbird, Sunbird, Evolution, or even a Google Calendar Prism.

I'm not much of a desktop software developer, but I might consider writing a calendar applet from scratch in Python that just provides hooks for your preferred calendar app.

---

### Post by Thelasko on 2010-02-01
Ooh, I just noticed this Thunderbird plugin now supports 64-bit.  Thanks! :P

---

### Post by c.zach on 2010-05-24
> **de_mts said:**
> Hi

I like the lightning addon but is it possible to use the edit button to make changes in the calendar? Or like it is with evolution when you dubble click it te calender opens?

I use sunbird and my solution is to rename /usr/bin/evolution (to for example /usr/bin/evolution_original) and place there skript which calls sunbird instead. I use:

```
#!/bin/bash
x=$1
if [ "${x:13:9}" = "startdate" ] ; then
   year=${x:23:4}
   month=${x:27:2}
   day=${x:29:2}
   day=$((day + 1))
   sunbird -showdate $month"/"$day"/"$year
else
   sunbird
fi
```

I'm not sure about lightings parameters, but modifications shouldn't be difficult. Hope that helps.

PS: skript translates evolution parameters to sunbird parameters. For some reason (my) gnome calendar always asks for previous day thus the 'day=$((day + 1))' line...

---

### Post by Ron O on 2010-05-25
It's pretty bad when so many people want to ditch Evolution because the development team does not seem to pay much attention to community complaints. Evolution was one of the apps that made me switch from Ubuntu to Xubuntu 3 years ago, and now that I am back, I'm shocked that some of the same issues are still there, specifically:

It is too complicated- too many options and settings to go wrong. In the Windoze world, everyone uses Outlook Express and not full blown Outlook, if they can help it. Evolution is like Outlook, TBird is like Outlook Express.

My main complaint is that the Calendar alarms are still dysfunctional. If you miss an appointment because you went a few days without using your system, you are never alerted, and you may not take remedial action like apologize and reschedule.

Also, it seems that if you are not sitting at your computer when an alert is scheduled, you miss it. For example, I have a Doctor's appt. tomorrow at 10 AM. I have the alarm set to notify me one day in advance- 10 AM this morning. When I turned my system on at 8 PM tonight, I got no alert at all. Was I supposed to set the alarm for every hour leading up to the appointment? Maybe there is a way to do it, but it is just simpler to use Mozilla Sunbird instead of wrestling with a beast with more features (and pitfalls) than you need. In Sunbird, you check "persistent alarms" and you get notified at ANY time you turn on your system between the alarm time (a day ago) and the actual appt. And if you miss the appt., you find out the next time you turn on your system. Unfortunately Sunbird is not supposed to be compatible with Lucid and is not in Synaptic's repository.

I saw bug reports on this during the times of Feisty 7.04, and nothing has changed as far as I can see. Please correct me if I am missing something. Why can't Evolution deal with these issues and perhaps lean out their application a bit as well. How about "Evolution Express".

---

### Post by HyperFlexed on 2010-06-13
I've tried installing the extension to synchronize TB with gnome-clock. No bones. I'd much rather have an easy to access calendar than all this silly Ubuntu One thing and crappy default skin they've packed into Lucid.

---

### Post by mark.c.fernando on 2010-06-14
I am running Ubuntu 10.04 64 bit with Thunderbird 3.0.4 and Lightning 1.0b1 and got the sync with the Ubuntu Gnome clock applet without Evolution.

I installed the Evolution Mirror 0.2.1 extension from the following site:
[URL="https://addons.mozilla.org/en-US/thunderbird/addon/9656/"]
https://addons.mozilla.org/en-US/thunderbird/addon/9656/[/URL]

Any meetings added to my Lightning calendar are reflected in the Gnome clock applet. I uninstalled Evolution a while back but guess the Evolution Database Server is one of those core bits that is not un-installed with the rest of Evolution.

Hope this helps you all.

---

### Post by HyperFlexed on 2010-06-15
> **mark.c.fernando said:**
> I am running Ubuntu 10.04 64 bit with Thunderbird 3.0.4 and Lightning 1.0b1 and got the sync with the Ubuntu Gnome clock applet without Evolution.

I installed the Evolution Mirror 0.2.1 extension from the following site:
[URL="https://addons.mozilla.org/en-US/thunderbird/addon/9656/"]
https://addons.mozilla.org/en-US/thunderbird/addon/9656/[/URL]

Any meetings added to my Lightning calendar are reflected in the Gnome clock applet. I uninstalled Evolution a while back but guess the Evolution Database Server is one of those core bits that is not un-installed with the rest of Evolution.

Hope this helps you all.

I've tried that plugin without success. evolution database server is installed. I notice there are many evolution-data* packages. Could you tell me which you have installed?

EDIT: I tried installing all of them, and now I get appointments. Now if only I could get it working to sync with Pimlico Tasks as it would do automatically in 9.10. I hate how "upgrading" sends you back to the stone ages. Oh well, thank god this is a LTS release.

---

### Post by Thelasko on 2010-06-15
> **mark.c.fernando said:**
> I am running Ubuntu 10.04 64 bit with Thunderbird 3.0.4 and Lightning 1.0b1 and got the sync with the Ubuntu Gnome clock applet without Evolution.

I installed the Evolution Mirror 0.2.1 extension from the following site:
[URL="https://addons.mozilla.org/en-US/thunderbird/addon/9656/"]
https://addons.mozilla.org/en-US/thunderbird/addon/9656/[/URL]

Any meetings added to my Lightning calendar are reflected in the Gnome clock applet. I uninstalled Evolution a while back but guess the Evolution Database Server is one of those core bits that is not un-installed with the rest of Evolution.

Hope this helps you all.

Where did you find Lightning for 64-bit?  It's not even in the repositories.

[Never Mind]("https://help.ubuntu.com/community/ThunderbirdLightning")

---

### Post by mark.c.fernando on 2010-07-19
You can find various versions of the Lightning extension from the Ubuntu Documentation site:

[https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

---

### Post by Ron O on 2010-07-21
mark- this link does not reference Lucid, and the lightning extension is not in Synaptic on a machine running Lucid 32 bit. Are you aware of anything more current?

Also, the Mozilla site says use
          o libstdc++5
            (Many modern Linux distributions only package libstdc++6, which is incompatible with Lightning. Therefore please install the package "libstdc++5" or "compat-libstdc++" on your system before installing Lightning)

++6 is in the repository and neither ++5 nor compat-libstdc++ are available.

---

### Post by duansai on 2010-07-22
Evolution mirror don't work in Ubuntu 10.04.

In there, I have thunderbird 3.1 and lightning 1.0b2.

The installation of evolution mirror is correct. But it just don't work.

Can anyone give me some suggestions?

Regards.

---

### Post by komputes on 2010-08-03
Nothing seems to happen when using Evolution Mirror in Lucid.

Any other proposed solutions to this issue yet?

---

### Post by aldeby on 2010-08-05
It's a shame that nobody cares about Thunderbird integration into Gnome. 

Evolution is not as versatile software as Mozilla Thunderbird is, despite having some good points overall is just crappy. Now I'm not willing to flame on Evolution, however it would be wise if Gnome/Ubuntu developers focus on the **functional integration **between most popular software of daily use rather than only on graphical aspects (i.e. system tray integration) which may be good but are definitely not crucial!

---

### Post by vnkatesh on 2010-09-06
Workaround:

I'm using TB 3.1.2 and Ubuntu Lucid 32bit. Lightning 1.0b2

This is a collective effort, after reading all the entries in this thread.

It may or may not work.

I have EDS [Evolution-data-server] package installed, along with python-evolution. You need to run evolution once before all the steps first.

Assuming your lightning calendar is local and on the network [You created a network .ics calendar with file:/// as the calendar URL]. If not, then first export your existing calendar that you use, and then use that again as the network calendar.

Then, use one of the previous post methods,
evolution -force-shutdown
rm /home/userid/.evolution/calendar/local/system/calendar.ics
ln -s <network-file:///calendar-location>/calendar.ics /home/userid/.evolution/calendar/local/system/calendar.ics

Use gconf-editor to edit /apps/evolution/calendar "sources" edit the local "On this computer" entry to add a refresh property value of 15 (minutes), check the other entries also.

Now run evolution again and close it.

Making any changes to the calendar via lightning should reflect in the gnome-clock panel calendar by around 15 minutes.

---

### Post by Ordes on 2010-10-12
> **vnkatesh said:**
> 
ln -s <network-file:///calendar-location>/calendar.ics /home/userid/.evolution/calendar/local/system/calendar.ics

hi vnk,

ur approach looks good, however i am wondering where u found the TB cal.ics; i thought lightning (using 1.02b) is safing its calendars in local.sqlite (tb-profile/calendar-data). or is there another *.ics file somewhere to look for? i looked in the extension folder itself as in the "calendar-data" folder, but couldnt find any .ics; where did u find yours?

txs

---

### Post by adad on 2010-10-13
I installed lightning in 10.04 and 10.10 using this guide:

[http://brizoma.wordpress.com/2010/10/13/sunbird-and-lightning-removed-from-ubuntu-10-10-maverick-meerkat/](http://brizoma.wordpress.com/2010/10/13/sunbird-and-lightning-removed-from-ubuntu-10-10-maverick-meerkat/)

---

### Post by vnkatesh on 2010-10-14
Hey Ordes.

As I mentioned before, "Assuming your lightning calendar is local and on the network [You created a network .ics calendar with file:/// as the calendar URL]. If not, then first export your existing calendar that you use, and then use that again as the network calendar"

Elaborating:

If you create a new calendar, as a network calendar, and then give file:///home/<userid>/.thunderbird/calendar.ics as the file, then, you basically have a calendar.ics which is read from the filesystem!

Now, if you already have a full working calendar, then, first export/publish that calendar. Create the new network-file:/// calendar, and then replace (mv) the published .ics to the file:/// location.

Hope it helps, let me know if you have more queries.

---

### Post by agustinalarconmuller on 2010-10-23
Hi,
I've also been interested in this subject for several weeks too.
I tried :

[LIST]
[*]Evolution Mirror plugin, which just does not seem to work for me, despite all I tried to do.
[*]The workaround proposed by vnkatesh, which did not work for me, but certainly beause I didn't knew exactly how to add te refresh value in gconf-editor
[*]Creating a network calendar in Thunderbird, create a Calendar in Evolution, and then real-time syncing the two folders in which the calendars where situated with Realtime Sync, from FreeFile Sync. It seemed to work at first, but then, when I modified again my Thunderbird/Lightning calendar, the changes would'nt appear in the gnome clock applet.
[/LIST]
And now, finally, I came with a kind of workaround which is pretty simple in fact, and seems to be perfectly working for now two days.
Two simple steps :

[LIST=1]
[*]You create a network calendar in Thunderbird / Lightning. Let's say you create it in /home/<userid>/.thunderbird/<thunderbird profile id>/calendars
[*]You create a calendar within Evolution... and tell Evolution it is in the exact same place the calendar you just created in Thunderbird.
[/LIST]
Now, just everything I change in my Thunderbird calendar almost immediately shows in the Gnome clock applet. And I can modify my appointments with Evolution, accesed by the gnome clock applet, afterthat I just need to tell TB to sync distant agendas and.. voilà !

Hope this helps

Config : 


[LIST]
[*]Ubuntu 10.04
[*]Thunderbird 3.0.9 / Lightning 1.0b1
[/LIST]

---

### Post by agustinalarconmuller on 2010-10-23
Well...
Sorry, but it seems I didn't get a look around too deeply.. in fact, it does not seem to wok adequately.
Don't know why, yet. I will ty to get it fixed, but I think it's a good idea. Has anyone tried this yet ? Is there a reason why I shouldn't be doing this ? (Perhaps it could never work for a reason I ignore ?)

---

### Post by Ordes on 2010-10-23
:) ah ok. i now see what u doing. u basicly create a new ics-cal by making a network calendar. 

also the method mentioned before, using evolutuion to create the basic ics-cal and than using the TB network method to have them in TB is a nice workaround.

however when also using google calendar it gets tricky. was using auto-export before to get my ics. but it seems to not be update for TB 3.1..

---

### Post by Teester on 2010-10-23
For anyone having problems using the Evolution Mirror addon for Lightning, ensure that you have the 'python-evolution' package installed on your system, or it won't do anything. 'python-evolution' can be installed through Ubuntu Software Centre (it's one of the hidden technical items if you search for it), Synaptic Package Manager or via the terminal using:
```
sudo apt-get install python-evolution
```
I noticed that during the upgrade from Lucid to Maverick, the package was removed and when I re-added it, Evolution Mirror started working properly again.

---

### Post by agustinalarconmuller on 2010-10-23
I have python-evolution installed, and as other people have yet told here Evolution Mirror is not working.
I assume it depends on the TB version you're using

---

### Post by vnkatesh on 2010-10-26
I'm tempted to try out agustinalarconmuller's workaround... but I've got things set up and don't want to mess with it :)

---

### Post by agustinalarconmuller on 2010-10-27
Vnkatesh, do as I do, make a backup first... but I think you don't need such a simple advice :)

Well, for now it's pretty much working. 
Two issues however :

[LIST=1]
[*]You can't modify your calendar from within Evolution. It's forced read-only, and you can't change that. At least, every time I tried to untick the "Force read-only" option, it did let me untick it, but still I couldn't change anything to the calendar. Trying to restart Evolution just made the option checked again.
[*]When you define a "recursive" event (sorry, I hope that's the word, I'm not a native english speaker..) in Lightning, and than you then manually change or delete some one of those events, Evolution does not "see" the change
[/LIST]
          For example : I am a teacher, and I use a calendar to record all my lessons. As with the last version of Lightning I had trouble defining those recursive events, I didn't indicate an end date, and only manually deleted lessons during holidays. Now, according to Evolution, the lessons are still here

I don't know if I make myself clear, it seems to me that these kind of explanations are far beyond my poor english level.
If you want, I can try and explain you in french or spanish :P

---

### Post by vnkatesh on 2010-10-27
By "recursive events", I think agustinalarconmuller means "repeating events".

I will try your method (next monday). I will post back as to if I find your method easier, better than my workaround :)

For a french guy, vouz anglais est par excellence.

---

### Post by piggyslasher on 2011-02-13
If you use the method I described in my blog, you'll be able to achieve this. Its towards the end of the post.

[www.techgarten.com/ubuntu/replace-evolution-thunderbird-completely-ubuntu/](www.techgarten.com/ubuntu/replace-evolution-thunderbird-completely-ubuntu/)

---

### Post by Habitual on 2011-02-13
PiggySlasher:

The technique/method described at [http://www.techgarten.com/ubuntu/replace-evolution-thunderbird-completely-ubuntu/](http://www.techgarten.com/ubuntu/replace-evolution-thunderbird-completely-ubuntu/) compatible with AWN 0.4.0?


Tbird 3.1.7

Thanks.

---

### Post by jasmines on 2011-08-30
I installed Evolution Mirror 0.2.3 extension on TB 6.0, restarted TB.
Started Evolution, I saw all the events of calendar in Gnome applet.
Removed Evolution, everything vanished.
I'm wondering what Evolution Mirror is doing...!?

Here some terminal hints, please help!

```
[calTimezoneService] using /home/xxx/.thunderbird/xxx.default/extensions/{e2fda1a4-762b-4020-b5ad-a41df1933103}/timezones.sqlite
[calTimezoneService] timezones version: 1.2011b
Traceback (most recent call last):
  File "/usr/share/xul-ext/indicator/python/indicator.py", line 109, in timeout
    srv.add_action("Contacts", action_addressbook)
  File "/usr/share/xul-ext/indicator/python/indicator.py", line 52, in add_action
    gobject.idle_add(self.app_indicator.set_menu, self.menu)
AttributeError: MessagingServer instance has no attribute 'app_indicator'

```

---

### Post by tuxor1337 on 2011-11-14
No news here?

---

