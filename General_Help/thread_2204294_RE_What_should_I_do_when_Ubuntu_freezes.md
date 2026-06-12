---
title: "RE: What should I do when Ubuntu freezes?"
date: 2014-02-07
forum: General Help
---

### Post by MeanRoy on 2014-02-07
I find in [http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes](http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes)

For a fully locked up system (mouse unresponsive) during a Firefox session, I found the following directions:

"If it locks up completely, you can REISUB it, which is a safer alternative to just cold rebooting the computer.

REISUB by:

While holding Alt and the SysReq (Print Screen) keys, type REISUB."

The problem I find with this is that pressing Alt and the SysReq (Print Screen) initiates a screen capture.
Well actually a bunch due to KB repeat feature.

What am I not understanding here?

This is pretty important to me as I just went through a lengthy adventure with downloading an Ubuntu iso, booting livedisk, open term window, run fsck, correct a lengthy set of problems, and very luckily successfully re-boot.

All because Firefox froze the system and I had to hard reset the system.
I've had to do this before and didn't have a problem but once was more than enough thank you very much!

Roy

---

### Post by tgalati4 on 2014-02-07
Normally your system will do a couple of things during a freeze:  The Caps Lock and Num Lock keys will flash--which is kind of scary looking or you will get no indication and nothing you do will revive the system--including the "magic keys".  If you get a screen shot, then that means your system is not really frozen.  Try going to another window (Control-Alt-Right_Arrow) and see if it switches.  If so, then you can open a terminal and:

```
sudo killall firefox
```

The Alt-Shift-SysRq AND R--E--I--S--U--B (one or two seconds between each key) will cause various things to happen, the most important being synchronize the disks (S) and then Reboot (B).  This prevents disk errors and having to wait for a file system check (fsck) upon the next boot cycle.  I find about 50% of freeze ups can be rebooted this way.  I haven't experienced many in 8 years of using Ubuntu.

Firefox might have a busted profile.  Try clearing cache, history, etc.  Open a terminal and run firefox in it.  Watch for errors that scroll by in the terminal.

---

### Post by egeezer on 2014-02-07
But if you really get into a bind, you need to check if your SysRq key is properly activated.  Run:
```
cat /proc/sys/kernel/sysrq
```
If it returns 1, it's working its magic.  If it returns 0, it isn't

To activate:
```
sudo echo "1" > /proc/sys/kernel/sysrq
```

---

### Post by MeanRoy on 2014-02-07
Thanks very much for the replies.
I accidentally mislead you, after fixing the problems I tried this to make sure I knew how it worked. The system wasn't frozen when I did this.
On reading your reply though, I see where I messed up!
I failed to hold the shift as well.

I just knew it was something dumb.

I'll do the check to be sure the SysRq key is working properly and re-try the technique.

I don't think my firefox is hosed, I think some javascript stuff in conjunction with youtube ties up all the resources and *might* eventually return control. I do wonder about how this happens though.

Roy.

---

### Post by tgalati4 on 2014-02-07
Run Adblock Edge and Noscript and that should take care of the bad actors.  The magic sequence should still reboot the system even if it is not frozen.  Make sure all of your applications are closed.  You don't want to lose any data during a rapid shutdown.

---

### Post by ajgreeny on 2014-02-07
Use the right hand Alt + Print-Screen, not left had Alt.

---

### Post by MeanRoy on 2014-02-07
Ok guys, that does it, works fine.
Someone should make the correction to add the shift key to the instructions in [http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes](http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes)

Thanks very much!

Roy

---

### Post by tgalati4 on 2014-02-07
Actually, I think the sequence works with either the Right Alt-PrtSc key or the Left Alt-shift-SysRq key.  But I don't want to test it right now.

---

### Post by ajgreeny on 2014-02-08
> **tgalati4 said:**
> Actually, I think the sequence works with either the Right Alt-PrtSc key or the Left Alt-shift-SysRq key.  But I don't want to test it right now.

OK, but how you hold the left Alt+Print-screen and then type REISUB is beyond me; it must require an unusual use of the nose on the keyboard.

---

### Post by egeezer on 2014-02-09
Naw, just big hands! :-)

---

### Post by Wheel on 2014-02-24
> **egeezer said:**
> But if you really get into a bind, you need to check if your SysRq key is properly activated.  Run:
```
cat /proc/sys/kernel/sysrq
```
If it returns 1, it's working its magic.  If it returns 0, it isn't

To activate:
```
sudo echo "1" > /proc/sys/kernel/sysrq
```

I have been wondering why the REISUB trick hasn't been working for me since using 13.10.  (It always worked in the past for those few occasions when it was needed.)

So I tried your "check".
It returned neither 1 nor 0.

It returned 176.
Any idea what that means?

FWIW--I am able to execute this safe reboot in a Virtual Terminal. (Tested when the system was NOT frozen.)
Although both the R and the E yield a return of "This sysrq operation is disabled".  But it DOES reboot.

---

