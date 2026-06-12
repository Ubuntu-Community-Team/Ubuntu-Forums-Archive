---
title: "[SOLVED] Printer low on ink message wrong - can I reset?"
date: 2007-10-30
forum: General Help
---

### Post by keyboardashtray on 2007-10-30
I just set up my old HP Deksjet 3845, had the cartridges refilled at Walgreens. 

The notification tool as well as HPLIP toolbox are telling me I'm low on ink, when that isn't the case.

Is there a way to force a recheck, or reset it?

Barring that, can I just get rid of the nag screen?

---

### Post by potam on 2007-11-02
Yes, you can reset it. The ink level is determined by the printer. And there is a serial number in the ink cartridge, so if you put the refilled cartridge back to the printer, it sees that it is the same (empty) cartridge. You have to do some hardware trick with the cartridge to reset the printer's serial number cache (which holds only the last inserted cartridge number). The tutorial is here: [http://www.inktec-uk.co.uk/57_58_reset.htm]("http://www.inktec-uk.co.uk/57_58_reset.htm")

---

### Post by keyboardashtray on 2007-11-02
> **potam said:**
> Yes, you can reset it. The ink level is determined by the printer. And there is a serial number in the ink cartridge, so if you put the refilled cartridge back to the printer, it sees that it is the same (empty) cartridge. You have to do some hardware trick with the cartridge to reset the printer's serial number cache (which holds only the last inserted cartridge number). The tutorial is here: [http://www.inktec-uk.co.uk/57_58_reset.htm]("http://www.inktec-uk.co.uk/57_58_reset.htm")

Many thanks Potam! I appreciate the help - that did the trick :)

Excellent - I'm easily bothered by incorrect nag screens. 

Just for anyone else that may give it a try, your results may vary, but for me, there weren't any error messages/test pages. So at first I didn't think it was working. I was watching the "status" tab in HPLIP - when I finally flipped over to the "supplies" tab, I realized it had worked for the black cartridge, and when I hit refresh devices, then the color updated as well. Unfortunately, I had tried a few of the methods by this point, so I'm not sure exactly which one did the trick - I started with the power down x6 method (seemed the cleanest) then I went with the first method, then the combo tape/power down method. Heh. I'm guessing your best bet would just be to start with method one, probably the tried and true.

Thanks again Potam.

---

### Post by scottie_z on 2008-06-18
I think I'm having a similar problem with the Deskjet D4260 -- even though I've filled the color reservoirs to overflowing, no colors come out.

The "dot" layout on the back of the cartridge is different for the 74/75 cartridges than it is for the 56/57 cartridges specified in the linked page.  

Has anyone successfully refilled cartridges for use in the Deskjet D4260?

---

