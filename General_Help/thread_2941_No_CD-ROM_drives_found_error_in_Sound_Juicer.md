---
title: "No CD-ROM drives found error in Sound Juicer"
date: 2004-11-02
forum: General Help
---

### Post by lennychen on 2004-11-02
Hi All,

First off...I just want to say, I really like ubuntu...it's clean, fast, and stable.  I'm excited to start using it.

I have a question about Sound Juicer.  I'm not able to rip a new audio CD that I just bought.   I get a "No CD-ROM drives found" error once I open Sound Juicer.  I have a USB2 external DVD/CDRW drive that came with my HP laptop.  The drive reads other data CDs without problem.

However, the audio CD plays automatically when I pop the disc in.  The odd thing is that if I stop the playback and close the CD player program, then reopen it, I can't play the CD and it gives me a "Drive Error" message.

Any help you can provide would be greatly appreciated!

---

### Post by lennychen on 2004-11-02
TheMuso on irc was able to help me...the problem is that Sound Juicer needs SCSI generic support in order to work with my USB drive (which is used as a SCSI Drive).

To get it to work, enter "sudo modprobe sg" at the shell.

To make it a permanent fix, edit the "/etc/modules" file using sudo and add a new line  "sg".

Thanks to TheMuso for the fix.

---

