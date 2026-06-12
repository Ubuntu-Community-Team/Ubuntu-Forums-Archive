---
title: "Stuck at low resolution- laptop mode- cannot change"
date: 2012-11-01
forum: General Help
---

### Post by sumithar on 2012-11-01
Hi Community,
Very long post- sorry, please bear with me

My current problem is that my display on the 19" monitor is showing laptop mode and is like 640x480 and won't let me change in Display applet.
Here is the sequence of issues
• My computer started to freeze at random especially on video pages.
• I asked a question about this on this forum and the only response I got was to upgrade to 12.04, but I was a bit reluctant to perform an upgrade to fix just this issue.
• I posted a bug report and I was asked for additional information that I provided but then nothing happened and now looks as if the bug is closed due to no movement
• I finally got fed up and upgraded to 12.04 thinking that will help.
• Made problem worse and now the freeze was happening even if I was just on desktop
• Thought problem could be due to video card, so removed that and connected to on-board video card
• I had a 2 monitor set up, one was 19" and one was 15" and for some reason, the 15" was considered the "main" monitor.
• My on-board video card had only 1 output, so I connected the 19" monitor to it (VGA)
• When I booted up I saw nothing except a message about "cannot display this video mode"
• Rooted around this forum and found a solution that involved hitting the down arrow at bios prompt and making changes to grub- basically uncommenting a line 
#GRUB_GFXMODE=640_480
• did that and now can boot up but only into aforesaid low-res mode

So now I really would appreciate some insight on what I can do next to fix this problem. I need to be able to change my resolution to 1280x1024 and not have a recurrence of the freezing problem.

I have rooted around some more in here and become confused between Nvidia and nouveau and additional drivers and what not.

Thanks!

---

