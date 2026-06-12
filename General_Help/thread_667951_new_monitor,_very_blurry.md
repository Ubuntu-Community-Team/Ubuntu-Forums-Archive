---
title: "new monitor, very blurry"
date: 2008-01-14
forum: General Help
---

### Post by TeeAhr1 on 2008-01-14
Just got a new-to-me HP A4331D monitor, this thing is ENORMOUS, 20" screen, max res of 1600x1200.  The monitor God would use if he needed a computer.

The first thing I did, of course, was go online to find out the sync ranges and refresh rates and all that.

hsync: 30-82khz
vsync: 48-150 hz
max res/refresh: 1600x1200@60

I then ran a dpkg-reconfigure xserver-xorg, so I am now, in theory, running at optimal rate.  But I have these funny "blurs" that trail off to the right from words or icons.  It's most noticeable on a dark background, and is incredibly annoying.  I have the onboard intel graphics set, so it's not a problem with a proprietary driver (those who would give up essential liberty for a video driver deserve neither liberty nor video drivers).  Where do I go from here in diagnosing this?  Thx in advance, as always.

-pd-

---

### Post by amadeus266 on 2008-01-14
Try booting from the live cd and see if you get the same results. If not, look at the xorg.conf file created by the cd and see what may be different than the one your currently using.  Maybe the rates you chose are close but not quite optimal for that monitor.

---

### Post by TeeAhr1 on 2008-01-15
Dammit.  Same artifacts on two different live CDs, it's the monitor.  That's a real shame.

---

### Post by Bigs11 on 2008-01-15
If it's an LCD monitor, you need to set display to native resolution of your monitor.

---

