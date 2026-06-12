---
title: "Bizarre random logout"
date: 2007-11-14
forum: General Help
---

### Post by cygnine on 2007-11-14
Here's my problem: Gutsy randomly ends my session and sends me back to the login splash screen. I don't really know what the problem is, so I'm going to describe what I've done and observed:

- I've never had this happen *while* I'm working on the computer
- I feel like it's logging me out because at one point I had my laptop lid open while I wasn't working on the computer, and I saw that it ran a few shutdown scripts exactly as if I were logging off (not rebooting).
- The computer does *not* reboot. It just goes back to the startup screen
- This is a dual-boot machine, so I can boot into Windows XP. I've had no problems there whatsoever.
- I had Edgy installed on here earlier, and there was no problem
- I leave my computer on for about 12 hours a day. This logout-thing happens about 2-3 times a day. Needless to say, I've started compulsively saving. 

Here's some information which may (or may not) be of use:
- I have compiz running with all sorts of nifty effects
- My video card is an ATI Radeon X1300
- As is common with ATI video card people around here, I can't suspend/hibernate the machine; there's some problem with the (closed-source! boo!) video driver.

Basically, I don't even know what the problem is. Why would my machine make log me out randomly?  The problem with troubleshooting this is that the event is intermittent. I can't necessarily reproduce the bug at will. Any help/ideas would be greatly appreciated.

---

### Post by dltwyman67 on 2007-11-15
Same thing happening here on Dell Inspiron 1721 has ATI card 64 bit amd x2,  running 7.10. Got the sound issue fixed but the logoff problem still remains and most apps are not able to save their state so its a big pain.

---

### Post by secular on 2007-11-15
cygnine, mine logs out by itself and goes to the login screen, too.

It never logs off by itself when I'm at the computer. If I step away for (maybe) 30 minutes or 1 hour, it does this.

I run a home-brew desktop. I'm running Compiz. My video card is an nvidia GeForce 7 series.

In my power management settings, both computer and display are set to never turn off.

I dual boot with PCLOS, but I don't have this problem there.

---

### Post by Whiffle on 2007-11-15
Sounds like something is crashing X, and then gdm auto restarts.  Maybe check and make sure your screensaver is working correctly.

---

### Post by secular on 2007-11-15
> **Whiffle said:**
> Sounds like something is crashing X, and then gdm auto restarts.  Maybe check and make sure your screensaver is working correctly.


Thanks. I went to System, Preferences, Screensaver and scrolled down the list of screensavers. When I did that, selecting certain screensavers took me to a black screen with some text and then quickly to the login screen. The black screen passed too quickly for me to read anything.

So, it does look like there is something wrong with the screensavers. How do I check that and fix it?

---

### Post by cygnine on 2007-11-16
> **secular said:**
> Thanks. I went to System, Preferences, Screensaver and scrolled down the list of screensavers. When I did that, selecting certain screensavers took me to a black screen with some text and then quickly to the login screen. The black screen passed too quickly for me to read anything.

Hm, I did the same thing, but my screensavers appear to be functioning normally in that window. However, I changed my screensaver now, and I'll report back after a day and let y'all know if it got better or not. I'll also try turning off my screensaver if this first try doesn't fix it.

Thanks for the suggestion, Whiffle.

---

### Post by dltwyman67 on 2007-11-16
definitely FIXED the problem here on the Dell Inspiron 1721 to specify a working screensaver - seems to be maybe related to the openGL screensavers and the ATI restricted driver

---

### Post by bordaigorl on 2007-11-16
I have a similar problem (Kubuntu 7.10, Compiz) but my system pushes me out while I'm working. The issue is -obviously- not related to the screensaver.
Any hint?

---

### Post by secular on 2007-11-18
There were some updates earlier today, and a couple of them were gdm-related. I was hoping this would solve my problem, but it hasn't.

I'm able to avoid the system logging out by itself by using "blank screen" as my screensaver. I really like putting my screensaver on "random," though, so this is a major annoyance.

I appreciate all that Ubuntu has done, but I hope that some developer is just as annoyed as I am and can find a fix.

---

### Post by cygnine on 2007-11-18
> **secular said:**
> I'm able to avoid the system logging out by itself by using "blank screen" as my screensaver. I really like putting my screensaver on "random," though, so this is a major annoyance.

For the past couple of days, this has appeared to fix the problem for me, too. It is kind of annoying to have to choose this, but it's much better than random logouts. 

dltwyman67, if you're still around, which screensaver fixed the problem for you?

---

### Post by secular on 2007-12-03
A total reinstall seems to have fixed things. Or maybe a recent update did the trick.

Regardless, my system isn't randomly logging out.

---

### Post by epitaph123 on 2008-01-03
it happens while I'm working... so it can't be the screen saver causing the logout for me, anyone able to help fix this?

---

### Post by RC Howe on 2008-01-03
I used to be horribly annoyed because whenever I typed Shift+Delete Compiz would kill X and go back to the login screen. Maybe it's that, if it happens while you're working. However, that doesn't happen for me in Gutsy.

---

### Post by mlwgszgao on 2008-01-06
Yea, this problem is really annoying. I'm trying the screensaver thing now, hopefully it'll work, but it'd be great if anyone could find out the real problem with it.

---

### Post by Resurge on 2008-06-03
> **bordaigorl said:**
> I have a similar problem (Kubuntu 7.10, Compiz) but my system pushes me out while I'm working. The issue is -obviously- not related to the screensaver.
Any hint?

Sorry for digging up this old thread, but I'm having the exact same problem as the above quote.

I'm running hardy on an ASUS f3sv-018c with an Nvidia 8600gs.

The problem occurs at random moments.

---

### Post by aeon on 2008-06-04
I have the same problem on my box and it also kicks me out when i'm working so i dont really know what the problem is.. anyone know if the screensaver trick helps?

---

