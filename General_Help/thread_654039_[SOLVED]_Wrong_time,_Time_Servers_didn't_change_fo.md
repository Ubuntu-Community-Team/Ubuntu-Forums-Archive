---
title: "[SOLVED] Wrong time, Time Servers didn't change for Agentina."
date: 2007-12-30
forum: General Help
---

### Post by Bruce M. on 2007-12-30
Hi Folks

Today ( 30 Dec 2007 ) my Ubuntu Clock is wrong.  For the first time since 2000 Argentina implimented DST, for this season, have no idea about next year.

30 Dec @24:00 +1 hr  /  16 Mar @24:00 -1 hr

I've trimmed the minutes, because as I type, the minutes go up.

See this:
[http://www.timeanddate.com/news/time/argentina-into-daylight-saving-time.html](http://www.timeanddate.com/news/time/argentina-into-daylight-saving-time.html)

I can see the jokes now:

Comes 16 Mar 2008 @24:00 people put their clocks back an hour
... and an hour later @24:00 people put their clocks back an hour.
... and an hour later @24:00 people put their clocks back an hour.
... and an hour late.....

Anyway, today:
My TV says it is 18:~~
Ubuntu says:  17:~~

[http://www.worldtimeserver.com/current_time_in_AR-BA.aspx](http://www.worldtimeserver.com/current_time_in_AR-BA.aspx)
The World Time Server says that in Buenos Aires Argentina it is now ( well was when I looked ): 4:~~ PM - Boy are those guys out to lunch!

[http://wwp.greenwichmeantime.com/time-zone/america/argentina/](http://wwp.greenwichmeantime.com/time-zone/america/argentina/)

says:  17:~~  (closer, equal to Ubuntu )

My Palm (set up to do a DST change last night) says: 18:~~ - before hotsync 
My Palm says: 18:~~ - after hotsync (it didn't get time from CPU) :(  It's supposed to!

When I go to >System>Administration>Time and Date to change the time, it points me to:

Time Zone: America/Argentina/Buenos_Aires
Configuration: Keep synchronized with Internet servers

and the wrong time.
I set the value to "manual", now I won't have a time server syncing my time.  :(

I'm really really glad I don't have Windows though:

[http://blogs.msdn.com/mthree/archive/2007/12/29/argentina-122907.aspx](http://blogs.msdn.com/mthree/archive/2007/12/29/argentina-122907.aspx)

WoW!  What a mess.

I want to use this but it's not a "time Server":
[http://www.timeanddate.com/worldclock/city.html?n=51](http://www.timeanddate.com/worldclock/city.html?n=51)
at least they have BsAs at the correct time.

So I need help setting up my time correctly.
Any ideas out threre?

Does anyone know of a "time server" in Argentina?

Thanks
Bruce

---

### Post by iris-n on 2007-12-30
I would just change to a Time Zone more to the East, i think São Paulo (GMT -2, BDST) would suffice.

And keep an eye on the updates, Venezuela got a fix quickly when it's time zone changed.

---

### Post by Bruce M. on 2007-12-30
> **iris-n said:**
> I would just change to a Time Zone more to the East, i think Brasilia or São Paulo would suffice.

And keep an eye on the updates, Venezuela got a fix quickly when it's time zone changed.

No no no, thats just too simple.
Going to do it now  :)

Thanks for the idea.  OK for the next little while I'll be living in São Paulo.  :guitar:

Ummmm, this is strange, I took it off manual and told Ubuntu to use a time server.
Clicked on São Paulo, and the time was an hour ahread of what I expected.
Put it back on Buenos Aires, and tresto!  21:03, the correct time.

So like you said:

> **iris-n said:**
> And keep an eye on the updates, Venezuela got a fix quickly when it's time zone changed.

WoW!  That was fast!

Thanks
Bruce

---

### Post by sergiom99 on 2008-01-03
In case I want to update the package manually (or in other distros), which one should I update to get the BUE time zone fixed??

Thanks!

---

### Post by Bruce M. on 2008-01-03
> **sergiom99 said:**
> In case I want to update the package manually (or in other distros), which one should I update to get the BUE time zone fixed??

Thanks!

Hola Sergio,

I'm syncing my time automatically.  On the morning of  the 30th the time was wrong, but it was "fixed" later in the day by the time server.  As you can see from my previous message.

Last night I had a "flashing" icon advising me of a new update: **tzdata** ~~>   to fix Argentina's DST problem.
I have no idea if this **tzdata** file is a generic, *good for everyone, everywhere fix*, or just for people in Argentina.

Do an update of **tzdata** file to see it works for you.

Also; I get my updates from the Ubuntu mirror here in Argentina: (see attached) or try manual search at: [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com)

Tengas un buen día.
Bruce

---

### Post by Bruce M. on 2008-01-03
**UPDATE: [COLOR="Blue"]tzdata[/COLOR] file**

Time Zone and Daylight Saving Time Data 
This package contains data that represent the history of local time for many
representative locations around the globe. It is updated periodically to
reflect changes made by political bodies to time zone boundaries, UTC offsets,
and daylight-saving rules

For Feisty users: Latest Version: 2007k-Oubuntu0.704 (feisty-updates)

It's generic - Misquote from LOTR:  One file for all!

Bruce

---

### Post by sergiom99 on 2008-01-03
thanks bruce! I updated it in Kubuntu and have yet to try in FC6.

gracias!

---

### Post by GLMnet on 2008-01-04
I am new to this apt-get thing:
I do a apt-get install tzdata and it sais: "tzdata is already the newest version"
I did the apt-get update

I do a apt-cache show tzdata and it says: "2007f-3ubuntu1"

what am I missing here?:)

---

### Post by Bruce M. on 2008-01-04
> **GLMnet said:**
> I am new to this apt-get thing:
I do a apt-get install tzdata and it sais: "tzdata is already the newest version"
I did the apt-get update

I do a apt-cache show tzdata and it says: "2007f-3ubuntu1"

what am I missing here?:)

Hi GLMnet

First things first. **Welcome to Ubuntu!**

What are you missing! Maybe nothing.

I'll bet you're clock is correct for whatever time zone you are in.  So there is no need to get another version.

Try this:

>System>Administration>Synaptic Package Manager
>Search  >> type in: tzdata
When it shows up, click on it once.

You'll see below [Description] <~~ what you're presently looking at.
and: [Common] [Dependencies] [Installed Files] [Version]

Click on [Versions] ~~> you see what versions you have (had) installed.

As you can see from the image below, I've never had your version: 2007f-3ubuntu1

I clicked on, Main Menu: [Package] and scrolled down to [Force Version] to show you the pop up window.

So my educated guess here is, what tzdata file you have depends on which time zone you are in.

Have a great day
Bruce

---

