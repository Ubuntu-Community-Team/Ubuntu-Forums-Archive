---
title: "AMD Catalyst 8.3 and Compiz"
date: 2008-03-12
forum: General Help
---

### Post by Cable on 2008-03-12
I just finished installing the most recent driver for my ATi Radeon 9800 XT (the 8.3 release) using [these]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually") instructions.  I followed them exactly.  The drivers installed fine and are working.  However, when I attempt to enable Compiz, I get a popup that says "Desktop Effects could not be enabled."  When I had the 8.2 release installed, Compiz would fire up right away.  It was a bit sluggish due to the subpar ATi driver, but it worked.  I wanted to try 8.3 to see if it was any better, and now it won't start Compiz at all.

I have fglrx whitelisted in the Compiz file mentioned in the directions linked about as well.  Also, when I try to start Compiz and I get the error mentioned above, many Compiz entries appear in the System Monitor.  This makes my CPU and RAM usage shoot way up.  Check out the screenshot below.

I'd really like to try Compiz with this driver release.  Any ideas on how to fix this?

---

### Post by Wise Ferret on 2008-03-12
I think I have the solution for you.

Using the whitelist trick didn't work for me either - fglrx is still blocked by compiz. I can avoid it, though, by disabling the driver check done by compiz on load altogether. This can be done easily by creating the file ~/.config/compiz/compiz-manager, and pasting into it:

SKIP_CHECKS=yes

Then reload compiz. Tell us if it worked!

---

### Post by Cable on 2008-03-13
Yep, that worked perfectly.  Compiz is working!  And it doesn't seem laggy like it was before 8.3.  Thanks!  However, I now have another problem.  When I play videos, I still can't see the video.  I can hear it, but cannot see it.  Doesn't matter what play I use (I have Totem, VLC, and MPlayer).  I saw on the Phoronix forums that people were getting video playback with Compiz enabled.  Any advice?  EDIT:  I have determined that I can see videos in fullscreen mode, but not windowed mode.

---

### Post by heng on 2008-03-20
You need to run a patched version of mplayer.
[http://ubuntuforums.org/showthread.php?p=4538510#post4538510]("http://ubuntuforums.org/showthread.php?p=4538510#post4538510") has an mplayer deb which should work under Hardy.

---

