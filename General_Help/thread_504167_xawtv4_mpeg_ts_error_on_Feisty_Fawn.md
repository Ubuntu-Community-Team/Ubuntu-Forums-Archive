---
title: "xawtv4 mpeg ts error on Feisty Fawn"
date: 2007-07-18
forum: General Help
---

### Post by Xawtv4user on 2007-07-18
ivtv is properly installed and tested to be working.
I have successfully compiled xawtv4 from cvs.
I have installed all possible mpeg libraries and development packages.
I can see during compile time that it is not finding mpeg ts things it needs to work.
It used to work under Edgy.
Below is the error that I get when running xawtv4.
Copying the known working xawtv4 from the old machine using Edgy results in the same error.


mpeg ts: no pids given and no PAT found
can't open: /dev/video0

Is there some way to see this fixed or does anyone have a new .deb of it that is known to work on 7.04? An old posted .deb results in the same error.

---

### Post by tjapko on 2007-09-05
I have exactly the same problem and hope someone will help us here.

The TV stations found previously are still available and scantv produces the same list in the sense that it keeps the old values. So scantv picks it up correctly.

Back to Windows

tjapko

---

### Post by Xawtv4user on 2008-04-13
Well, a lot of time has passed and still there is no xawtv4 application for Ubuntu nor was the post for help answered.
Recently, I converted an xawtv4 rpm via alien and it, as well, gave the very same error as above. I can use mplayer and ivtv to watch my PVR-150. I'd like to use xawtv4. I certainly would not like to use mythtv.
Compiling from source with all the new libraries in Ubuntu gives more errors than ever before when attempting it.
Could someone please post some help or just make a deb for xawtv4 that works on modern Ubuntu systems? Is there no xawtv maintainer? Seems version three is still the only one going around for Ubuntu.
What are any of the other Ubuntu and PVR-150 users using for a lightweight tv app?

---

### Post by saedelaere on 2008-04-23
Hi,

how about trying [this one]("http://ubuntuforums.org/showthread.php?t=763698")?

regards

---

