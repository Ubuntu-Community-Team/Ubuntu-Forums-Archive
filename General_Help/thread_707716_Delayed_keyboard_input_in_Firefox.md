---
title: "Delayed keyboard input in Firefox"
date: 2008-02-25
forum: General Help
---

### Post by johannix on 2008-02-25
Ever since I setup the ATI 8.2 driver typing in firefox has a delay associated with it. My input seems to be going into a queue and shows up about a half second after I type. In other programs such as Emacs or GEdit I don't have any issues.

---

### Post by Sam Lars on 2008-02-25
Is the system taking a lot of CPU during the delay?

---

### Post by johannix on 2008-02-29
Yes, whenever I start typing within Firefox the process usage sky rockets. In other programs it doesn't.

---

### Post by Sam Lars on 2008-02-29
So this is typing anywhere, not just certain boxes?
Try running Firefox from the command line with MOZ_DISABLE_PANGO=1

---

### Post by johannix on 2008-02-29
A little bit faster, but still definitely delayed. For example typing this up right now I typed the entire word "delayed" before it showed up on the screen.

---

### Post by Sam Lars on 2008-02-29
If you switch drivers for your video, does it fix it?
Can you try Firefox 3 and see if it's the same?

---

### Post by johannix on 2008-03-01
First, I'd like to say thanks for all the input!!

Of the two suggestions you gave I know that my system was fine with a different video setup, but am very weary to mess with my current setup, since my video card hasn't really been behaving and I finally got the newest drivers working with it...

So, I tried your second suggestion of testing out firefox 3 and the lag totally went away!!

How'd you figure this would help?

Thanks so much,
Michael.

---

### Post by Sam Lars on 2008-03-01
Well I couldn't rule out the bug being in Firefox, so I wanted to know if the problem was the same in FF3.  I think it's using a different rendering engine (Cairo rather than Pango?), but I'm not sure.

---

### Post by johannix on 2008-03-02
True. Well good catch anyways...

I'm considering making the move from ATI to nVidia so that I don't have to worry about driver issues anymore...

Thanks for the help.

---

