---
title: "[SOLVED] Evolution Wont support UTC Time?"
date: 2008-03-12
forum: General Help
---

### Post by locky28 on 2008-03-12
Hi All,

I'm having problems with Evolution having the right time zone setting. I'm on the East Coast of Australia and have my time zone set to Australia/Brisbane which is GMT+10 I believe.

Now I have the box for 'Use UTC' ticked when I right click the Time/Date and go to preferences and that makes the Time perfect, it's exactly what I have in my BIOS and is what Windows XP shows when I dual boot into that.

However the Evolution Email client is not so compliant. I have selected what I think is the correct timezone (Australia/Brisbane) in Evolution through the settings however my emails that I say for example received today are being given a time stamp for yesterday afternoon. It's not really a big issue however it is annoying having to look through the HTML headers to find the correct date.

Does anybody know a fix?

*I just noticed in the timezone setting there is in option for just UTC, rather than Australia/Brisbane so I'll try that out*

---

### Post by Zill on 2008-03-12
locky28:  Just a guess but I don't think you want "use UTC" set in the Gnome Time/Date applet.  UTC (Coordinated Universal Time) = GMT (Greenwich Mean Time) so I don't think this should be set for Australia!.  If you unset this option does Evolution then show the correct local time?

---

### Post by locky28 on 2008-03-12
I'm not sure what that'll do for evolution but if I untick UTC in the gnome clock then the time is wrong.

---

### Post by Zill on 2008-03-13
locky28:  It seems that either your system clock (as seen in the BIOS) is **not** set to UTC (GMT - London), or the local time zone is set incorrectly.

I suggest you first ensure that your system clock is set to UTC and then check the local Time Zone via the Time/Date applet which should allow you to change this to Australia if necessary.  I believe it will then be necessary to **uncheck** the "Use UTC" box here to show the correct local time.

If you check file /etc/default/rcS it should contain the following lines:
```
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes
```

[This link]("https://help.ubuntu.com/community/UbuntuTime") may help explain things ;-)

Then go to Evolution preferences, Calendar and Tasks and ensure/change the Time Zone to Australia.

Hopefully, this will work - but as I live in the UK, GMT is my home time zone so it is difficult for me to test :confused:

---

### Post by locky28 on 2008-03-24
> **Zill said:**
> locky28:  It seems that either your system clock (as seen in the BIOS)


I think your right with that one, though since it is only BIOS I don't expect it to be able to support UTC as it's really just, well a dumb clock.

When I **don't** have UTC ticked then manually configure the time withing gnome so it's correct then Evolution DOES show the correct time for sending/receiving mails. However after I do this when I look at my BIOS or Windows clock they are both incorrect.

Now when I **tick** UTC then manually configure the time in gnome my gnome clock is correct and is the same as my BIOS/Windows one. However this means that Evolution shows the wrong time on Sending/Receiving.

So the Ideal solution would be if when I ticked Use UTC in Gnome, then Evolution Automatically started using UTC, but that doesn't seem to be happening.

