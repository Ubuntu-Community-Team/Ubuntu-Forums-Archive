---
title: "[SOLVED] Open Office"
date: 2007-12-05
forum: General Help
---

### Post by cartisdm on 2007-12-05
Curious.  I'm relatively new to using Open Office (fairly new to Linux as well so bare with me).  I've been using my word processor to write some papers here and there so I can get the hang of it and (hopefully) soon make the 100% Linux/XP switch, problem is how come a full one page paper written in Open Office then saved, sent to be opened in MS Word isn't a full page anymore?  It's like 80% of the length it should be.  I looked at my page settings and they're all set to 8.5'' X 11'' etc and I'm using the TIMES font.  What am I missing?

Dan

---

### Post by skyjacker on 2007-12-05
> **cartisdm said:**
> Curious.  I'm relatively new to using Open Office (fairly new to Linux as well so bare with me).  I've been using my word processor to write some papers here and there so I can get the hang of it and (hopefully) soon make the 100% Linux/XP switch, problem is how come a full one page paper written in Open Office then saved, sent to be opened in MS Word isn't a full page anymore?  It's like 80% of the length it should be.  I looked at my page settings and they're all set to 8.5'' X 11'' etc and I'm using the TIMES font.  What am I missing?

Dan I quit using OO, but have you compared the top and bottom of the page space on both programs.  Not sure they default to the same values...

---

### Post by oeolycus on 2007-12-05
I've had this happen too. Sometimes it's longer though. I usually make the edits after I've opened it in Word and save that file on the XP workstation as well. Unless you're printing with OOo, I'm not sure if there's a way to prevent this. It may never be a 1:1 conversion rate between the two programs.

Is it possible that wherever you're printing might install OOo? That would fix the problem.

---

### Post by Tyche on 2007-12-05
One other thing you might look into is using the same font in OpenOffice.org that will be used on the Windows machine.  Microsoft core fonts are available in the repos, and OpenOffice.org will use them when they're installed through Synaptic.

The problem is that if a word processing program doesn't have the font available, it will substitute another one.  The substitution is seldom the same size (horizontally or vertically) as the one that was specified, thereby changing the physical spacing of your text.  This can result in more or less pages than you expected.

I hope this helps.

---

### Post by cartisdm on 2007-12-05
Thanks guys, quick responses:)  I'll check into those in the morning when I'm not caffeine drained

---

### Post by cartisdm on 2007-12-08
Ok for future reference for anyone else I solved the problem by adding MS fonts.  I was using TIMES which came with open office but now I'm using Times New Roman which is, far as I can tell, a direct match in size and spacing when you open with MS Word.

Here's the link to a simple installation of the fonts

[http://penguinfonts.com/howto/ubuntu.php]("http://penguinfonts.com/howto/ubuntu.php")

enjoy:)

---

