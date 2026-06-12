---
title: "Timezone wrong?"
date: 2022-11-07
forum: General Help
---

### Post by geordiejohn on 2022-11-07
Hello I have just installed xbuntu on my mac mini but the timezone is American,I managed to put get in but does anyone know how to set up as London please? 
Thank you.

---

### Post by Rex Bouwense on 2022-11-07
Xubuntu has a GUI for changing the date/time. Select Time and Date from the main menu.  Unlock the application and make the changes.

---

### Post by geordiejohn on 2022-11-07
Thank you.

---

### Post by TheFu on 2022-11-07
If the time and timezone are set wrong, you weren't paying attention during the installation.  Installation has about 5 questions and the timezone is one of those. It usually guesses well, based on the network IP address geo-location, but I suppose it could guess wrong for people on borders where the timezone changes.  

Ensure all the times in the hardware are stored as UTC, then each user can simply set the TZ environment variable for their ~/.bashrc or ~/.profile to control how times are displayed.  Sadly, there isn't just 1 place to control this stuff - I'm blaming the Gnome/Qt/GTK+ guys for confusing the issues, but it goes back to X/Windows and localization.

Remember that Linux is based on Unix and Unix is multi-user from the beginning with the expectation that users will be located around the world while each is concurrently connected to a single system.

So, that means there's multiple places where time is kept.
a) In the BIOS clock.  This should be UTC with local display in the BIOS set to whatever location the physical computer sits. [https://tldp.org/HOWTO/TimePrecision-HOWTO/set.html](https://tldp.org/HOWTO/TimePrecision-HOWTO/set.html)

b) In the OS.  This should be UTC with local display in the BIOS set to whatever location the physical computer sits.  /etc/timezone should be set for systemwide local time display and the default for everyone. [https://tldp.org/HOWTO/TimePrecision-HOWTO/set.html](https://tldp.org/HOWTO/TimePrecision-HOWTO/set.html)

c) Per userid, for text sessions ... like a console login and/or remote ssh session.  It picks up the OS time, but displays it based on the TZ environment variable.
```
$ egrep TZ  ~/.bashrc
export TZ="America/New_York"
```
You'd want, 
```
export TZ="Europe/London"
```
in that file, probably at the top. Again, this should only be necessary if the default OS setting isn't picked up correctly.

