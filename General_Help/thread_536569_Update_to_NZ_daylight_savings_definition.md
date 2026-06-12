---
title: "Update to NZ daylight savings definition?"
date: 2007-08-27
forum: General Help
---

### Post by MobiusNZ on 2007-08-27
Hi there,

You may or may not be aware, but the NZ government has decided to extend our daylight savings time by three weeks (one week early and two weeks late). I've got a fully up-to-date Feisty Fawn install, but sudo zdump -v /etc/localtime | grep 2007 is still incorrect:
```

/etc/localtime  Sat Mar 17 13:59:59 2007 UTC = Sun Mar 18 02:59:59 2007 NZDT isdst=1 gmtoff=46800
/etc/localtime  Sat Mar 17 14:00:00 2007 UTC = Sun Mar 18 02:00:00 2007 NZST isdst=0 gmtoff=43200
/etc/localtime  Sat Oct  6 13:59:59 2007 UTC = Sun Oct  7 01:59:59 2007 NZST isdst=0 gmtoff=43200
/etc/localtime  Sat Oct  6 14:00:00 2007 UTC = Sun Oct  7 03:00:00 2007 NZDT isdst=1 gmtoff=46800

```
Daylight savings *should* start on Sun Sep 30 14:00:00 2007 UTC.

Any idea on when an update should come out for this? I've heard that it is in the pipeline, but we're getting closer to d-day.

---

### Post by AlexThomson_NZ on 2007-08-29
Greetings fellow kiwi!

You can update all versions of Ubuntu with the following commands:
```

sudo wget http://mirror.pacific.net.au/linux/ubuntu/pool/main/t/tzdata/tzdata_2007f-3ubuntu1_all.deb
sudo dpkg -i tzdata_2007f-3ubuntu1_all.deb

```

---

### Post by MobiusNZ on 2007-08-29
Champion!

I found I had to run ```
sudo dpkg-reconfigure tzdata
``` as it complained about me having a user-defined timezone... ?

I was just at a M$ discussion about the issues with this change. It's a lot more in-depth than I'd previously thought! Schedules, appointments, transaction recording... all skewed...eek!

Luckily I don't seem to be affected too much, as I don't schedule too far ahead.

Also, I have tested with pretend schedules, and Kontact doesn't appear to need its appointments to be skewed like Outlook does. I think we still have to be wary of emailed meeting requests during these times though.

Now I just have to find a way to get PHP to update to these changes.... it stores its information separately, and the updates I have found are still out of date. Any ideas on that?

---

### Post by AlexThomson_NZ on 2007-08-29
Yeah, lot of work involved alright- I don't think the government really thought it through very well.

I got a warning too, but found it had still worked ok.

I think there are going to be a lot issues around this, I know a lot of government departments run applications provided by third parties are going to break (Java is another thing that needs to be patched)

---

### Post by Irihapeti on 2007-08-30
Thanks Alex_ThomsonNZ

That fix worked nicely. Not even any complaints from my system about custom time zones (so far!).

Greetings to both fellow Kiwis

Irihapeti

---

### Post by penguin007 on 2007-08-31
Thanks mate!

---

### Post by iamhugeinjapan on 2007-09-13
I just checked my up to date Feisty system and it is showing the correct start and end dates for the 2007/2008 period.  No manual deb install is needed.

---

### Post by leisuresuitgreg on 2007-09-20
My up to date feisty system also does not need the manual deb

```
/etc/localtime  Sat Mar 17 13:59:59 2007 UTC = Sun Mar 18 02:59:59 2007 NZDT isdst=1 gmtoff=46800
/etc/localtime  Sat Mar 17 14:00:00 2007 UTC = Sun Mar 18 02:00:00 2007 NZST isdst=0 gmtoff=43200
/etc/localtime  Sat Sep 29 13:59:59 2007 UTC = Sun Sep 30 01:59:59 2007 NZST isdst=0 gmtoff=43200
/etc/localtime  Sat Sep 29 14:00:00 2007 UTC = Sun Sep 30 03:00:00 2007 NZDT isdst=1 gmtoff=46800
```

Also "iamhugeinjapan" I'm guessing you played in Huge In Japan with Ara, or is the name just a coincidence? My girlfriend Claire is good friends with Ara...

Greg

---

### Post by dcstar on 2007-09-22
> **MobiusNZ said:**
> Hi there,

You may or may not be aware, but the NZ government has decided to extend our daylight savings time by three weeks (one week early and two weeks late).
...........

Just out of (regional) interest, this time next year a lot of Australian States will also be changing their Daylight Saving start time from the last Sunday in October to the first Sunday (I'm not sure if the end changes).

One hopes that this advance info has made its way to the relevant package maintainers....   ;)

---

