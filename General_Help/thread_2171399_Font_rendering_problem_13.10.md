---
title: "Font rendering problem? 13.10"
date: 2013-08-30
forum: General Help
---

### Post by s-cradock on 2013-08-30
Over the last few weeks, using Saucy updated daily, I have noticed a sprinking of font glitches in displayed text - single letters in a word seem to be rendered incorrectly. A forced re-draw of the page (in Firefox, for instance) usually cures the problem. It happens very rarely, on the order of one character on a page, and only sporadically. It also happens in LibreOffice, so it's not just a Firefox problem.

Has anyone else noticed this? I've become sensitised to it, so I notice it several times a day; it would be easy to miss or to dismiss as a bad spot on the screen.

Any ideas as to what might cause this? What package could I report a bug against? It's not just one program, so must be a lower-level process responsible for passing font info to the display.

I do have mir enabled (from the repo, not a ppa). Could it be a mir fault?

---

### Post by startas on 2013-08-30
Well, i noticed some fonts bugs too - in chrome newest version, in some pages, some "e" letters of only one and the same size looks like "o".

---

### Post by s-cradock on 2013-08-30
Replying to my own question - no, it doesn't seem to be a mir problem - I removed the mir programs and the font glitch is still present.

---

### Post by s-cradock on 2013-09-02
Well, not a lot of responses! 

Here is a snapshot of a typical glitch - the "t" of "the" in the second line.

Not a spectacular problem, but something is incorrect.

As I said, a forced screen redraw clears it, but there are always more, wherever I look hard enough...[ATTACH=CONFIG]245932[/ATTACH]

---

### Post by javanthropus on 2013-11-19
> **s-cradock said:**
> Well, not a lot of responses! 

Here is a snapshot of a typical glitch - the "t" of "the" in the second line.

Not a spectacular problem, but something is incorrect.

As I said, a forced screen redraw clears it, but there are always more, wherever I look hard enough...[ATTACH=CONFIG]245932[/ATTACH]

I'm seeing the same thing across various applications after upgrading to 13.10 a couple days ago.  I didn't have this problem at all before on 13.04.

If I had to guess, I would say this looks like a video driver issue.  I have an old Intel chipset in my laptop, Mobile Intel® GM45 Express.  However, I also use gnome-shell rather than unity, and I guess it's also possible that the compositor is involved.  Does any of this sound similar to your situation?

---

### Post by cariboo on 2013-11-20
Moved to General Help, as this has nothing to do with Trusty.

---

### Post by ken-west on 2013-11-22
Yes, I'm having this as well. Annoying!

---

### Post by rUff3r on 2013-12-16
I have this too. I also have a Laptop with Intel GMA 4500HD Integrated Graphics. I tried a LiveCD with Manjaro Linux, the bug seems to be there also.

So I googled a little: It seems to be a bug in the Intel Accel Mode SNA.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1098334](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1098334)

I changed it to UXA. So the problem is gone. At the price of performance I guess.

---

