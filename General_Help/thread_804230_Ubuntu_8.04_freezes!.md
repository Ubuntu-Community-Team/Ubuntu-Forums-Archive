---
title: "Ubuntu 8.04 freezes!"
date: 2008-05-22
forum: General Help
---

### Post by shewless on 2008-05-22
Fresh install of 8.04 on my desktop.

I get freezes approx once a day... When the freeze occurs, my mouse can still move, but nothing else is responsive... my only option is to hard boot the system.

I thought it was firefox at first, or java or flash... but the latest time it happened I didn't have firefox opened!

I tried looking at /var/log but I don't know where to start.

Is there a debugging mode I can attempt to enter then the freeze occurs? Or can you recommend some log files to start with??

The last freeze occured when I had a remote desktop session opened and one terminal window..

Thank you

---

### Post by nick_h on 2008-05-23
Use System->Administration->System Log to view the log files.  Have a look at kern.log, syslog, messages.

Try to reboot using the [Magic SysRq](http://ubuntuforums.org/showthread.php?t=617349) keys rather than a hard boot.

If you are running with Visual Effects try disabling them.

---

### Post by shewless on 2008-05-23
Cool - magic keys... thanks :)

I am running visual effects but it would be depressing if I had to disable them - and I would hope I could find a log somewhere indicating that was the problem.

I'll try again to view the log files, but I already looked at those ones in /var/log and I didn't see anything that stood out (though I'm not sure what I'm looking for)

Thanks again,

---

### Post by shewless on 2008-05-27
The magic keys allow me to reboot my system cleanly - so that is a great start - still haven't found anything in the logs yet.
It does seem to be "desktop effects" related... any clue as to what log files to look into for that?
Thanks!

---

### Post by nick_h on 2008-05-28
Look at all the log files.  I used to get freezes with Visual Effects enabled but could never find anything in the logs.  When my system froze I couldn't even reboot with the magic sysrq keys.

I guessed the problem was to do with my graphics card so I made sure that my drivers and video bios were the latest versions and it seemed to fix the problem.  Be careful if you decide to update your video bios.

What graphics card are you using?

---

### Post by shewless on 2008-05-28
yeah.. I checked all the log files.. searched for "error" - didn't see anything out of the ordinary.

maybe it is my vid card - it's a cheaper one and I think it shares mem with the mobo.

Sysinfo says:
ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01) (prog-if 00 [VGA controller])
Subsystem: C.P. Technology Co. Ltd Unknown device 2094

My memory total is reported as 1010MiB - I have a 1GB stick which is 1024MB - but I can't remember if MiB is different than MB - so I'm not sure how much mem my vid card is using.

---

### Post by nick_h on 2008-05-28
> I can't remember if MiB is different than MB
[Prefixes for binary multiples](http://physics.nist.gov/cuu/Units/binary.html)
Memory is normally expressed in binary units - multiples of 1024.
A quick google suggested your card has a dedicated 128M memory.

Your card and system memory should be fine to run Ubuntu.
I would think it is probably a subtle hardware specific bug.

---

### Post by twright on 2008-05-28
i have been experiencing similar problems with an ati card since gutsy

---

### Post by shewless on 2008-05-28
Yeah - now that I think of it - I think that was another card I had that had shared mem.

Twright - do you problems go away if you disable desktop effects?

I have been using this hardware for a long time with windows with no probs so I don't think I have a hardware issue..

---

### Post by twright on 2008-05-28
i don't know, it only happens every few days (when my laptop gets very hot)> **shewless said:**
> Yeah - now that I think of it - I think that was another card I had that had shared mem.

Twright - do you problems go away if you disable desktop effects?

I have been using this hardware for a long time with windows with no probs so I don't think I have a hardware issue..

---

### Post by shewless on 2008-05-28
alright this is getting frustrating - I disabled desktop effects and I'm still getting the same freeze.

Seems to happen around twice a day or more... mostly when I'm actually at the computer...

Today I was listening to music - the music keeps playing, my mouse still moves around, but I can't click on anything or type anything...

Common programs open are a terminal window, firefox (sometimes - not all the time), and gnome terminal server client (remote desktop) [sometimes].

I can't seem to find anything in the log files... any suggestions? should submit this as a bug?

Thank you.

---

### Post by nick_h on 2008-05-29
> I have been using this hardware for a long time with windows with no probs so I don't think I have a hardware issue.
It may well be a problem with the interaction between linux and the hardware not a fault in the hardware.

> Today I was listening to music - the music keeps playing
Yes, this happens to me.

> my mouse still moves around
My mouse also freezes but I have read other posts where people describe the mouse still moving.

> should submit this as a bug?
Check that it has not already been reported.  There are already quite a few threads about freezing in Hardy.

---

### Post by twright on 2008-05-29
> **nick_h said:**
> It may well be a problem with the interaction between linux and the hardware not a fault in the hardware.


Yes, this happens to me.


My mouse also freezes but I have read other posts where people describe the mouse still moving.


Check that it has not already been reported.  There are already quite a few threads about freezing in Hardy.
my mouse sometime keeps moving

i quite often have rhythmbox and firefox open when it occurs (but then i always have them open)

---

