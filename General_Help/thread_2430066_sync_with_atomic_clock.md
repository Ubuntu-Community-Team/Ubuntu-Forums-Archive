---
title: "sync with atomic clock"
date: 2019-10-27
forum: General Help
---

### Post by Old Jimma on 2019-10-27
Hi Forms:

I need to sync my computer's clock with an atomic clock. The most recent discussion on this that I've found is 2006. Alot of things have changed since then with ubuntu features. Some of the instructions in the  2006 replies refer to system features that don't exist anymore.

Could someone please give me instructions on how to do this?

THanks,
Old Jimma

---

### Post by TheFu on 2019-10-27
[https://help.ubuntu.com/lts/serverguide/NTP.html](https://help.ubuntu.com/lts/serverguide/NTP.html) is usually millisec accurate.
If you need greater accuracy, there is PTP, but I've not used it.
If your machine isn't on the internet, then you can use a GPS device to get accurate time. GPS accuracy is all about accurate time.  I have a $20 GPS device that can be accessed over bluetooth for position data. Incidentally, it also knows the current time to extremely accurate levels.

If you actually have an atomic clock, their should be an API to get that information.  I've never been anywhere that actually used one.  When I worked in a govt lab, we used GPS satellite time using 9 sources and ran 3 time servers for our thousands-or-so systems.

---

### Post by Old Jimma on 2019-10-27
Hi The Fu:

I read the [QUOTE [https://help.ubuntu.com/lts/serverguide/NTP.html](https://help.ubuntu.com/lts/serverguide/NTP.html) [/QUOTE] page... and am a little concerned.

It says add the following lines to >  /etc/chrony/chrony.conf;

> 
# Use servers from the NTP Pool Project. Approved by Ubuntu Technical Board
# on 2011-02-08 (LP: #104525). See [http://www.pool.ntp.org/join.html](http://www.pool.ntp.org/join.html) for
# more information.
pool 0.ubuntu.pool.ntp.org iburst
pool 1.ubuntu.pool.ntp.org iburst
pool 2.ubuntu.pool.ntp.org iburst
pool 3.ubuntu.pool.ntp.org iburst


However, >  /etc/chrony/chrony.conf already has lines like this:

> 
# About using servers from the NTP Pool Project in general see (LP: #104525).
# Approved by Ubuntu Technical Board on 2011-02-08.
# See [http://www.pool.ntp.org/join.html](http://www.pool.ntp.org/join.html) for more information.
pool ntp.ubuntu.com        iburst maxsources 4
pool 0.ubuntu.pool.ntp.org iburst maxsources 1
pool 1.ubuntu.pool.ntp.org iburst maxsources 1
pool 2.ubuntu.pool.ntp.org iburst maxsources 2


They look pretty similar. I wondered whether I should remove the lines listed above and patch in the lines described on the help page.

The reason why I'm asking for help is because I got a warning message:

> 
Warning: Potential Security Risk Ahead

Firefox detected an issue and did not continue to logon.vanguard.com. The website is either misconfigured or your computer clock is set to the wrong time.

It&#8217;s likely the website&#8217;s certificate is expired, which prevents Firefox from connecting securely. If you visit this site, attackers could try to steal information like your passwords, emails, or credit card details.

What can you do about it?

Your computer clock is set to 10/27/2019. Make sure your computer is set to the correct date, time, and time zone in your system settings, and then refresh logon.XXXX.com.

If your clock is already set to the right time, the website is likely misconfigured, and there is nothing you can do to resolve the issue. You can notify the website&#8217;s administrator about the problem.


So... I'm investigating if the time on my Ubuntu computers is wrong.

Thanks,
Old JImma

ps. BTW, yes I've3 been an Ubuntu "adictee" since 5.04 Hoary Hedgehog. While I have technical training and learned unix on a super computer, that was a long, long, long, long time ago and I'm not a computer sleuth anymore. I'm 68, retired, and study music now. Over they years, ability to read computer science literature evaporated and the world has passed me by. However, very glad that I'm using Ubuntu... and Raspian. "Old" Jimma is a completely apt handle for me... or perhaps "Older Than Rocks" Jimma might be even better. I've been grateful for your help in past postings. Thank you! O.J.

---

### Post by Old Jimma on 2019-10-27
Maybe the root of the problem is that I took my laptop to New Orleans last week. I can't fix that!

---

### Post by TheFu on 2019-10-27
Do you or do you not have access to an actual atomic clock?  You brought it up.

Is the computer on the internet?  Are internet time sources not sufficiently accurate?  Internet time should be accurate to milliseconds.  

date is the command to see what time your computer thinks it is.
```
$ date
Sun Oct 27 11:14:50 EDT 2019
```
is what mine says.

I doubt HTTPS would care much if a clock was off by a few hours.  Since it is a weekend, that HTTPS issue is probably an issue on the far side.  Check their server certificate. Perhaps it expired?

---

### Post by Holger_Gehrke on 2019-10-27
As the TheFu guessed it's an expired certificate. They should have renewed last week because the certificate they are using for https expired today. Nothing wrong on your end.

Holger

---

### Post by Old Jimma on 2019-10-27
Yo Fu and Hoger!

You da guys!  This is the first time it isn't my fault! I love it when somebody else screws up, 'cause it is usually me who is the probem example child. I'm used to it, though. Its been that way since elementary school right up to today (I'm sure I'll screw something up today!)

Many thanks!
Older than the Universe Old Jimma

---

### Post by Old Jimma on 2019-10-27
bbb

---

