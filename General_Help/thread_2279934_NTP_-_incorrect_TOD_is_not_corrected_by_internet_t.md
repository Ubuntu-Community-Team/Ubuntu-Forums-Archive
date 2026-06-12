---
title: "NTP - incorrect TOD is not corrected by internet time."
date: 2015-05-26
forum: General Help
---

### Post by aqk on 2015-05-26
I just upgraded from 14.10 to 15.04, and I happened to have a hardware clock set about 8 minutes behind. (Don't ask why)
I noticed that Ubuntu will not correct this clock.
As well I use Grub to dual boot into Windows-10, (10076) AND IT will not correct my clock via the internet either!
When did this start happening?
In the past, anytime my clock was off by less than an hour, it was usually corrected at boot time, either by Ubuntu or by Windows.

If- IF - my clock is off by two minutes, will it always stay incorrect like this? I used to rely upon PRECISE network time. 
When did NTP get shuffled outa the boot sequence?

---

### Post by SeijiSensei on 2015-05-26
Can you set the hardware clock manually with:
```
sudo hwclock --set --date '10:11:12'
```
Does it survive a reboot?

How old is the computer?  Maybe the clock's battery needs replacing.

---

### Post by tgalati4 on 2015-05-26
Why is your hardware clock set 8 minutes behind?  It's possible that the ntp daemon has been modified to not correct clocks that are grossly out-of-sync.  

Look in /var/log/syslog for any ntp messages.

What is in your ntp configuration file?  Perhaps there is a configuration setting change from 14.10 to 15.04.  These things happen with in-place upgrades.

You could purge and reinstall.

```
sudo apt-get purge ntp
sudo apt-get install ntp
```

---

