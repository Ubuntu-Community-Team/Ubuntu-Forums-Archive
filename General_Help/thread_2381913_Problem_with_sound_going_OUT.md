---
title: "Problem with sound going OUT"
date: 2018-01-06
forum: General Help
---

### Post by Beautymist on 2018-01-06
Hey,

This is a problem I've had for some time under xUbuntu with the output sound default settings on my laptop.

Using Skype, I can hear the other caller (the sound goes IN), but can't be heard by the other caller (the sound doesn't go OUT from my computer).
Same with listening to music or watcing videos: the sound is produced (I can see the waves going up and down on the monitor) but does not get OUT on the proper channel so I can actually hear it.

I've tried AlsaMixer before to solve this, and it was a temporary fix. It seems that by turning my computer off and restarting it, the default sound settings were back all over again - and obviously they don't work properly.

I hope you guys can help. Thanks!

-BM

---

### Post by TheFu on 2018-01-09
Different DEs use different sound controllers.  Most use pulse-audio these days.
I had an issue with pulse failing/crashing whenever I changed between applications. Then it wouldn't restart automatically.  Had this issue for over a year. There was a solution - to switch from using socket communications to using shared memory for pulse.  Don't know if that will help you or not.  To set it up, 
edit the ~/.config/pulse/client.conf file.  Add/unset the 
```
enable-shm = no
```
If the file doesn't exist, copy one from under /etc/ and use that copy, but really that line is the only line that isn't just a comment in mine.

Don't know if it will help you, but it made pulse-audio stop crashing and basically work all the time for me.  Of course, this assumes you have all the other stuff setup correctly in the pulse-controller applet.

As for anything to do with skype, I cannot help. I won't use that software.

---

### Post by Beautymist on 2018-01-10
@TheFu thank you! will check that out

---

### Post by TheFu on 2018-01-10
If this fixed it, please mark the thread as "solved".  

If not, others might be able to help, so post what you've tried. Often, running through the *Ubuntu Sound Troubleshooter* will be helpful. Google for it. It has a tool that generates lots of information about the sound subsystem.  The folks who deal with sound a bunch know that output well and can spot issues quickly.

---

