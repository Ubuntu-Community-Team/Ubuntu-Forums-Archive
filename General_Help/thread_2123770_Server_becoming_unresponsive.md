---
title: "Server becoming unresponsive"
date: 2013-03-08
forum: General Help
---

### Post by MiniStephan on 2013-03-08
Hello,

I have an Ubuntu 12.04.2 machine set up that I'm using as a server for my house.  Occasionally, it will become unresponsive and I am forced to reboot.  When it does so, only the background shows up, nothing else of the GNOME desktop.  When I Ctrl+Alt+F# to another console, after I put my username in, it sits there, doing nothing, not asking for a password.  The same thing happens if I try to FTP or SSH in.

Can you help me figure this out?  I don't even know where to begin, as I am not experienced in troubleshooting this sort of issue.

---

### Post by tgalati4 on 2013-03-08
Typically you would log in using ssh and run* top* in a terminal window.  Then wait for the machine to freeze and look at what is running.  Pay attention to IO Waits. Take a picture of the screen and post it.  It's possible that you have a hardware problem.  A disk that is having read problems will cause a machine to behave in a similar fashion.

---

### Post by MiniStephan on 2013-03-08
The problem is that it's not a consistent thing.  It will run fine for a few days, sometimes a week, but then Poof! it stops responding.

---

### Post by SeijiSensei on 2013-03-08
This sounds like a hardware problem, possibly bad memory.  Try rebooting and running memtest from the grub menu (hold down the Shift key during boot if you don't see the menu).  I'd let it run overnight.

Before that, though, I'd look through /var/log/syslog and see if there are any obvious problems.

---

### Post by MiniStephan on 2013-03-09
I tried memtest86+ but it didn't come up with anything.  Could it be a drive read issue?

---

### Post by SeijiSensei on 2013-03-10
You'd see drive errors in /var/log/syslog.  That's why I suggested starting with that.  You could also install the [smartmontools]("https://help.ubuntu.com/community/Smartmontools") package and run some diagnostics on the drive.

---

### Post by MiniStephan on 2013-03-18
Sorry for the lack of response, guys.  I had a drive fail in my raid array.  It's pretty old so I'm not surprised.  HOWEVER: this did not finish the issue.

I got this message today when it went unresponsive:
> task jbd2/cciss!c0d0:221 blocked for more than 120 seconds

This seems to be pretty close, I'll try some solutions from there:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/666828](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/666828)

---

