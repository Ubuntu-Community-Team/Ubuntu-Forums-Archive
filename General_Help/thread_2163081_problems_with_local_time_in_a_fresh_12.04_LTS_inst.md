---
title: "problems with local time in a fresh 12.04 LTS installation"
date: 2013-07-17
forum: General Help
---

### Post by fabiani on 2013-07-17
Hi,

I just update to ubuntu 12.04 LTS and I'm having problems in setting my local time properly.

My time zone seems to be set properly:

fabiano@fabiano-OptiPlex-960:/etc$ more /etc/timezone 
Australia/Melbourne

But for some reason I get

fabiano@fabiano-OptiPlex-960:/etc$ sudo hwclock 
Wed 17 Jul 2013 14:54:54 EST  -0.640978 seconds

That  is the correct local time (in Melbourne, I had to set it manually  through the applet gui), but I'm obviously not in the EST zone. The same  happens with

fabiano@fabiano-OptiPlex-960:/etc$ more /etc/localtime 
TZif2
&#65533;y&#65533;&#65533;&#65533;&#65533;@(&#65533;T0&#65533;U 
&#65533;V&#65533;&#65533;V&#65533;&#65533;&#65533;W&#65533;&#1856;X&#65533;&#896;Y&#1023;&#65533;Z&#65533;&#65533;&#65533;[&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;T&#65533;
&#65533;&#65533;&#65533;
&#65533;@(&#65533;re--(51%)
&#65533;
EST-10EST,M10.1.0,M4.1.0/3

I changed the time servers in /etc/ntp.conf to

server 0.au.pool.ntp.org
server 1.au.pool.ntp.org
server 2.au.pool.ntp.org
server 3.au.pool.ntp.org

and restarted my machine, but the problem persists. Can anyone lend me a hand with this? Many thanks!

---

### Post by dino99 on 2013-07-17
is it better with that howto ?  [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by decrepit on 2013-07-17
fabiani
Interesting, this is what I get with my 12.04 box.

michael@Percy:~$ more /etc/timezone
Australia/Perth
michael@Percy:~$ sudo hwclock
Thu 18 Jul 2013 02:27:11 WST  -0.991225 seconds

The above time is GMT, it was actually 17:27:11 here, but my clock is working fine.

It surprises me you aren't EST, I thought Melbourne Sydney and Brisbane where all Eastern Standard Time, apart from summer when Queensland don't do daylight saving??

---

### Post by fabiani on 2013-07-17
Thanks for your help, but actually EST and WST refer to North America east and west standard times... Melbourne should be in the AEST zone. Strange indeed...

---

### Post by fabiani on 2013-07-17
Actually if Perth is assigned to WST there might be a bug in the way timezones in Australia are used to set the local time?

---

### Post by Snowhog on 2013-07-18
Take a look at [[SOLVED] Time Changing Itself]("http://www.kubuntuforums.net/showthread.php?63011-Time-Changing-Itself&highlight=local+time") over on Kubuntu Forums . Net.

---

### Post by fabiani on 2013-07-18
Thanks for the tip, but I ran dpkg-reconfigure tzdata before and it didn't help.

I tried again, and this is the output:

$ sudo dpkg-reconfigure tzdata
[sudo] password for fabiano: 

Current default time zone: 'Australia/Melbourne'
Local time is now:      Thu Jul 18 14:34:50 EST 2013.
Universal Time is now:  Thu Jul 18 04:34:50 UTC 2013.

Note that the time zone is set to EST instead of AEST. hwclock has been set accordingly (I ran this after rebooting):

fabiano@fabiano-OptiPlex-960:~$ sudo hwclock 
[sudo] password for fabiano: 
Fri 19 Jul 2013 00:38:59 EST  -0.052815 seconds

---

### Post by decrepit on 2013-07-19
I'M not sure about the American zones, but Perth is +8hrs at AWST and that's what I get with WST, Looks like you have +10 with EST. So it may be using the common Aussie vernacular and leaving the A out. I'm sure if it was really setting to American times there would be a huge discrepancy.

I'm fairly sure I didn't have to manually adjust my time, just set it to Perth.

---

### Post by CatKiller on 2013-07-19
I agree with decrepit. The US is only, like, 5-7 hours off GMT. The 10 hours you're getting seems much more Australian. What the time zones are called is probably in a localisation file somewhere if you wanted to file a bug report.

---

### Post by fabiani on 2013-08-04
Apologies for replying so late, I've been busy and then this forum has been down for 10 days or so.

It seems very strange to me that the time zones might have a different name depending on where you are, so that EST means one thing in the US and another in Australia... actually I've never seen EST referring to Australian Eastern Standard Time outside Australia.


Also, if I run

$ sudo hwclock 
Mon 05 Aug 2013 02:07:42 EST  -0.447395 seconds

I get the time in New York (It's about 4 pm now in Melbourne), albeit the date is wrong (it's Sunday in both time zones).


Hence maybe it might be worth to send a bug report. I think this is the place to start for that

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

but it doesn't seem to be so immediate, so I don't know when I'll have time to do this, I don't really need a very precise clock anyway, manual setting works good enough for now.

Thank you anyway for your feedback, cheers

---

### Post by decrepit on 2013-08-04
Yep, I get the same.
michael@Percy:~$ sudo hwclock
[sudo] password for michael: 
Mon 05 Aug 2013 04:45:44 WST  -0.047267 seconds

It's now Sunday 04 Aug 2013 20:44 here, so something is very screwy.

---

### Post by fabiani on 2013-08-04
I see, that's not exactly the time difference between Perth and LA but it's rather close (should be 5 am in LA when it's 8 pm in Perth, I guess). But it's only one hour so maybe it's something related to daylight savings. I guess it's definitely worth sending a bug report than, I'll do it as soon as I can (which will probably be not very soon).

If anyone from the ubuntu development team sees this and can do something about it that would be much appreciated. Thanks!

---