At the moment I have Use UTC ticked and the time is correct in Gnome/Bios/Windows, but not Evolution :(

---

### Post by dcstar on 2008-03-24
> **locky28 said:**
> ......
At the moment I have Use UTC ticked and the time is correct in Gnome/Bios/Windows, but not Evolution :(

Evolution uses the correct offset from UTC as set by your locale.

If you tick "Use UTC" and you system does not display UTC time (i.e. it displays local time), then your system is wrong.

Your Windows is set to the wrong time zone so it sets your BIOS to the wrong time, which sets your Ubuntu to the wrong time.

Fix the source of the problem and everything will be correct.

---

### Post by Zill on 2008-03-24
> **locky28 said:**
> I think your right with that one, though since it is only BIOS I don't expect it to be able to support UTC as it's really just, well a dumb clock...
Just to clarify, UTC = GMT = London(UK) time.  UTC does **not** mean *local time* (i.e. Australian time).

Your BIOS (hardware clock) can be set to any time you like but it should best be set to UTC and then set local time with the OS.  One advantage is that local DST will then change automatically.

dcstar has given you the correct advice.  With the BIOS set to UTC, Ubuntu will show the right time and Windows will show the wrong time until you set Windows correctly :-)

---

### Post by daniel. on 2008-03-24
I am having the exact same problem (except w/ Thunderbird instead of Evolution) and would appreciate any additional help.

I am a little confused by dcstar's and Zill's remarks, which seem to locate the source of the problem in some misconfiguration of Windows.

dcstar:
> If you tick "Use UTC" and you system does not display UTC time (i.e. it displays local time), then your system is wrong.

Your Windows is set to the wrong time zone so it sets your BIOS to the wrong time, which sets your Ubuntu to the wrong time.


The problem is that when I tick UTC time I *do* get the correct time. Yet when I login to the BIOS setup that is also correct (not UTC). In fact, ticking UTC is the only way I can get Windows and Ubuntu to agree. 

Zill:
> With the BIOS set to UTC, Ubuntu will show the right time and Windows will show the wrong time until you set Windows correctly

What, exactly, do you mean by setting windows correctly? What timezone.


Right now, for example, I have Windows set to Pacific timezone - it shows the correct time. My BIOS shows the same time. Ubuntu is set to Pacific time, and UTC IS TICKED, and it shows the correct time. Why is there not an offset here? THEN Thunderbird shows a different time.

This situation seems completely bizarre to me. Am I missing something obvious?

Thanks for your help,

Daniel

---

### Post by dcstar on 2008-03-25
> **daniel. said:**
> 
.........
This situation seems completely bizarre to me. Am I missing something obvious?


In a terminal:

```
tzselect
```

and go through the selection process, the last step should be something like this (on my system):

```
The following information has been given:

        Australia
        Victoria

Therefore TZ='Australia/Melbourne' will be used.
Local time is now:      Tue Mar 25 17:46:58 EST 2008.
Universal Time is now:  Tue Mar 25 06:46:58 UTC 2008.
Is the above information OK?
1) Yes
2) No
```

Which shows how things should be.

---

### Post by dcstar on 2008-03-25
> **daniel. said:**
> 
.......
What, exactly, do you mean by setting windows correctly? What timezone.
.........

Effn useless Windows:

[http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx](http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx)

---

### Post by locky28 on 2008-03-25
I thought that we DIDN'T want to use UTC?

A big fact that's sticking it's tounge out at me is that the BIOS and Windows have the same correct time without (presumingly) using UTC while Ubuntu, while also presumingly having UTC turned off has the wrong time. That's 2:1 for it being a problem within Ubuntu.

> Effn useless Windows:

[http://weblogs.asp.net/dfindley/arch...Pro_2900_.aspx](http://weblogs.asp.net/dfindley/arch...Pro_2900_.aspx)

That doesn't really fix anything more than it breaks the Windows clock and from the end of that blog it doesn't seem reliable at all. Also that still means the BIOS clock isn't the same as the other two.

It sort of seems to me like Ubuntu is automatically applying UTC, and when you tick the box to use UTC it turns it off again.

DCstar if there was a solution just like the one you just posted that worked for Ubuntu rather than XP than that would be ideal because I think that would be reversing the problem within Ubuntu.

---

### Post by Zill on 2008-03-25
> **daniel. said:**
> ...What, exactly, do you mean by setting windows correctly? What timezone.

Right now, for example, I have Windows set to Pacific timezone - it shows the correct time. My BIOS shows the same time. Ubuntu is set to Pacific time, and UTC IS TICKED, and it shows the correct time. Why is there not an offset here? THEN Thunderbird shows a different time...
UTC means Coordinated Universal Time which used to be called Greenwich Mean Time (GMT).  UTC/GMT is the current time in London (UK) at zero degrees Longitude.

Your [local timezone]("http://wwp.greenwichmeantime.com/time-zone/usa/pacific-time/") is apparently Pacific, which is 8 hours behind UTC/GMT in winter (PST) and 7 hours behind UTC/GMT in summer (PDT).

It is quite possible to set your PC system clock (BIOS) to either UTC or local time.  Windows often does set this to local time by default, but it is best to set this to UTC.

If you do set the system clock to UTC, rather than local time, then it is necessary to configure both Windows and Linux to use the correct **local** timezone.  The OS will then automatically apply the appropriate offset (i.e. 7 hours) to show the correct local time in both winter and summer.

As far as Ubuntu is concerned, you should **not** be displaying UTC, as this will be 7 hours ahead of your actual local time.  You should only display your local time, which should be 7 hours behind UTC.

I am sure Windows will need a simple adjustment to also work correctly with a UTC system clock - check the built-in help and Windows forums if further help is needed.

---

### Post by daniel. on 2008-03-25
locky28:

> I thought that we DIDN'T want to use UTC?

dcstar and Zill have been offering solutions to you based upon the BIOS clock being set to UTC - this is, for various reasons, "the way it should be."

> A big fact that's sticking it's tounge out at me is that the BIOS and Windows have the same correct time without (presumingly) using UTC while Ubuntu, while also presumingly having UTC turned off has the wrong time. That's 2:1 for it being a problem within Ubuntu.

If you want everything on local time, did you try setting utc=no in /etc/default/rcS as per [_this thread_]("http://ubuntuforums.org/showthread.php?t=6285") and then unticking 'use UTC'? I made the mistake of thinking that the tickbox and rcS did the same thing.

Zill:

> I am sure Windows will need a simple adjustment to also work correctly with a UTC system clock

One would think so, wouldn't they? No, the idea of being able to set the system clock to UTC apparently escaped the puppet masters at Microsoft.

> Check the built-in help and Windows forums if further help is needed

Fair enough. I'm convinced Ubuntu is handling things correctly - and a quick mailbomb to Redmond will at least relieve some stress. Then maybe I'll hit the Windows forums.

Thanks dcstar, Zill,

Daniel

---

### Post by dcstar on 2008-03-26
> **daniel. said:**
> locky28:

dcstar and Zill have been offering solutions to you based upon the BIOS clock being set to UTC - this is, for various reasons, "the way it should be."


And you shouldn't need to use UTC at all for the local BIOS time.

I have just checked my system and the BIOS is running local time, my system timezone (through tzedit) is correct, my /etc/default/rcS has UTC=no so Ubuntu will make the correct adjustment for the UTC time it gets from the timeservers I have set up in NTP (AFAIK this is the default setting - unless you answered a question incorrectly during install).

My Gnome time and date preferences has "Use UTC" unticked, so all my times are displayed correctly.

My Evolution is set to the correct time zone in Preferences-Calendar and Tasks-General, so it works fine as well.

---

### Post by locky28 on 2008-03-26
> **daniel. said:**
> 
If you want everything on local time, did you try setting utc=no in /etc/default/rcS as per [_this thread_]("http://ubuntuforums.org/showthread.php?t=6285") and then unticking 'use UTC'? I made the mistake of thinking that the tickbox and rcS did the same thing.
Daniel

=WIN!

Thanks very much mate that fix looks to be the go so far! UTC was set to yes when I opened the file (UTC was and is UNticked in the gnome clock) so I changed the setting to NO and now everything seems to be synchronised correctly including Evolution!

Also is it possible for you to explain what this actually did just to satisfy my curiosity? I see you said that you made the mistake of thinking rcS and the tickbox are the same thing, what's different about them? and what is rcS?

Thanks again,

Locky.

---

