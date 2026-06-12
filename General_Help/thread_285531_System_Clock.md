---
title: "System Clock"
date: 2006-10-26
forum: General Help
---

### Post by cssutto on 2006-10-26
I have checked the proper box and selected three servers all in the same time zone and my clock is not updated periodically.

Right now, it is about 4 minutes or so fast.

What can I do to insure that time checks are done on schedule?

The computer being on line is not a problem.

CSSJR

---

### Post by chippy99 on 2006-10-27
Do you have ntp installed ?
Type ps -A | grep ntp and you should see an entry for for ntpd.

If not you will need to install it. In edgy it does it automagically if you right click on the time/date in the panel and select adjust date/time a dialogue opens that gives you the option of synchronizing the clock with internet servers. If ntp is not installed it prompts whether you want install it.

---

### Post by cssutto on 2006-10-27
This is what it returned:

 5018 ?        00:00:00 ntpd
 5037 ?        00:00:00 ntpd

CSSJR

---

### Post by matthewstory on 2006-10-27
ntp won't work if your clock is too far off . . . to set the clock:

date 9:00

or whatever the time is in 24 hour format

then run 

hwclock --systohc

That'll sync down the system clock to the hardware clock . . .

then restart your ntp server:

/etc/init.d/ntp-server restart

should fix your problems.

---

### Post by cssutto on 2006-10-27
I went through the above steps.

I got confirmation at each step that it was successful.

No change in the displayed time.

I can go to system>administration>set time and uncheck the "periodically check" box and do the one time sync and it sets the clock correctly.

Which I finally did out of exasperation.

So now I guess I have to wait to find out what happens next.

So problem patched but not cured.

CSSJR

---

