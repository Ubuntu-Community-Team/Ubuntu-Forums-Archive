---
title: "Aspell and LyX problem"
date: 2008-05-22
forum: General Help
---

### Post by rousselm on 2008-05-22
Hi,

I've just installer LyX and I'm trying to use aspell with it. I've downloaded and installed aspell via synaptic plus the dictionary I want. 
When I try to start aspell from LyX, the dialog window just pop up but close straight after (I don't have time to see anything) and then I get a tiny window telling me "one word has been checked" (I have put voluntary one misspelled word in my document). 
When I try to use aspell from the terminal with the command lines, it works fine in the terminal. Also, although I installed aspell, I can't seem to find how to start aspell GNU (outside of LyX).
Can you help me or tell me what I'm doing wrong?
Thanks in advance!

Marie

---

### Post by finemann on 2010-12-18
The post is a bit old, but I am replying because others might find it helpful. This is a reported bug of LyX, and it is yet to be fixed (version 1.6.7 has the same bug. See [https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/400577]("https://bugs.launchpad.net/ubuntu/+source/lyx/+bug/400577")). There seems to be a workaround though. The catch is to place the cursor at some place other than the end of the document before initiating the spell-check. Further, make some deliberate mistake in the document, so that at least one word is wrong. It seems to work fine that way.

---

