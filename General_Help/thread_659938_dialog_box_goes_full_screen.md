---
title: "dialog box goes full screen"
date: 2008-01-06
forum: General Help
---

### Post by Footer on 2008-01-06
I'm not sure when this started happening (currently running Kubuntu 7.10), I think maybe with Feisty but nonetheless, when I go to 'Export as PDF' in OpenOffice, the resulting export dialog box goes full screen rather than being in a normal windowed box.  It seems to me this has occurred with other dialog boxes as well but 'Export as PDF' is the only one I can currently reproduce (I'm exporting a .png file as PDF).

Can anyone else confirm this behavior?  I'd like to know if it's my system or a bug.

Thanks!

---

### Post by adam.tropics on 2008-01-06
No, tried it here, all normal.

edit:re-read post: but I am on Gnome, so not much help I'm afraid.

Did you upgrade from Feisty, or fresh install Gutsy? And do you have more than one user setup, wondering if it is system wide, or just local to you.

---

### Post by ajgreeny on 2008-01-06
Doesn't happen on mine when I export a letter (rtf in this case) as pdf, so either it is your set-up or you have a different version of something to me.  I am also on gnome not kde, so I suppose that may be the difference.

---

### Post by Kralizec on 2008-01-06
I get the same problem with exporting, and I'm using GNOME. Also, I get it randomly if I try to close without saving.
For anyone not sure what I/we am/are talking about, here are some screenshots.

---

### Post by Footer on 2008-01-06
Cool!  Thanks for the replies!  So I'm not imagining it!  Excellent on the screenshots.  That's definitely the problem.  So is this a bug...?

Thanks!

---

### Post by Kralizec on 2008-01-06
I have no idea what it is. I'm wondering if its something to do with my gtk/metacity setup, so I'll check that out and post again. If not, then I don't know. I've had quite a few problems with open office in the past though.

---

### Post by Kralizec on 2008-01-06
I figured out the cause and it does indeed have to do with your appearance settings. When I disabled advanced desktop settings completely (no compiz at all), the problem went away.

---

### Post by Footer on 2008-01-08
Hmmm, you're right!  I disabled compiz, and the export dialog box is now a normal window vs. full screen.  Went back to compiz and export dialog box is back to full screen again.

So again, I wonder, if this a 'bug' or is it considered normal behavior under compiz?  Hard to believe it's normal since this is one of the few dialog boxes that do it!

Thanks!

---

### Post by Kralizec on 2008-01-08
As far as I've experienced, this problem doesn't occur with anything other than OpenOffice, which makes me think their developers should be notified.
Does with compiz *not* experience this problem? If so, I'm curious about your system specs, Footer, so we can find out the similarities between us.

---

### Post by Footer on 2008-01-12
If I turn compiz off and just use Kwin as my window manager, this problem does not occur.  Only when I have compiz enabled does the dialog go full screen.  I have been able to make one other dialog (besides the export to pdf one) go full screen as well and it was also an OpenOffice one.  I believe it was searching a spreadsheet with F3.

Anway, yes, it appears to only be an OpenOffice issue and only when Compiz-fusion is enabled.  Sounds like a bug to me!

:)

---

### Post by d2theg on 2008-02-13
I had the same problem, fixed it by going into compiz config, (advanced desktop settings),  go to the Workarounds section under Utility, and de-select legacy fullscreen support. Good Luck!

---

### Post by Kralizec on 2008-02-13
Thank you, your solution seemed to have fixed my problem as well.

---

### Post by prince_niceguy on 2008-02-26
> **d2theg said:**
> I had the same problem, fixed it by going into compiz config, (advanced desktop settings),  go to the Workarounds section under Utility, and de-select legacy fullscreen support. Good Luck!

yup that fixed it.. thank you.

---

