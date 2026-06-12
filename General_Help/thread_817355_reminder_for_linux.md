---
title: "reminder for linux?"
date: 2008-06-03
forum: General Help
---

### Post by wwuster on 2008-06-03
I'm looking for a linux program that will remind me to do stuff every other Monday, eg. I need it to put up a window on my screen at 8:00 am and keep it there until I close it. Or it could write to whatever terminal I'm on in a way that I can't miss the reminder. Is there such a program?

thanks,
William

---

### Post by strider1551 on 2008-06-04
A quick search came up with two possibilities: [KAlarm]("http://www.astrojar.org.uk/kalarm/") and [plan]("http://me.in-berlin.de/~bitrot/plan.html").

---

### Post by wwuster on 2008-06-11
> **strider1551 said:**
> A quick search came up with two possibilities: [KAlarm]("http://www.astrojar.org.uk/kalarm/") and [plan]("http://me.in-berlin.de/~bitrot/plan.html").

I finally settled on a combination of cron, a small php script which launches gmessage like this:

```
function message($str)  {
	system("/usr/bin/gmessage -display :0.0 -center -geometry 800x400 -borderless -bg \"#000000\" -fg \"#00ff00\"  -font \"40\" $str");
	return;
}
```

You can add any logic you want in the php script to control when gmessage is run.

William

---

### Post by editrix on 2008-06-11
If you can run Firefox, there's a nifty extension called ReminderFox.

Korganizer works beautifully for this kind of thing, and Evolution may have something similar.

---

### Post by DexterLB on 2008-06-11
How about evolution's alarm?

---

### Post by KingTermite on 2008-06-11
I just set one up with a script and using osd_cat (got the template for the script in "Linux Desktop hacks").

osd_cat will put the reminder on your screen no matter where you are as a "on screen display", not a window. That way it can't be hidden. It comes up much like the volume bar on your TV does.

I run it as a script like:
remindme 2:00pm "install window"

If you are interested, send me a PM and I can send you the script and information (I'm at work and don't have access to it right now).

---

### Post by spupy on 2008-06-11
gnome-schedule
A simple gtk frontend for cron.
+
zenity
```
DISPLAY=:0.0 zenity --warning --title="Title" --text="Text."
```

---

### Post by andrewski on 2008-06-11
> **wwuster said:**
> I'm looking for a linux program that will remind me to do stuff every other Monday, eg. I need it to put up a window on my screen at 8:00 am and keep it there until I close it. Or it could write to whatever terminal I'm on in a way that I can't miss the reminder. Is there such a program?
My favorite tool for this job is [Remember the Milk]("http://www.rememberthemilk.com"). It's primarily a website, but between using their [Gmail extension]("http://www.rememberthemilk.com/services/gmail/") and [Tasque]("http://live.gnome.org/Tasque"), it's great for reminders, and I even have it send me text messages and reminders via IM when I'm out and about on my phone. It really has a ton of services: [http://www.rememberthemilk.com/services](http://www.rememberthemilk.com/services). They make it one of my favorite websites I don't actually visit (because I interact with it elsewhere).

So, for you, you could get IM/email/Tasque reminders when your tasks are due. Neat, eh? :grin:

---

### Post by archeryguru2000 on 2009-02-24
> **KingTermite said:**
> I just set one up with a script and using osd_cat (got the template for the script in "Linux Desktop hacks").

osd_cat will put the reminder on your screen no matter where you are as a "on screen display", not a window. That way it can't be hidden. It comes up much like the volume bar on your TV does.

I run it as a script like:
remindme 2:00pm "install window"

If you are interested, send me a PM and I can send you the script and information (I'm at work and don't have access to it right now).

Hello KingTermite.  I actually have that same book.  I'm currently trying to get my "reminder" script to execute properly myself.  Did you have to make many modifications to the script found in the book?  When I attempt to create a new reminder I'm greeted with the following.
```

$: remindme 1:17PM "Just checking to see if this works."
warning: commands will be executed using /bin/sh
job 16 at Tue Feb 24 13:17:00 2009

```
I'm not certain... but I highly doubt that I should be receiving a warning message if the script executes properly.  Anyway, if you could lend some assistance I'd greatly appreciate.

Thanks,
~~archery~~

---

