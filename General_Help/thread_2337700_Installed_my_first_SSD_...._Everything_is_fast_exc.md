---
title: "Installed my first SSD .... Everything is fast except Firefox"
date: 2016-09-20
forum: General Help
---

### Post by linuxyogi on 2016-09-20
I installed my first Samsung SSD today. Everything is pretty fast including boot time.

The only thing that still has a long launch time is Firefox. Its taking about 10 secs to launch.

Any teaks I can do ?

Addons installed :

NoScript
UblockOrigin
Bluhell
Ghostery
WebofTrust

---

### Post by &amp;KyT$0P# on 2016-09-20
Does Firefox still load slowly with a new, clean [profile]("http://kb.mozillazine.org/Profile") with all default settings and no extensions added?

If the problem doesn't exist there, try uninstalling Ghostery and Bluhell.  Ghostery is notorious for causing extension conflicts weird issues, and both those addons are made redundant by uBlock Origin.

---

### Post by wildmanne39 on 2016-09-20
*Thread moved to **General Help**.*

---

### Post by linuxyogi on 2016-09-20
Removed Ghostery and Bluhell. Launch time now is 6 secs. Interestingly other apps like libreoffice is launching in 2 secs.

---

### Post by &amp;KyT$0P# on 2016-09-20
What was Firefox launch time with the clean profile?  Make the profile, select to start Firefox with it, quit Firefox **not saving the tabs**, and then start Firefox into the same clean profile again.  Time that last start.

That's your baseline to go by, and without that information we can't know whether there's room for improvement on a number like 6 seconds.

---

### Post by linuxyogi on 2016-09-20
> **halogen2 said:**
> What was Firefox launch time with the clean profile?  Make the profile, select to start Firefox with it, quit Firefox **not saving the tabs**, and then start Firefox into the same clean profile again.  Time that last start.

That's your baseline to go by, and without that information we can't know whether there's room for improvement on a number like 6 seconds.

Backed up the old profile, launched FF, closed all tabs, restarted FF. Launch time was 3 secs.

---

### Post by &amp;KyT$0P# on 2016-09-20
I have both NoScript and uBlock Origin and my start time is very fast, so those are not likely cuplrits.  Especially with uBlock Origin having async initialization (meaning, not initializing "heavy stuff" like filters until *after* the browser startup).

What page(s) does your Firefox open on startup and do you allow any scripts there in NoScript?
Does disabling WOT speed up your start time at all?

---

### Post by linuxyogi on 2016-09-20
> **halogen2 said:**
> 
What page(s) does your Firefox open on startup and do you allow any scripts there in NoScript?
Does disabling WOT speed up your start time at all?

On startup FF opens this page

[ATTACH=CONFIG]271283[/ATTACH]

I have allowed this page in noscript. Tried removing WOT but no improvement.

> **halogen2 said:**
> I have both NoScript and uBlock Origin and my  start time is very fast, so those are not likely cuplrits.  Especially  with uBlock Origin having async initialization (meaning, not  initializing "heavy stuff" like filters until *after* the browser startup).


Which CPU are you using. May be my CPU is not powerful enough.

I am using AMD Athlon(tm) 64 X2 Dual Core Processor 5600+

---

### Post by &amp;KyT$0P# on 2016-09-20
> **linuxyogi said:**
> On startup FF opens this page
Ok that's not the problem then.

If you add your extensions (NoScript, uBlock Origin, WOT) in the new profile, still leaving default settings, what is the startup time?
(Give it a few restarts after installing the extensions.  I tested new profile Firefox ESR with just NoScript + uBlock Origin, the first restart after installing took more time than subsequent restarts.)

> Which CPU are you using. May be my CPU is not powerful enough.
It's in a VM running on 2 cores of a Intel Core i7 quad-core, but I don't have a SSD.  Which is precisely why we're benchmarking your system against your system.
My startup time is just over 1 second, but does that alone mean anything here?  Nope, I would expect about 3-4 seconds startup time on your machine with that list of extensions.

So, we compare relative scaling of the times.  On my system, a new profile isn't much noticeably slower startup than my working profile.  A factor-of-2 increase in delay seems improvable.

---

### Post by linuxyogi on 2016-09-20
> **halogen2 said:**
> 
If you add your extensions (NoScript, uBlock Origin, WOT) in the new profile, still leaving default settings, what is the startup time?
(Give it a few restarts after installing the extensions.  I tested new profile Firefox ESR with just NoScript + uBlock Origin, the first restart after installing took more time than subsequent restarts.)