### Post by Washi on 2007-09-23
Hiya to all the other Kiwi´s, I did the patch just in case, but atleast we have options, I pity the Microsoft users who will be getting nothing but grief with all their software.  Atleast the linux apps will just go ¨hello new info, lets use it...¨ as usual :)

---

### Post by NZ-Wanderer on 2007-09-26
Greetings to fellow NZers :) :)

Thanks for the code, gonna put it in soon as I save this message...

Tried to get the update for vista from that other crowd (M$) but alas it just keeps bombing out with an error when trying to update itself, so methinks I will just make sure I stay in Kubuntu till after the day and then just change it manually in vista...

---

### Post by AlexThomson_NZ on 2007-09-26
And people use Windows because "it just works", ha.

We are doing the last of our production boxes this evening, been pretty painless so far (all Linux+Solaris boxes), most just requiring just a Java and OS patch.  A few problems are already appearing though in things like Lotus Notes, etc. so should be interesting to see if there are major issues that arise from the change...

---

### Post by MobiusNZ on 2007-09-26
Hah, you should have gone to the M$ conference about the change. Check out microsoft.co.nz/timezone to see how badly they design their clocks ;)

---

### Post by NZ-Wanderer on 2007-09-26
hehe well I trierd updating through their own automatic update without success..
The thing that really makes me laugh (or cry) is that the update error I get tracks down to be an OFFICE error (a componant in services turned off (I don't even have the entry in services for it cause I don't even have Office installed on Vista... (I only use Vista to play my games :) )
Just as well I only play games on Vista and use Kubuntu for everything else, cause it would drive me up the wall...

---

### Post by psb777 on 2007-09-29
I have an up to date Feisty Fawn installation.  The time switch did not happen for me.  The timezone reported my date changed to NZDT but the clock did not move.  I am running the ntp timeserver.  I disabled that so I could run "sudo ntpdate pool.ntp.org" and all is now OK.  Problem with the ntp server?

---

### Post by MobiusNZ on 2007-09-29
Maybe your ntp server needs updating?

---

### Post by InTheSand on 2007-10-01
> **MobiusNZ said:**
> Now I just have to find a way to get PHP to update to these changes.... it stores its information separately, and the updates I have found are still out of date. Any ideas on that?

Hi,

Did you have any luck with this? My servers updated fine and report the correct time and timezone when queried locally, but PHP unfortunately still reports NZST and GMT+12...

Cheers,

 - Ali

---

### Post by Irihapeti on 2007-10-01
Had an odd thing happen here. I booted the computer on Sunday, still showed NZST. I went online (dialup) and I updated from one of the internet servers. So far, so good.

But then, I suspended the system and went out for a while. When I got home, I resumed and happened to notice that the clock had reset itself back to NZST! I manually put it on an hour and it's been fine since.

Is this normal behaviour, or did I set something wrong?

Irihapeti

---

### Post by MobiusNZ on 2007-10-01
Hey Ali,

The latest php5 package in the standard Feisty repositories is 5.2.1-0ubuntu1.4. I'm gathering that means php5 version 5.2.1. According to php.net, the latest version out is 5.2.4. In its changelist is > Updated timezone database to version 2007.6. (Derick)

This sounds promising. I have no idea how long we'll have to wait for this package to come into the repos. If you're desperate for the change, you'll just have to uninstall the package version and compile the latest one yourself.

---

### Post by MobiusNZ on 2007-10-01
> **Irihapeti said:**
> Had an odd thing happen here. I booted the computer on Sunday, still showed NZST. I went online (dialup) and I updated from one of the internet servers. So far, so good.

But then, I suspended the system and went out for a while. When I got home, I resumed and happened to notice that the clock had reset itself back to NZST! I manually put it on an hour and it's been fine since.

Is this normal behaviour, or did I set something wrong?

Irihapeti
Whats the output you get when you type ```
sudo zdump -v /etc/localtime | grep 2007
``` in the terminal?

---

### Post by MobiusNZ on 2007-10-01
> **Washi said:**
> Hiya to all the other Kiwi´s, I did the patch just in case, but atleast we have options, I pity the Microsoft users who will be getting nothing but grief with all their software.  Atleast the linux apps will just go ¨hello new info, lets use it...¨ as usual :)

Well, except for *some* apps, no names.. (coughphpcough). I don't really understand why they use different timezone data... I think its something to do with being able to work the same way across all platforms... but I don't see why it can't just have an abstraction layer that bases its data off the operating system.

Then again, even that wouldn't work, what with Apple still not having released an update for the macs yet. Obviously they don't believe that Mac users do any real work... I mean Photoshop doesn't care what time it is! ;)

---

### Post by Irihapeti on 2007-10-01
> **MobiusNZ said:**
> Whats the output you get when you type ```
sudo zdump -v /etc/localtime | grep 2007
``` in the terminal?

