---
title: "Clock can't keep right time"
date: 2016-07-13
forum: General Help
---

### Post by 4kh3RAm on 2016-07-13
My clock is not showing the right time.

Tried both manual and letting server set time.

BIOS battery is new.

What else can I check ?

I really appreciate all the help here. :-)

---

### Post by Frogs Hair on 2016-07-13
Are you dual booting with Windows ?

---

### Post by 4kh3RAm on 2016-07-13
No way.

But even when I did, it did not affect Linux in terms of time keeping.

---

### Post by QIII on 2016-07-13
Hello!

How far is it off?  Are the minutes correct?  Is it off by your time zone with regard to the UTC?

---

### Post by 4kh3RAm on 2016-07-14
My actual current time is 11:10 p.m. (Central Standard Time in US)

Ubuntu is showing 6:07 p.m.

---

### Post by qyot27 on 2016-07-14
The system clock is probably set on a time consistent with current Central Daylight Time (that's a 5-hour skew, Central Standard is UTC-6:00), but it's being assumed to be UTC, and then adjusted in Ubuntu to be consistent with UTC-5:00.  [It's the inverse of the Windows UTC clock skew problem, actually.](https://wiki.archlinux.org/index.php/time#Time_standard)

---

### Post by Bucky Ball on 2016-07-14
> **qyot27 said:**
> The system clock is probably set on a time consistent with current Central Daylight Time (that's a 5-hour skew, Central Standard is UTC-6:00), but it's being assumed to be UTC, and then adjusted in Ubuntu to be consistent with UTC-5:00.  [It's the inverse of the Windows UTC clock skew problem, actually.](https://wiki.archlinux.org/index.php/time#Time_standard)

How does this explain the time on the computer being :07 and the actual time in the timezone being :11, regardless of the hour? If the time was being offset in the way you suggest, the minutes would match, regardless of the hours, or be thirty minutes out in some cases for the real time. I'm just wondering if OP has set Ubuntu clock manually. :-k

@OP: Is this the case, you chose your location during install and the time on Ubuntu is just what it gave you? 

*No doubt you have done this*, but have you right clicked the clock> Properties> Timezone and checked you are set to the right one or one that has the correct offset for your location?

---

### Post by 4kh3RAm on 2016-07-14
> **qyot27 said:**
> The system clock is probably set on a time consistent with current Central Daylight Time (that's a 5-hour skew, Central Standard is UTC-6:00), but it's being assumed to be UTC, and then adjusted in Ubuntu to be consistent with UTC-5:00.  [It's the inverse of the Windows UTC clock skew problem, actually.]("https://wiki.archlinux.org/index.php/time#Time_standard")

I appreciate your effort at helping.

But, you offered no help in my time problem.

---

### Post by qyot27 on 2016-07-15
> **4kh3RAm said:**
> I appreciate your effort at helping.

But, you offered no help in my time problem.
As you posted before in reference to Windows:
> No way.

**But even when I did**, it did not affect Linux in terms of time keeping.
(emphasis mine)

So if Windows was at all *ever* installed on that setup, and the motherboard's clock was aligned with it, the motherboard may be assuming localtime because Windows did.  Now, Ubuntu gets installed, but since Ubuntu defaults to UTC, it sees (and misinterprets) the motherboard clock as UTC and not localtime.  *Usually* the clock skew problem doesn't affect Ubuntu (it's usually that Ubuntu is correct, and Windows is the one with the skew because the clock has been reset to UTC-0:00 and Windows doesn't readjust for that without fiddling with the registry), but if the motherboard's clock has been messed with at all, it might.

And the solution to this is likely to be either to just force systemd to do the right thing* by using *timedatectl* (as the linked part of my last post shows how to do), or to go into your BIOS setup and change the clock there...to the correct time in Greenwich.  And/or to the correct UTC-0:00 time zone, if the BIOS lets you do that.

*which could mean either forcing localtime or resetting the clock.

---

### Post by 4kh3RAm on 2016-07-15
Since reinstalling Ubuntu-Mate, my time has been accurate.

Maybe something in the first installation got corrupted.

---

### Post by Bucky Ball on 2016-07-16
So your clock is now fine? If a problem gets solved please let helpers and others know this by marking the support thread as 'solved'. You can do that by using Thread Tools at the top of this page. 

If there's a problem finding that, see the second link in my signature at the bottom of this post. Thanks.

---

