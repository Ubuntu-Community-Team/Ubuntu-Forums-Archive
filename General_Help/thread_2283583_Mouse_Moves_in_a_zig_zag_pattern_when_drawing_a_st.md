---
title: "Mouse Moves in a zig zag pattern when drawing a straight line."
date: 2015-06-23
forum: General Help
---

### Post by ThoseTimesAreGone on 2015-06-23
hi,

The problem is exactly as the title says.

Video illustrating what i mean (and this is with me fighting to keep it even and move it across a straight line horizontally and vertically):

[https://vid.me/LgyY](https://vid.me/LgyY)

This problem persists in ubuntu, elementary OS, and linux mint. Obviously all distros based on ubuntu.

I am using a Steelseries sensei mouse. Acceleration is off. Problem is reproducible with another mouse but is visible to a lesser degree.

No wonder i dropped 3 ranks in CS GO since i started gaming on linux. Any idea what the hell the problem is?

Thanks as always for your insight people.

---

### Post by veddox on 2015-06-23
Hm, no idea what could be causing the problem, but perhaps we'll get to the bottom of it with a bit more information. So here are a few questions:

1. First of all, well done for trying with different distros. However, I noticed you didn't try it on Debian - the basis for Ubuntu. Could you try it out on that? And which versions of the mentioned distros did you use?

2.What desktop environments did the problem appear on? The video appears to show Pantheon (presumably on elementaryOS) - any others?

3. Have you in any way changed your graphic stack from the default setup? (Installed Wayland/Mir instead of X, changed the DE, etc.?)

4. If you say "Problem is reproducible with another mouse", what do you mean by "other mouse"? Another mouse of the same model, another mouse of the same company, or a completely different mouse?

5. Have you successfully used that particular mouse on Windows/Mac OS X before? Any problems there? (If yes, I would suspect hardware problems - contact the developer.)

6. Have you heard of anybody else experiencing similar problems with that mouse? (I presume you googled the problem first?)

---

### Post by ThoseTimesAreGone on 2015-06-30
1. I have not had a chance to run it on debian as I have never used that. Maybe it is something i can try in the future if time permits. I used mint 17.1, ubuntu 14.04, elementary os 0.3 .

2. Problem persists on default ubuntu install (unity), mint cinammon, and eOS pantheon.

3. I have not changed anything regarding the graphics stack.

4. Problem is reproducible but to a much lesser degree on a different type of mouse (logitech m525)

5. The mouse used to work fine in windows 7 (but then again i was using official steelseries drivers). 

6. I have been googling the problem but havent found anything at all.

Sorry for the late reply

---

### Post by veddox on 2015-07-02
Looks like a tough one... Here's some suggestions on what to do next:

First,  submit a bug report. At least to Ubuntu (via Launchpad), possibly also  to the GTK project (all the desktop environments you mention use GTK).  Second, try contacting Steelseries, if they can give you any  advice/help.

Sorry for not being able to help more, but this looks like something pretty deep :-(

---

