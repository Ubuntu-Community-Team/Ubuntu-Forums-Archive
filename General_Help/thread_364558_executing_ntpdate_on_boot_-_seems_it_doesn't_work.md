---
title: "executing ntpdate on boot - seems it doesn't work"
date: 2007-02-18
forum: General Help
---

### Post by robome on 2007-02-18
Hi!

I currently try to figure out if ntpdate is called on boottime in my system (feisty herd4) or not.

It *should* be called when the network interfaces come up (ifup), therefore the /etc/network/if-up.d/ntpdate is present. And it's indeed called when I manually call ifup -a after booting--an entry in the syslog then shows something like "adjust time server ... offset ...".
But I don't see such a syslog entry for boottime, so I fear there's something wrong. Any ideas what that could be or how to be sure everything is ok?


And another oddity: ifup is called by the network script which is rcS.d/S40networking. So if everything works well, ntpdate sets the system clock at S40. But *after* that S50hwclock.sh calls hwclock --hctosys which sets the system clock to the hardware clock.
So doesn't hwclock needs to be called before ntpdate?

In Debian (at least etch) hwclock seems to be called much earlier as S11hwclock.

Bye,
Robert

---

### Post by robome on 2007-02-18
> **robome said:**
> I currently try to figure out if ntpdate is called on boottime in my system (feisty herd4) or not.

It *should* be called when the network interfaces come up (ifup), therefore the /etc/network/if-up.d/ntpdate is present. And it's indeed called when I manually call ifup -a after booting--an entry in the syslog then shows something like "adjust time server ... offset ...".

In the meantime I've done some more research and tests with echos in the ntpdate script.
ntpdate really isn't started at boottime. Reason is 
```

if [ "$METHOD" = loopback ]; then
	exit 0

```
in the script. Echoing $METHOD gives "loopback" while booting and "static" upon manual call.

I don't know what those methods are and how they're set. But how it currently works is contradictory to what I think ntpdate is for (setting the time at bootup).
Of course I could simply remove all checks from the script, but I guess it's like it is by some purpose. Maybe someone can shed light on that purpose.

Robert

---

### Post by ElrohirMacBeorn on 2007-02-22
At last I found somebody, who has the same problem as me! For me too, time (effectively) isn't updated to internet while booting -- as well at home as at work. Now I linked /etc/network/if-up.d/ntpdate to /etc/rc2.d/S17ntpdate and thus it does work now with minimal manipulation. But of course, now ntpdate is called twice, once from rcS.d/S40networking and then from rc2.d/S17, so this isn't really an elegant solution. And I still wonder, if it is a bug, that hwclock is called after ntpdate or if there is some reason to it?

Elrohir

---

### Post by Sodki on 2007-02-22
Thank you, ElrohirMacBeorn, I've lost a few hours of my life thanks to this bug.

---

### Post by bw44 on 2007-12-11
> **Sodki said:**
> Thank you, ElrohirMacBeorn, I've lost a few hours of my life thanks to this bug.

This may be an unwarranted cross-post, but this is one of two threads that went silent back in February about problems with ntpdate not running at boot time.  (I think you also posted to the other thread: [http://ubuntuforums.org/showthread.php?t=366041](http://ubuntuforums.org/showthread.php?t=366041)).

Was there ever a resolution of this problem?  I didn't understand ElrohirMacBeorn's post -- it went over my head.  I'm running Gutsy and ntpdate works fine from the command line.  But how do (can) I get it to run at boot time?

Any help much appreciated.

---

### Post by bw44 on 2007-12-14
> **bw44 said:**
> . . .Was there ever a resolution of this problem?  I'm running Gutsy and ntpdate works fine from the command line. . .  But how do (can) I get it to run at boot time?

The answer I needed was on the UbuntuTime Community Dcoumentaion page [https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=NTPTimeSynchronisation#head-7ce84659ce7371da7976d6527d1e0263297e90ff](https://help.ubuntu.com/community/UbuntuTime?action=show&redirect=NTPTimeSynchronisation#head-7ce84659ce7371da7976d6527d1e0263297e90ff)
where it says:
```
Command Line ntpdate

Ubuntu comes with ntpdate as standard, and will run it once at boot time to set up your time
 according to Ubuntu's NTP server. However, a system's clock is likely to drift considerably
between reboots if the time between reboots is long. In that case it makes sense to correct
the time occasionally. The easiest way to do this is to get cron to run it every day. With your
favorite editor, create a file /etc/cron.daily/ntpdate containing:

sudo ntpdate ntp.ubuntu.com

Make sure that you make this new file executable:

sudo chmod 755 /etc/cron.daily/ntpdate
```

I still don't think it runs at boot time, but the above cron job does what I want.  (With thanks to qpieus who first pointed this out to me in another thread.)

---

