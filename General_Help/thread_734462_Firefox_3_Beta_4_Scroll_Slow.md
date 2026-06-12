---
title: "Firefox 3 Beta 4 Scroll Slow"
date: 2008-03-24
forum: General Help
---

### Post by DocHoliday52090 on 2008-03-24
There have been other threads on this, but I haven't found one with FF3B4. 

Is anyone else experiencing this? I'm running Hardy Beta, after a long break from Ubuntu on Windows. 

FF3B4 scrolls fine on Windows, and smooth scrolling is absolutely unbearable. Is Pango still causing trouble?

Any thoughts?

---

### Post by electrosoccertux on 2008-03-24
> **DocHoliday52090 said:**
> There have been other threads on this, but I haven't found one with FF3B4. 

Is anyone else experiencing this? I'm running Hardy Beta, after a long break from Ubuntu on Windows. 

FF3B4 scrolls fine on Windows, and smooth scrolling is absolutely unbearable. Is Pango still causing trouble?

Any thoughts?

So, something funny I found, go to fullscreen by pressing F11 and suddenly it's not slow anymore.

My laptop resolution is pretty low anyways (1280x768) so I surf on fullscreen regardless.

Sucks for desktop though.

---

### Post by enchantedsky on 2008-03-24
At first, I thought you were asking how to adjust how many lines to scroll when moving the mouse wheel, that's easy. But what you're talking about sounds like a bug in Firefox Beta 4

Well, it is beta software, so I'm sure they are hammering out the bug causing it. I have experienced it as well. We can only wait it out until the final release really.

---

### Post by DJ_Peng on 2008-03-24
I seem to remember seeing this posted about on the Mozillazine Forums in the Firefox Builds section (where they discuss testing builds). You may want to check there, but beta 5 is due out later this week so your issue may be already resolved and waiting to get to your computer.

---

### Post by AlphaBob on 2008-03-24
Hi,

I just installed the 8.04 beta today and have exactly the same issue, VERY slow scrolling on the included FF3 beta.  I loaded the original FF2 and it has the same problem.  So I suspect it is something to do with the graphics system and not Firefox itself.

Very difficult to use at the moment.  As the gentleman said, hopefully this is due to debug code.

Edited to say that it does scroll MUCH faster in the full-screen mode (F11 toggles).  But it is still noticeably slower than FF2 under 7.10

---

### Post by anodizer on 2008-03-25
I think it has something to do with compiz-fusion. If you disable it Firefox will more likely behave faster.

---

### Post by chewit on 2008-03-25
I was testing out FF3beta4 at my school on a windows pc. scrolling pages was fine, but full page zoom is slow.

---

### Post by guyminuslife on 2008-03-27
Just installed Hardy. Same problem here. It just responds slowly generally, and especially for scrolling. Not running Compiz, didn't have any problems with Gutsy version.

---

### Post by LowSky on 2008-03-27
funny mine seems fine, running hardy as well

---

### Post by DJ_Peng on 2008-03-27
I hope someone has either made sure there was a bug filed or mentioned this slowness at the Mozillazine Forums so we can try to get it fixed.

(btw, the Mozillazine Forums are owned by Mozilla, although devs do read it fairly often, which is why I direct so many people there)

ETA: Mine as well, LowSky, but I'll grant that just because I don't have an issue doesn't mean an issue may not exist.

---

### Post by forrestcupp on 2008-03-27
I'm using FF3 beta 4 with no problems.

You're not by chance using an ATI card with Compiz are you?  If so, that is your problem.  The newer drivers are better than they were about FF scrolling, but they're still not great.

---

### Post by fmonjaraz on 2008-04-01
I turned off all the visual effects on system-appearence and the scrolling problem stopped.

---

### Post by sc00ter on 2008-04-08
I suspect it's a combination of Compiz-fusion and the video drivers specific to certain hardware. When I fire the Live CD for 8.04 Beta, on my Intel Graphics based laptop (945GM), with CF enabled, content scrolling within FF3B4 is dog slow.

Turn off CF and the speed of scrolling content is acceptable.

This Launchpad entry may shed some light on the issue:
[https://bugs.launchpad.net/ubuntu/+bug/204308]("https://bugs.launchpad.net/ubuntu/+bug/204308")

---

### Post by Endolith on 2008-04-26
Just installed Hardy and have the same problem in beta 5 with Nvidia drivers and no Compiz.  Full screen does not help, it still scrolls very slowly

---

### Post by EricDB on 2008-04-26
> **Endolith said:**
> Just installed Hardy and have the same problem in beta 5 with Nvidia drivers and no Compiz.  Full screen does not help, it still scrolls very slowly

Same here.  I mostly notice it in Gmail and Slashdot.  Gmail is almost unscrollable...if I flick my finger on the scroll-edge of my touchpad, it takes maybe 10 seconds to get all the way to the bottom of the Inbox page (which is only about two screen-heights tall!)

I'm using the nvidia-new driver.  Turning off visual effects didn't help, but it DID reset all the Compiz settings I'd spent an hour carefully customizing last night...inexcusable!...but back on topic...switching to full-screen didn't help, either, as some have recommended.

Another suggestion I tried is changing to the Murrine theme.  That didn't affect anything, either.

I've had this problem since I first installed FF Beta 3 on 7.10, and it still exists for me out of the box in 8.04.

---

### Post by Endolith on 2008-04-26
Hmmm....  I'm wondering if this has to do with the way buttons and checkboxes are drawn using the GNOME theme now, since it slows down Gmail which has lots of checkboxes.

---

### Post by charonn0 on 2008-04-29
Same troubles here. After disabling the **Ubuntu Firefox Modifications** addon in Firefox, scrolling was back to normal. Even with Compiz-Fusion at full blast it's all good.

What the heck is the Ubufox or whatever addon supposed to be good for?

---

### Post by Endolith on 2008-04-29
> **charonn0 said:**
> Same troubles here. After disabling the **Ubuntu Firefox Modifications** addon in Firefox, scrolling was back to normal. Even with Compiz-Fusion at full blast it's all good.

What the heck is the Ubufox or whatever addon supposed to be good for?


I disabled Ubuntu Firefox Modifications and I still have slow scrolling.  But the widgets still look just like others on my system, so I don't know if it has changed anything.

---

### Post by Endolith on 2008-04-30
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217580](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/217580)

---

### Post by unimatrix on 2008-05-31
I disabled Compiz and must say it is MUCH better, but still NOT as good as in Windows. What a shame.

---

### Post by p110011 on 2008-06-04
My laptop with a fresh install of Hardy got to be so laggy the mouse responce was almost 2 seconds slow.
It's an HPZV5000 w/ati mobility 9100(It's Compiz/Fuzion black listed) but I'm running the advanced desktop anyways.

So after reading about Compiz slowing things I started unchecking some of it's settings and found the Cube to be the problem.
After that I started reseting the Cube settings and found the problem was the opacity when not rotating caused all of my system lag. It would even freeze my laptop during screen saver mode.

It must be why my card is black listed but I'm good for now:)

---

