---
title: "Resetting printer cartirdge status on HP PSC1310"
date: 2007-11-02
forum: General Help
---

### Post by toupeiro on 2007-11-02
I have one of those all-in-one HP printers (sans the fax) that was reporting low on ink.  I've since replaced both cartridges and the status messages continue to pop up.  Is there something else in CUPS I need to do to clear that error?  Obviously its not stopping me from printing, but I like my error messages to be truthful. :)

---

### Post by Insightfill on 2007-11-02
The problem is actually in the printer - it keeps track of the cartridge serial number and will remember that it had run out.  Depending on your actual model, the trick to "fooling" the printer varies slightly.

Some printer models will remember the last two or three cartridges, and if you have enough other dead ones on hand, you can keep dropping them in.

The method I used was specific to my cartridge type (HP 56 and 57 for a HPDJ 5550) and can be found here:

[http://www.inktec-uk.co.uk/57_58_reset.htm](http://www.inktec-uk.co.uk/57_58_reset.htm)

It involved covering the various pins with tape and putting back in the printer several times; they also had a few alternative tricks.  According to a quick search, it seems you use the same model cartridges - give it a whirl.

---

### Post by toupeiro on 2007-11-03
technology wasted on ink! :)

Thanks for the information.  I'll give it a shot and see how this works with the PSC series.

---

