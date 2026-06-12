---
title: "2 random Ubuntu problems"
date: 2008-03-17
forum: General Help
---

### Post by vitaliyn on 2008-03-17
I first installed Ubuntu 7.10 Gutsy Gibbon about a month after it came out.  Everything worked great.  Amarok got the right codecs to play shoutcast streams, and I could change the visual affects in the Appearance.  Then I dropped Ubuntu for about 3-4 monthes.  Now Amarok gives me an error message when i try to play shoutcast.  Also when I try to change the visual affects it gives me a message like this: The Composite extension is not available.

Whats gone wrong with Amarok and Ubuntu since the last time I used it?
Someone please help because this is driving me crazy.

---

### Post by jken146 on 2008-03-17
> **vitaliyn said:**
> Now Amarok gives me an error message when i try to play shoutcast.
What's the error message?

---

### Post by vitaliyn on 2008-03-17
Actually I just found the answer to my first question abtou Aamarok.  I had to do was: "sudo apt-get install libxine1-ffmpeg"  

The Error message is:  "The Composite extension is not available."

---

### Post by myfigurefemale on 2008-03-30
bump

---

### Post by rainwalker on 2008-03-31
Search the forums for that error your getting, I've seen it before quite a few times but I've never experienced it so I can't give an actual solution.

---

### Post by myfigurefemale on 2008-04-01
I did search the forums - this was the only post I could find...

---

### Post by myfigurefemale on 2008-04-23
i've been trying to get compiz working for weeks on ubuntu and have had to re-install a few times due to the huge mess i made.  everything i did created problems such as:
a blank boot up screen (after installing the proprietary driver)
logging in, going to the desktop for 1 second and back to the login screen...repeatedly until i re-installed ubuntu (after using the open-source driver)
"the composite extension is not available"
"advanced desktop effects could not be available"
ect, ect.
after i installed hardy (i wiped the hardrive) i installed the [envy]("http://www.albertomilone.com/nvidia_scripts1.html") package it installed the correct ati driver for my machine.  compiz is enabled by default in hardy, so all i had to do was install the compiz-manager (in the repositories) and PRESTO!  everything finally worked.  so to anyone else who has these problems, try this...it might help!

---

