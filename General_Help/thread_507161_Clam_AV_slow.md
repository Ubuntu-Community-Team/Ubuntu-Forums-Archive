---
title: "Clam AV slow"
date: 2007-07-22
forum: General Help
---

### Post by cjlindem on 2007-07-22
I'm trying to get clamav with Clamtk gui up and running.  It seems to work, but when I scan, even if it's just a single small text file, processor usage on the clamscan process goes to 100% and stays that way for about 5 minutes.  The GUI goes unresponsive for the duration.  I also scanned using just the commandline and had the same results.

Isn't clamTK supposed to give me some sort of realtime scanning results or progress bar?  If clamscan locks the processor up for the duration of the scan what point is the interface at all?

I have tried uninstalling and reinstalling clamav several times, and tried different versions of Clamtk, none make any difference.  My computer is 2.6ghz 1gb ram, and everything else runs great.  Please tell me this isn't the normal function of AV on linux, or I have found the first area where the OS is -extremely- lacking.

Thanks for any help.

---

### Post by Tzimisces on 2007-08-25
The problem lies in the fact that ClamAV first has to load its virus database, which takes a lot of time (imagine :). 
The solution lies in using ClamAV as a daemon ("service"). 
Nevertheless, due to the fact that clients like ClamTk do not support that modus operandus, you'll have to run "clamdscan" by hand (note the "d", there is also an "clamscan", without the "d', running in standalone mode).
That's not as complicated as it sounds, though :) Check the man-pages for info..

Regards,

  Bob

---