I get

```
/etc/localtime  Sat Mar 17 13:59:59 2007 UTC = Sun Mar 18 02:59:59 2007 NZDT isdst=1 gmtoff=46800
/etc/localtime  Sat Mar 17 14:00:00 2007 UTC = Sun Mar 18 02:00:00 2007 NZST isdst=0 gmtoff=43200
/etc/localtime  Sat Sep 29 13:59:59 2007 UTC = Sun Sep 30 01:59:59 2007 NZST isdst=0 gmtoff=43200
/etc/localtime  Sat Sep 29 14:00:00 2007 UTC = Sun Sep 30 03:00:00 2007 NZDT isdst=1 gmtoff=46800

```

When this thread first started, I followed the instructions and checked the results by doing what you've just suggested. That's why I'm puzzled.

---

### Post by MobiusNZ on 2007-10-01
If the output of 
```
date
```
has NZDT then you should be fine. If not, you need to adjust the timezone for your computer. You can do that in your system settings.

---

### Post by Irihapeti on 2007-10-01
> **MobiusNZ said:**
> If the output of 
```
date
```
has NZDT then you should be fine. If not, you need to adjust the timezone for your computer. You can do that in your system settings.

Yes, that's all fine.

Just so that I understand, is the computer supposed to automatically change the clock? I have to admit I'm unclear on this. The last computer I owned was a Mac SE/30 - boy, does that date me :-) - and everything of that kind had to be done by hand.

Irihapeti

---

### Post by MobiusNZ on 2007-10-01
Ideally, your computer clock (in the BIOS) should be set to GMT, which never changes. Most decent *nix installs operate like this. Then the operating system applies its timezone offset to that, and presents you with a nice friendly time. Thus, you change the offset, and all the times appear to change as well.. without buggering up appointments etc.

Unfortunately this isn't the way that that *other* operating system works - it stores its time locally, and does all sorts of strange things when you muck with it. Anyone checked their outlook calendar this week? :P

When you installed linux it would have asked you if your computer clock was to be set to GMT or not, and from there it would run either way. If you have windows, you can't sensibly have the GMT way.

So, in short - the time is only ever changed if your system clock does not run GMT.

[Edit]
Err, that didn't really answer your question now I read it again... Hows this: "It *should* change it for you"

---

### Post by Irihapeti on 2007-10-01
> **MobiusNZ said:**
> 

So, in short - the time is only ever changed if your system clock does not run GMT.

[Edit]
Err, that didn't really answer your question now I read it again... Hows this: "It *should* change it for you"

Well, I'm not running W******* any more, so unless it's done some permanent damage (stranger things have happened) it's not likely to be the problem.

However, now I think about it, whenever I run the GParted liveCD, which I do to make regular backups of my root partition, any files that I write to the HD end up with dates 12 hours in the future. So maybe something IS a bit mixed up in there. Unless someone can give me a straightforward guide to finding and fixing it, I think I'll leave well alone and just reset the clock manually, like all the other clocks around the place :-)

---

### Post by MobiusNZ on 2007-10-01
Maybe you skipped over the "Set my system clock to GMT" bit in the install. 
Not sure how to fix that, it hardly seems to warrant the effort though.

---

### Post by Irihapeti on 2007-10-01
> **MobiusNZ said:**
> Maybe you skipped over the "Set my system clock to GMT" bit in the install. 
Not sure how to fix that, it hardly seems to warrant the effort though.

That may well be the case. There are so many things to think about when doing an install as a newbie that it's easy to overlook something, or not even realise what effect it's going to have. When I screw something up badly enough to reinstall, I may do that - assuming I remember.

Thanks

---

### Post by InTheSand on 2007-10-02
> **MobiusNZ said:**
> According to php.net, the latest version out is 5.2.4. (snip) I have no idea how long we'll have to wait for this package to come into the repos. If you're desperate for the change, you'll just have to uninstall the package version and compile the latest one yourself.

Thanks for the info. Neither server affected is critical, so I'll wait for the newer version of PHP to filter through into the repositories. I'm guessing this'll happen after this weekend, by which time it'll be less of a noticeable problem!

 - Ali

---

### Post by Irihapeti on 2007-10-09
> **MobiusNZ said:**
> Maybe you skipped over the "Set my system clock to GMT" bit in the install. 
Not sure how to fix that, it hardly seems to warrant the effort though.

I found an answer. I'm posting it in case others have the same problem - it goes with dual-boot, apparently.

My version of /etc/default/rcS had a line reading "UTC=no". I changed it to "UTC=yes" and it fixed the problem. Now when I boot into Gparted liveCD I'm not getting a future date.

BTW, I'm no longer dual booting.

Irihapeti

---

