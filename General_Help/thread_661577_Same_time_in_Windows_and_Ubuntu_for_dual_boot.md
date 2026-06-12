---
title: "Same time in Windows and Ubuntu for dual boot?"
date: 2008-01-08
forum: General Help
---

### Post by Schalken on 2008-01-08
I'm in Melbourne (GMT+10) and I always have very different times in Ubuntu and in Windows on this dual boot system. Usually when Ubuntu boots after using Windows the time is wrong (by many hours, sometimes the wrong day/date) and then it fixes it when it syncs with the Internet servers, then I boot into Windows and the time is wrong again, and then it fixes itself and I go into Ubuntu and the time is wrong again. :/

My understanding is that one of the OSes wants the system clock to be set to local time, while the other OS wants the system clock to be set to GMT, and be adjusted to local time by whatever application is using the time.

How can I make sure both Windows and Ubuntu are treating and adjusting the system clock the same way?

**Update: post #5**

**SOLUTION: post #6**

---

### Post by erfahren on 2008-01-08
hmmm.. how about the time in your BIOS ? is it set correctly (or close)?

I only have a problem similar to that when I start installing using the LiveCD - the time is always off but is correct after I install. 

I'd check the BIOS time

---

### Post by daniel_szollosi-nagy on 2008-01-08
I may be asking the obvious here, but are you sure both Windows and Ubuntu are set to the same timezone?

---

### Post by dcstar on 2008-01-08
> **Schalken said:**
> I'm in Melbourne (GMT+10) and I always have very different times in Ubuntu and in Windows on this dual boot system. Usually when Ubuntu boots after using Windows the time is wrong (by many hours, sometimes the wrong day/date) and then it fixes it when it syncs with the Internet servers, then I boot into Windows and the time is wrong again, and then it fixes itself and I go into Ubuntu and the time is wrong again. :/

My understanding is that one of the OSes wants the system clock to be set to local time, while the other OS wants the system clock to be set to GMT, and be adjusted to local time by whatever application is using the time.

How can I make sure both Windows and Ubuntu are treating and adjusting the system clock the same way?

In Ubuntu, right-click the time (top RHS of the Gnome panel) and select Preferences. Change "Use UTC" and this should make the system the same as what you have in Windoze.

---

### Post by Schalken on 2008-01-13
Okay, I've done some investigation and I've found the following:

I'm on GMT+10:00, but because of daylight savings it's actually GMT+11:00. Windows treats the system clock as local time and Ubuntu treats the system clock as UTC.

After going from Ubuntu to Windows, the time in Windows appears 11 hours behind. It then syncs and appears correctly, and the system time is set to the local time (as seen in the BIOS). Then in Ubuntu the time appears 11 hours ahead, then it syncs and the time appears correct again, and the system time is set to UTC.

> **daniel_szollosi-nagy said:**
> I may be asking the obvious here, but are you sure both Windows and Ubuntu are set to the same timezone?

Yes, both are set to Melbourne (GMT+10:00)

> **dcstar said:**
> In Ubuntu, right-click the time (top RHS of the Gnome panel) and select Preferences. Change "Use UTC" and this should make the system the same as what you have in Windoze.

With that setting on, Ubuntu will still treat the system time as UTC and hence sync it to UTC, and will then display the UTC time in the panel instead of adjusting it to local time. I want the local time to appear in my panel, not UTC.

So my question is, how can I either:
A) set Ubuntu to treat the system time as the local time, and hence sync it to local time like Windows
or
B) set Windows to treat the system time as UTC, and hence sync it to UTC like Ubuntu ***(preferrable)***

I could also work around it:
A) turn off syncing in Ubuntu and tell it to display UTC, and since Windows will sync the system clock to local time, what Ubuntu thinks is UTC is actually local time and will hence display local time in the panel (**that will throw off everything else that treats the system clock as UTC, for eg message timestamps in Pidgin and post times on the WordPress installation will be wrong**)
B) turn off syncing in Windows, but since I cant get it to display any time other than the system time, **the time will always be 11 hours behind in Windows, and i will end up 1 or 2 hours late for an interview after using Windows!**

**EDIT: ** After more reading I've found there is a difference between what I've been calling "System time" and the "Hardware time"/"BIOS time". In both Windows and Ubuntu, "System time" is the local time, and is set according to the hardware time during boot. Where it differs is that, as stated, Windows wants hardware time to be the local time/system time, while Ubuntu wants the hardware time to be UTC, and for the system time to be set to local time according to that.

"date" will give the local time according to the system time.
"date -u" will give UTC according to the system time.
"hwclock" or "hwclock -u" will give the local time according to the hardware time, treating hardware time as UTC.
"hwclock --localtime" will give local time according to hardware time, treating hardware time as local time.

Before this edit where I've mentioned "System time" i was actually talking about hardware time :P

---

### Post by Schalken on 2008-01-14
I've found the solution: [http://miknight.blogspot.com/2006/06/storing-system-time-in-utc-in-windows.html](http://miknight.blogspot.com/2006/06/storing-system-time-in-utc-in-windows.html)

Basically, you add the registry key "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation\RealTimeIsUniversal" as a DWORD Value (REG_DWORD) and set it to 1, and Windows will treat the hardware clock (or Real Time Clock (RTC) as it is called here) as UTC, and will set it as such, just like Ubuntu. So now both Windows and Ubuntu's system clocks will be the same and will set the hardware clock to UTC according to the NTP/time servers they are syncing with.

Funny how the solution came from someone in the same timezone as me :P

---

