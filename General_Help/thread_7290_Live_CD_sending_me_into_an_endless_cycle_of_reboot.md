---
title: "Live CD sending me into an endless cycle of reboots"
date: 2004-12-05
forum: General Help
---

### Post by Marble2 on 2004-12-05
Well, I just received my CDs, I pop the live CD in, boot to it, it loads, and when it finishes loading it reboots, then loads, does the same thing. Any ideas?

---

### Post by pablito on 2004-12-05
Hi,

I finished downloading the ISO this morning (3+ hours... ouch! :)) and am seing the same behaviour. The pretty Ubuntu splash screen is shown during boot-up and the progress bar makes it to the end, a pause and then the system reboots. 

Because of the Ubuntu splash screen, the boot sequence is hidden so there was no obvious way to see the cause of the problem. I tried Alt+Fn in case virtual terminals were enabled with more info, but no luck. Any way to disable the boot-up splash screen on the fly?

That being said, it smelled a bit of an X problem.  I think when it got the end, it was probably trying to lauch X and had a problem with the default resolution or something. I suspected this based on a previous experience... quite a while back... Hmmm... come to think of it, might have been with a Morphix Live CD.

I mention Morphix as in a 3rd attempt, I chose to boot in "safe mode" from the boot menu. This doesn't show the splash screen so as it boots, I noticed the Morphix welcome or starting message (forget which). In safe mode, the system started fine for the most part. Main problem is that networking was not available. Ran ifconfig and sure enough, no interface for my NIC. Guessing networking is disabled in safe mode?!

Anyway, it was good enough to play with and explore a bit, but without networking... well a bit less than ideal. Any advice welcome! :)

Cheers,
Paul

---

### Post by deception on 2004-12-05
During the splash screen press F2 for more info.

---

### Post by BWF89 on 2004-12-05
And they wonder why more people aren't useing Linux...

---

### Post by pablito on 2005-01-01
Hi,

Sorry for the slow update, but I've been meaning to provide the solution to my problem for a while now.

With a bit more time to spare for debugging this time, F2 did away with the splash screen as suggested. I was able to confirm my theory about the X problem. On the next reboot attempt I then scrolled through the boot options looking for X related items. When I tried with "xmodule=vesa", that did it. So in short, I used the default menu item in the boot loader screen (first at top), but manually added xmodule=vesa and then enter. The system booted with everything working properly. I'm writting this from Ubuntu live.

Just out of curiosity, what does the vesa module do?

Actually, I do have another small problem with USB/PS2, but a new thread might be more appropriate for that.

Cheers,
Paul

---

### Post by eco2geek on 2005-01-02
[quote="BWF89"]And they wonder why more people aren't useing Linux...[/quote]
Where, exactly, can I download an open-source live Windows CD? Think about it.

[quote="pablito"]Just out of curiosity, what does the vesa module do?[/quote]
It's a video driver that ought to work with just about any combination of video card and monitor, that has fewer capabilities than video drivers that are vendor-specific.

The "live CD" part of the Ubuntu live CD is based on [Morphix](http://www.morphix.org), and you can see more [boot options here](http://www.alextreme.org/phpwiki/index.php/MorphixBootOptions).

---