d) Per userid, for GUI Session (X/Windows, Wayland, Gnome, KDE, yadda, yadda, yadda).  There are usually "localization" settings with some GUI to control those.  Google for the "Desktop Guide" for the DE and release you are running.  "Kubuntu Desktop Guide 22.04" is an example google query. Then look for localization.  [https://help.ubuntu.com/stable/ubuntu-help/clock-timezone.html.en](https://help.ubuntu.com/stable/ubuntu-help/clock-timezone.html.en)  or set the clock manually [https://help.ubuntu.com/stable/ubuntu-help/clock-set.html.en](https://help.ubuntu.com/stable/ubuntu-help/clock-set.html.en)

I find it is best to start at the beginning "a", then "b". If those are each set, I can't remember needing to touch "c" or "d".

More .... probably just ignore:

Once you have these things set as needed, you'll want to ensure that your system keeps µsec (microsecond) accurate time.  [https://tldp.org/HOWTO/TimePrecision-HOWTO/ntp.html](https://tldp.org/HOWTO/TimePrecision-HOWTO/ntp.html) NTP is the protocol and we used ntpd for 40+ yrs to keep very accurate time between Unix systems world wide.  Most people don't need µsec accuracy and NTP has some attack vectors that are being addressed by newer protocols.  Today, there are mainly 3 different tools to keep accurate time sync on our systems.  ntp, chrony and systemd-timesyncd.  I think around 20.04, systemd-timesyncd became the default on Ubuntu. 
The config file is timesyncd.conf

 For whatever reason, timesyncd wasn't working well for me with my internal time server, so rather than go back to NTP, I chose to deploy chrony across all my systems.  Now it is part of my new system setup process and takes about 10 seconds.  Most people who are happy with 60 seconds of accuracy in their computer times wouldn't bother doing anything non-standard. timesyncd should easily be within that range, probably under 2 second accurate.
 MSFT thinks that ±5 minutes is accurate enough.  I spoke with a Microsoft engineer about exactly this issue when I was showing up to meetings late even with a 2 minute ahead reminder. The engineer asked corporate which responded with the ±5 minutes as being "good enough".  Unix systems have been sub-second accurate for as long as I've been using computers.  It is a solved problem for everyone else except that one OS.  At home, my main time server system here started as a Windows system. It was off over 15 minutes each day using the default weekly MSFT time setting over the internet.  I changed it to once per day - which made no difference. It was still off 15 minutes each 24 hours.  With time services, asking for the current time more than once a day if not using NTP is considered abusive, so my solution was to install an NTP server on a different system and have MS-Windows poll it hourly.  It was still losing a few minutes each hour!  Changed it to sync every 15 minutes and finally it was keeping time close enough to start and top TV recordings close enough.  At the time, I was using Windows media center.  The first time I'd seen this issue was in 1995 with Win95, so MSFT definitely knew it was a problem.  Eventually, I removed Windows from running directly on that hardware after getting a new Windows laptop and installed Ubuntu Server which never had any issue keeping time with the defaults.  The same exact hardware keeps time perfectly for my network 12+ yrs later.  It wasn't/isn't the hardware at fault.

You're lucky being in London with GMT/UTC.  When most of the world enables extra privacy settings in their browsers, the local time sent to webservers is UTC, which means anything shown in a website based on the local date-time will only be useful for people in UTC.  I get to subtract 5 hours from the returned information when privacy mode is enabled.

If you haven't been to the Royal Observatory in Greenwich, it is worth a 4 hr visit, for a nerd. Be certain to get the "tourist" photo standing on both sides of the prime meridian up the hill next to the telescopes too.  I did. ;)

Sorry, I get a bit excited about time and how humans came to an agreement about it for commerce, navigation, and rail schedules.

---

### Post by QIII on 2022-11-07
The history of making accurate marine timepieces for the navigation of rolling ships at sea is fascinating.  Determining latitude was a straight forward matter. Longitude, on the other hand, was not.  You might be sailing West along just the right latitude and come to an abrupt stop on the rocks because you sailed full-speed into land you thought was miles further ahead because you didn't know how far West you had come. The pendulum clock from the foyer of your manor house in the English countryside was entirely useless as the waves rocked a ship.  John Harrison won the £20,000 prize offered by virtue of the British Longitude Act with his H5 model in the last half of the 18th Century.  And remember, "computers" used to be the people who computed by hand the values that were set to paper in the books so that the navigator could look up the time and the readings from his instruments to determine his location.  Since Harrison was British and the award was British, the British chose the baseline, the origin, at Greenwich.

So people called "computers" and machines called "computers" fulfill the same roles.  In fact, human "computers" were used to cross-check calculations provided by the simple electronic computers used during the early days of the US Apollo program.

I like that geek stuff, too.

---

### Post by TheFu on 2022-11-07
Now you did it ...  100% off topic:

Harrison meet all the conditions with his H-4 chronometer, but the panel refused to pay the reward until Parliament acted 11 yrs later. It is a sad story because the politically powerful astronomers were the power-brokers on the committee.  For accurate time on ships, going smaller was better than going larger.  The Royal Observatory has multiple models of Harrison's time keepers, along with other clocks that are mesmerizing to watch at work.  

I inherited a huge Cherry Howard Miller grandfather clock that uses weights, gets wound weekly, and the pendulum has to be slightly adjusted quarterly as the temperature changes to stay within 2 minutes/week of accuracy.  Cleaning it and oiling that clock is a labor of love.  Hopefully, someone in the family will want it when I'm dead.  
Growing up, we also had a Black Forest Cuckoo  clock that had to hang high on a wall to give teh weights enough room to drop over the week.  It didn't keep great time, but was fun to watch. I prefer the hourly chimes from the grandfather clock.  The Cuckoo was killed in a move, I suppose. It was up in 1 house, then my parents moved and I don't remember seeing it again.  When I looked a few years ago to get one similar, they were much more expensive than I recall.  Think ours was about $80. A "cheap" replacement today seems to be in the $400 range with midlevel costing $800.

[https://www.imdb.com/title/tt0192263](https://www.imdb.com/title/tt0192263) is a 2-part TV Movie called "Longitude" 2000 - very interesting retelling of John Harrison's efforts. Recommended if you haven't seen it.  [https://en.wikipedia.org/wiki/History_of_longitude](https://en.wikipedia.org/wiki/History_of_longitude) explains the issue, if you aren't already familiar.

[https://www.imdb.com/title/tt4846340](https://www.imdb.com/title/tt4846340) "Hidden Figures"  2016 is a retelling of the Apollo era "computers" - a group of smart, black, women, who performed the orbital mechanics calculations for all aspects of Apollo flight.  It is behind streaming paywalls now (at least here).  It isn't Apollo 13, but still interesting.  When Apollo 13 was first released, I happened to be working at JSC on the FCR upgrade project (bldg 30S). Most of my team took Thursday afternoon off and went to watch the movie at the 2pm showing.  We worked all sorts of hours, so "flex time" wasn't an issue at all. Anyway, 2 rows behind me was Gene Kranz with a few other flight controllers.  He was retired then and I never worked with him. I didn't start that program until mid-1994. The movie theatre held about 400 people, with the vast majority being NASA employees and contractors who worked directly in the FCR and POCC environments.  Talk about an audience who was rooting for the movie!  It wasn't like everyone there didn't already know the outcome - heck, probably 20% of the audience lived it and were in the part of their careers were they were making big decisions for many different NASA programs.

Both of those movies show up on free streaming from time to time.  I know Longitude is in the Netflix DVD archives (not the streaming offers). It is available to rent from Amazon streaming in the USA.  I suspect anyone interested in NASA already saw Hidden Figures.

The Martian is pretty realistic, as is Europa Report. Of course, Martian storms are hard to estimate on Earth since the Martian atmosphere is 1% of that on Earth, so lots of things wouldn't be blown around without 20+x more wind.  Very tiny particles, sure, but nothing large.  Most popular movies trying to be set in the "near future" get the rocket science parts so very wrong that I can't suspend my belief and enjoy them.  Interstellar and Gravity both make me cringe.  So much of the rocket science in those is just wrong, wrong, wrong.  If the gravity on a planet is anywhere like it is on Earth, then you'll need a huge rocket to get off it.  Gravity impacts wave action, so waves wouldn't move like on a lake, they'd be much, much, much slower.  The movie people really need to get an engineer who can crunch the numbers before they make up this stuff.  It literally isn't rocket science 99.999% of the time.  Any mechanical engineer can crunch these numbers using simple 2nd order differential equations - no vector calculus or n-dimensional calculus necessary.  Heck, orbital mechanics has a little big of calculus, but approximate answers which would be close enough for a movie to be realistic using "rules of thumb" algebra are in wikipedia.

Most other movies are off in fantasy land ... sufficient that I can ignore the science mistakes because it is mostly wishful thinking.  Most of the other good Mars movies try hard to be close enough, but usually fail.  For example, "Red Planet" rocket science seems reasonable (it has been a few years), but the idea that a robot wouldn't have an off switch under local control is just crazy.  In human space flight stuff, there's a way for the local people to modify every single memory location on their computers.  It is seldom needed and a last resort, but it has been used on the Shuttle programs.  I don't know about the ISS - I didn't work on the flight computers in that program.  ("Program" is govt speak for Congressional funding item).  I did get funded by the ISS program, but I was working on non-flight control stuff then. Under the STS program, I did work on GN&C flight control stuff, directly.

---

### Post by QIII on 2022-11-07
Hmmm ... maybe providing a bit of background information might help inform the user's conceptualization of the issue at hand and make the solution more useful?  That's my story, anyway.  :P

---