Just tried that. Its back to 6 secs. I think the only way is to remove all addons but I cant afford to surf the web without at least NoScript, uBlock and WOT.

I guess I will have to cope with this. Thanks a lot for your replies. If you want me to do further testing just ask.

---

### Post by &amp;KyT$0P# on 2016-09-21
> **linuxyogi said:**
> Just tried that. Its back to 6 secs. 
That's really odd, so either something about your system or the current Firefox release.  Are you short on free RAM?

Aside that, I don't know what else to say, sorry.

> I think the only way is to remove all addons but I cant afford to surf the web without at least NoScript, uBlock and WOT.

I guess I will have to cope with this. 
Think of it this way, these addons are **improving** performance of Firefox.  3 extra seconds on startup vs waiting 20+ seconds on every other site loading?  I'd make the same choice as you.

> Thanks a lot for your replies
You're welcome. :)

---

### Post by linuxyogi on 2016-09-21
> **halogen2 said:**
>   Are you short on free RAM? 

I got 4 GB of Ram, no swap

The followig result is with Firefox, Claws-Mail and Smplayer

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3965       1836       2128         37         71       1229
-/+ buffers/cache:        535       3429
Swap:            0          0          0
```

---

### Post by shantiq on 2016-09-22
[a few more tricks ?]("http://bernaerts.dyndns.org/linux/74-ubuntu/212-ubuntu-firefox-tweaks-ssd")

---

### Post by &amp;KyT$0P# on 2016-09-22
Link hangs loading here.  It's accessible through the [wayback machine]("https://web.archive.org/web/20150715024352/http://bernaerts.dyndns.org/linux/74-ubuntu/212-ubuntu-firefox-tweaks-ssd") though.

> **shantiq said:**
> a few more tricks ?
(1) and (5) are likely worth it.  Read [this]("http://kb.mozillazine.org/Content.interrupt.parsing") before trying (7).
(2) might help, but putting the firefox directory in [FONT=Courier New]/run/user/your_uid[/FONT] would seem a better choice than randomly in /dev.

The rest are known to be dangerous to Firefox and should be avoided on anyone's main profile.

---

### Post by linuxyogi on 2016-09-22
```
network.prefetch-next **false**
```

1) is already set to false.

5) ```
network.prefetch-next
``` does not exist. Should I create it?

---

### Post by &amp;KyT$0P# on 2016-09-22
> **linuxyogi said:**
> 5) ... does not exist. Should I create it?
According to [this page]("http://kb.mozillazine.org/Browser.sessionstore.enabled"), disabling session restore is done differently now.

---

### Post by linuxyogi on 2016-09-22
> **halogen2 said:**
> According to [this page]("http://kb.mozillazine.org/Browser.sessionstore.enabled"), disabling session restore is done differently now.

Unfortunately that page was too complicated for me. Can you please have a look and tell me what to remove/insert/change.

---

### Post by &amp;KyT$0P# on 2016-09-22
Just this part -
> setting browser.sessionstore.max_tabs_undo and browser.sessionstore.max_windows_undo to 0
Do both of those preferences exist in your about:config?

---

### Post by linuxyogi on 2016-09-22
> **halogen2 said:**
> Just this part -

Do both of those preferences exist in your about:config?

```
 browser.sessionstore.max_windows_undo
``` exists and I have set it to zero but

```
setting browser.sessionstore.max_tabs_undo
``` doesn't exist.

---

### Post by &amp;KyT$0P# on 2016-09-22
> **linuxyogi said:**
> ```
setting browser.sessionstore.max_tabs_undo
``` doesn't exist.
But the entry ```
browser.sessionstore.max_tabs_undo
``` does exist, no?

The word "setting" isn't part of the setting itself. ;)

---

### Post by linuxyogi on 2016-09-22
> **halogen2 said:**
> But the entry ```
browser.sessionstore.max_tabs_undo
``` does exist, no?

The word "setting" isn't part of the setting itself. :wink:

Sorry, found it and set to zero. Launch time is still 6 secs. I guess the above tweaks are meant to enhance the longevity of the SSD.

One more thing I wanted to ask is do I need to do fstrim on a daily or weekly basis ?

I have already added noatime to /etc/fstab.

Please have a look [here]("https://www.reddit.com/r/buildapc/comments/3a58s0/dont_use_linux_on_samsung_ssds/")

---

