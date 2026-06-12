---
title: "Timezone Confusion"
date: 2008-05-12
forum: General Help
---

### Post by Zelandeth on 2008-05-12
Okay...this is slowly driving me insane!  I'm sure it's something mindlessly simple that I'm doing wrong...but I can't for the life of me figure it out.

Simply put - the clock in Ubuntu runs an hour slow...but it doesn't.

The clock on the toolbar runs an hour slow!  Note the preferences window open in the attached screenshot - it's normally set to automatically syncronise, I just set it to manual there to show the discrepency.

In Konversation, the timestamps show the correct time as well - it just seems to be the on-screen clock that's affected, and I'm at a complete loss as to how to go about sorting it!  Setting it an hour fast does work...but means that timestamps in anything else are an hour adrift...

Thoughts people?

---

### Post by Bruce M. on 2008-05-13
This is a shot in the dark here.

Right click on the clock in the Panel and check the properties, it should be the Calendar Settings, with that open check your "Time and Date settings". They may be different by one hour.

See if there is a "Daylight Savings Time" setting that is checked or not in either make sure they are the same. Is one set to UTC or Floating?

I'm running Xubuntu and have different programs than Ubuntu but one of them must be out by an hour.

>Applications > Settings > Calendar Settings
>Applications > System > Time and Date
plus the right click on the panel clock.

Hope this helps.
Bruce

---

### Post by Zelandeth on 2008-05-13
I've just chased these around for a bit.

The system clock, having no concept of BST, was indeed an hour slow.  Correcting this, rebooting into Ubuntu greeted me with the correct time...for about five seconds, until it jumped back to being an hour slow again.

I'm really starting to wonder whether this is something odd with Gnome.

If I set the time manually - no matter what I do, the time shown in the toolbar is consistently an hour behind what is shown in the time/date properties control panel.  There doesn't seem to be anywhere to set BST, it appears to be done automatically - what is interesting however, is that when the date is advanced to a point outside summer time - that the date shown on-screen and in the control panel then DO match.

Odd, and irritating.

---

### Post by Bruce M. on 2008-05-14
I'd be irritated enough to wake William Wallace from his grave.

Another shot in the dark here but have you seen these:

[UbuntuTime]("https://help.ubuntu.com/community/UbuntuTime")

[Time Synchronisation with NTP]("https://help.ubuntu.com/7.10/server/C/NTP.html")

I'm guessing you may have, but just on the off chance that you haven't.

ahhhh maybe this just saw it:

[Setting the time using the clock applet, shows authentication window below time settings window]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/200036")

Maybe I'm grabbing at straws here but I want to help.

Bruce

---

### Post by Zelandeth on 2008-05-14
Think we're getting closer - ran through everything in there, and have found out that the computer understands correctly what timezone it's in - the problem is that the clock applet is showing UTC.

...and I've not the foggiest idea how to tell it not to.  There was a checkbox for that in Gutsy - but there's not in Hardy as far as I can find.

It's obviously something happening during startup, as when I first login, the clock always shows the correct time for about five seconds before dropping back by an hour.

Hmm...more headscratching.

---

### Post by alexandremrj on 2008-05-14
I had the same problem with my hardy.

When you tell your ubuntu to sincronize with internet servers go and pick a new server, like london or something. Mine was with US first and the daylight savings was off, when changing the server then there stopped being a problem.

---

### Post by Bruce M. on 2008-05-14
> **Zelandeth said:**
> Think we're getting closer - ran through everything in there, and have found out that the computer understands correctly what timezone it's in - the problem is that the clock applet is showing UTC.

...and I've not the foggiest idea how to tell it not to.  There was a checkbox for that in Gutsy - but there's not in Hardy as far as I can find.

It's obviously something happening during startup, as when I first login, the clock always shows the correct time for about five seconds before dropping back by an hour.

Hmm...more headscratching.

As I recall when doing a clean install it asks you if you want to set the clock to UTC or Local. But it is strange indeed that there are "two" places to set the time and have the time showing as two different times..

Maybe what alexandremrj said above makes sense. Change your time sync server and see what happens... Strange indeed,

On my Xfce 7.10 system I have:
[LIST]
[*]Time and Date setting, and
[*]Calendar Setting
[/LIST]

In the first image on the left is the Time and Date setting. And on the right is the "Calendar Setting".

In the the "Calendar Setting" if I click on the [America/Buenos_Aires] the pop-up gives me the option to select a definate TimeZone: BsAs or [UTC] or [Floating] (second image)

Are you sure you don't have a setting like that for the "panel clock" in Gnome?

Anyway, like you said, we're getting close.

Have a great day.
Bruce

---

### Post by Zelandeth on 2008-05-15
Well, I never did find the actual solution - but another niggle (continuous thrashing of the harddrive) which had resisted all attempts to fix eventually led to me doing a clean install this evening.

The clock now works properly!

Installer didn't even glitch on me once either, bonus!

---

### Post by Bruce M. on 2008-05-15
> **Zelandeth said:**
> Well, I never did find the actual solution - but another niggle (continuous thrashing of the harddrive) which had resisted all attempts to fix eventually led to me doing a clean install this evening.

The clock now works properly!

Installer didn't even glitch on me once either, bonus!

GREAT news... Glad to hear it's fixed.

Not so happy about the method, but what works: Works!

Have a great day,
Bruce

---

