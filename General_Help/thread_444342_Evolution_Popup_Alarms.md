---
title: "Evolution Popup Alarms"
date: 2007-05-15
forum: General Help
---

### Post by casperlingus on 2007-05-15
I deeply deeply apologize I did not look exhaustively for a a solution to this, but because I don't have time.  I just installed Feisty on my work laptop, and I have missed 2 meetings in the last two days because Evolution does not put up a static popup alarm.  This is not good, and I need a solution ASAP.

I have tested it and found it puts a popup in the LOWER RIGHT corner of my secondary monitor on the right, and only for about 5 seconds.   I don't spend much time at my desk, usually I just drop in to check my email.  I NEED to have a popup like outlook does it which gets in your face and doesn't go away until you explicitly tell it to.  The 5-second popup is not sufficient, nor is the icon next to the system time (but the window you get when you click the tray icon is perfect).   Honestly I have become totally dependent on these notifications, and *I will have to go back to windows if I can't get this fixed.*

My company uses an Exchange server, and as far as I know Evolution is the only linux mail client that works with Exchange.

Help!

-Casper

---

### Post by ayenack on 2007-05-16
This is the way I do it go into Calenders and make an appointment or meeting which brings up the appointments/meetings window click on alarms then customise this will bring up add alarms window click on repeat alarm in extra time change the number to something like 100 then 1 in the minutes this will display a notification every minute you should notice this.

Best of luck. ayenack.

---

### Post by hashstat on 2007-05-25
The following change causes the old-style dialog box to pop up instead of placing the notification in the tray.

Run the following command and uncheck the **notify_with_tray** box:
```
gconf-editor /apps/evolution/calendar/notify/notify_with_tray
```
You probably have to kill evolution and evolution-alarm-notify and then restart evolution for this to take effect.

---

### Post by casperlingus on 2007-06-01
Thanks!

This will be added to my list of small, obscure things in Ubuntu that are WAAAAY harder than they should be.
I *love* Ubuntu and I've been using it as my primary desktop for 2 years.  But, some things (like this) make me scratch my head and wonder how frustrated a newbie would be trying to figure it out.

-Casper

---

### Post by tytus on 2007-06-12
In addition to changing notify_with_try I had to add Calendar to /apps/evolution/calendar/notify/calendars. This list was empty for me....

---

### Post by casperlingus on 2007-06-18
What exactly did you add to the list?  I was expecting a drop-down menu to select the desired calendars, but this low-level operation does not give a list.   It's not obvious since there's multiple categories of calendars ("On This Computer", "Contacts", "Work").  How do I specify?  I tried "Calendar" but that did nothing.

I've figured out a "hack" to make sure I get pop-up alarms.  Anytime Evolution is restarted, I have to go into Edit->Preferences->Calendar&Tasks->Alarms(tab) and unclick-reclick each of my calendars.  Typically, I forget to do this, and as soon as I unclick-reclick the checkbox next to my work calendar I immediately get a popup window with all the notifications it hasn't displayed yet.  This is clearly a bug.

-Casper

---

