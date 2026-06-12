---
title: "What has just happened??"
date: 2017-06-01
forum: General Help
---

### Post by monkeybrain20122 on 2017-06-01
Hi,

I have Ubuntu 16.04 on a Toshiba Satellite laptop, it is normally very fast and responsive. Today I took the notebook to my client to show him my codes, then turned off the laptop, went home and when I turned it on it became very sluggish, it took forever to open Firefox and it ran at 100% cpu even with one tab, same with other applications. I ran a bench mark on Octave that usually takes about 7s now it took 30s. Chrome basically made the desktop animations slow down like molasses. 

I have not installed anything and there has not been any update for days: I haven't done anything to alter the system, this just happened out of the blue. 

I  rebooted a few times. Looked at top and System monitor but couldn't find any abnormal activity (other than high cpu usage when starting up any application and the 100% usage persists for a long time) I checked the logs, nothing special, I renamed $HOME/.config and rebooted, I uninstalled apt-xapian-index (it was upddating a lot and uses a lot of cpu apparently) .. After a few hours and a dozen reboots and trying out some random trouble shooting tips from old forum posts, it was still slow and sluggish, something was broken but not sure what or how.

Then I thought it might be hardware related, the hard drive might be dying (I don't don't if that even make sense, I was desperate) So I booted off another Ubuntu from an external drive and ran a SMART test on the internal drive. I ran the long test and it passed everything and got a good bill of health. When I rebooted to my surprise everything is back to normal again, Ubuntu is as fast as it has always been and no more 100% cpu usage, Firefox starts and closes immediately Seems that the SMART test fixed it!!!

This is mystery. Can anyone offer a theory to what had happened? Thanks

---

### Post by monkeybrain20122 on 2017-06-02
Any thought?

---

### Post by monkeybrain20122 on 2017-06-04
Bump,

---

