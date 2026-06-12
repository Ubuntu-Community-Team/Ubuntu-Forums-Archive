---
title: "Firefox printing, HP 4000, gtklp?"
date: 2005-06-13
forum: General Help
---

### Post by dudinatrix on 2005-06-13
Hello,

I've got my networked HP4000 printer set up (Windows network) and it test prints fine.  However, when I tried to print from Firefox, I got the following error printout instead:

[I]The Postscript interpreter in your printer is 2014.108
This printout requires at least version 2015 or greater
[/I]

I read that one workaround is to install gtklp using Synaptic.. however, I can't find it anywhere!  (Forgive me, I'm a day old noob.)  I tried searching for gtklp or xpp, and neither of them are found in Synaptic.  How do I get gtklp installed through there?

Any other advice you can offer to get my networked printer up and running completely would be apprecaited. :)  Thanks!

---

### Post by jamyskis on 2005-07-06
In Synaptic, click on Settings, then go to Repositories. Click on the Settings button in the window that opens, and check "Show Disabled Software Sources". It will ask you if you want to update your lists - click yes. GTKLP should be in there, although I've not had much success with the same problem, even if I can print out of just about every other program.

---

### Post by Ken.Lank on 2005-07-06
You can also go into the printer properties on the "Advanced" tab and change "GhostScript pre-filtering" to "Convert to PS level 2".  This is what I did to get my printer working.

---

### Post by robertoneto123 on 2005-09-27
Hey, I'm with the same problem.

I try to install the package, put the filter... but now the printer just says "Processing job" forever (the indicator is blinking for 10 minuts now).

The cups log is the following:

I [27/Sep/2005:15:41:27 -0300] Job 39 queued on 'LaserJet-4000' by 'roberto'.
I [27/Sep/2005:15:41:27 -0300] Started filter /usr/lib/cups/filter/pstops (PID 12863) for job 39.
I [27/Sep/2005:15:41:27 -0300] Started filter /usr/lib/cups/filter/foomatic-rip (PID 12864) for job 39.
I [27/Sep/2005:15:41:27 -0300] Started backend /usr/lib/cups/backend/parallel (PID 12865) for job 39.

Does anyone have any clue?

Thanks!

---

