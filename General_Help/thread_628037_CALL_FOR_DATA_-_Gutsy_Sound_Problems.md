---
title: "CALL FOR DATA - Gutsy Sound Problems"
date: 2007-11-30
forum: General Help
---

### Post by kjkrum on 2007-11-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/34947](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/34947) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm fed up with the lack of progress on fixing the volume control problems in Gutsy, and since I am currently unemployed and bored, I'm taking it upon myself to try to fix it despite my limited experience with C/C++.  This is a call for information to help me figure out what layer(s) of the sound system I should be looking at.  PLEASE NOTE: If you are NOT experiencing these problems, your input is still helpful!  Please reply with the following information:

a. The make and model of your sound device
b. Which of the following problems you can or cannot duplicate on your system

Problem #1: When a USB sound device is unplugged and replugged, mixer_applet2 begins using nearly 100% of the CPU according to top.

Problem #2: The volume control slider on mixer_applet2 behaves erratically, jumping around wildly when moved and randomly muting and un-muting.

Related Problem #2.1: The slider position and mute status of mixer_applet2 do not directly affect the sound volume.  (However, moving the slider triggers the problem described in 3.1.)

Problem #3: The volume control sliders in gnome-volume-control behave erratically.  The left and right channels behave differently.  The right channel operates normally, but the left channel jumps around wildly when moved, with a tendency to drop to zero.  This causes the "link" icon to be unchecked.

Related Problem #3.1: When the volume control is adjusted via hardware (keyboard and/or buttons on USB headset) or via mixer_applet2, the left volume channel behaves as described in 3.  This occurs regardless of whether gnome-volume-control is open.

Related Problem #3.2: Adjusting the volume via alsamixer does NOT cause the erratic behavior described in 3 UNLESS gnome-volume-control is also open when alsamixer is receiving input.

Thanks.

---

