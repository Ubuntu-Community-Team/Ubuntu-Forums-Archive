---
title: "PuTTY window update issue with Ubuntu 13.10"
date: 2013-12-03
forum: General Help
---

### Post by Newbunto on 2013-12-03
PuTTY was working fine on Ubuntu 12.04 LTS. Now on 13.10 I have an issue were the window updates seem to lag by a few seconds or even many, many seconds. Clicking on another window seems to get the PuTTY window to update.

PuTTY version is Release 0.63.

The problem happens with Ubuntu SSHing to another Linux box on the local LAN (thereby eliminating any other operating systems from consideration and eliminating internet glitches from consideration). In any case I can tell that it's not a network lag issue because sometimes the window shows lines of text that are only partially updated i.e. top half of one line of text with bottom half of another line of text.

Suggestions?

---

### Post by Newbunto on 2013-12-16
bump

---

### Post by phoyce2 on 2013-12-17
Newbunto,

Out of curiosity have you tried an earlier release of PuTTY to compare the performance between them.  Sometimes the latest and greatest versions aren't exactly that. :P

---

### Post by efflandt on 2013-12-17
I use PuTTY in Windows to access Linux or my NetBSD shell account, etc. But I am just curious why you would use PuTTY instead of regular ssh "from" Ubuntu?

The ssh client is installed by default in Ubuntu, and if used from a terminal in X it automatically uses an ssh-agent to keep track of your password or pass phrase for a key once you enter it until you log out of X or shutdown, so you do not have to re-enter it to reconnect ssh or using scp, etc. later. I cannot remember any issues using regular ssh to that NetBSD internet shell account or locally to any Ubuntu, Debian on a Raspberry Pi, or a headless Celeron 333 MHz box that has been running obsolete SuSE 8.2 for the past 10 years. So I doubt if regular ssh would have whatever issues you are seeing with PuTTY (unless a local DNS issue results in lag initially connecting).

---

### Post by bashiergui on 2013-12-17
I am also curious why you'd use putty in ubuntu. 

I'm not sold on the lack of network lag. Are you traversing any firewalls? I would want to look at top on both server & client to see what's up when you see the lag.

---

### Post by Newbunto on 2013-12-19
> **efflandt said:**
> I am just curious why you would use PuTTY instead of regular ssh "from" Ubuntu?

I am happy to use it for a while for fault isolation anyway but two issues that spring to mind are:


[LIST]
[*]PuTTY has mouse support (which I do use) but it doesn't seem to be working when using regular ssh from a terminal window (more specifically, roll works with ssh but not with PuTTY but click works with PuTTY but not with ssh, while with PuTTY on Windows both work) - maybe this is a config issue 
[*]using ssh from a terminal is just more window clutter - maybe this is fixable 
[/LIST]
 
It wouldn't surprise me if there were other terminal emulation compatibility issues.

Edit: PS "roll works" means "roll event passed through to application and application responds to roll". With PuTTY on Ubuntu roll is intercepted by PuTTY and implemented by PuTTY (scrolling back the terminal) rather than letting the application handle it.

Edit: PS Yes, significant terminal emulation compatibility issues. Could be a config issue.

---

### Post by Newbunto on 2013-12-19
> **bashiergui said:**
> Are you traversing any firewalls?

Not when testing from Ubuntu to other Linux box on local LAN.

Also, note my comment about an unupdated window with half a line of text drawn or not drawn. It's difficult to see how network lag could cause that.

---

### Post by Newbunto on 2013-12-22
> **phoyce2 said:**
> have you tried an earlier release of PuTTY to compare the performance between them.

Good idea. Not sure how possible this is though.

Before I upgraded from Ubuntu 12.04 LTS to Ubuntu 13.10 I imaged the disk to an external disk. So I am able to boot into 12.04, exactly as it was, and check what was on there.

PuTTY reports itself as "Unidentified build Aug 7, 2013 12:25:03"

Yeahright!

I have little idea where that came from. Whatever it is, it worked well! I believe that I installed PuTTY with [FONT=courier new]apt-get install putty[/FONT] when originally on Ubuntu 11.10.

It is possible even that the version of PuTTY that I had on 12.04 is later than the version of PuTTY that I have now. Unfortunately the PuTTY that I have with Ubuntu 13.10 identifies only as "Release 0.63" (no date) so I don't know.

Does any of this help?

---

### Post by Newbunto on 2013-12-22
> **Newbunto said:**
> PS Yes, significant terminal emulation compatibility issues.

One unresolved issue (with using ssh instead of PuTTY) that I have investigated somewhat is now here:

[http://ubuntuforums.org/showthread.php?t=2195182](http://ubuntuforums.org/showthread.php?t=2195182)

---

### Post by Newbunto on 2013-12-29
I copied the PuTTY executable from the disk image made before the upgrade to Ubuntu 13.10

With this arrangement I am able to run the two PuTTY executables side by side, under Ubuntu 13.10. The old one just works even under Ubuntu 13.10. The new one does not work properly, suffering from weird delay in updating the window.

I suppose this is a workaround for me, albeit not a good one in the long term.

So it would seem that the version of PuTTY available under Ubuntu 13.10 is either broken or uses an interface in a different way or a different interface and the software behind that interface is broken.

---

