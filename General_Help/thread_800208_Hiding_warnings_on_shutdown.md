---
title: "Hiding warnings on shutdown"
date: 2008-05-19
forum: General Help
---

### Post by vancouverite on 2008-05-19
Hello,
Sicne upgrading to 8.04 I get warnings from network manager when I shut the computer down.  They don't seem to be a problem, but I would prefer not to see them.  

Is there a way to silence the warnings and just see the normal shutdown screen?

Cheers,
Vancouverite

---

### Post by opendevlite on 2008-05-20
i have the same problem too.

---

### Post by opendevlite on 2008-05-20
> **vancouverite said:**
> Hello,
Sicne upgrading to 8.04 I get warnings from network manager when I shut the computer down.  They don't seem to be a problem, but I would prefer not to see them.  

Is there a way to silence the warnings and just see the normal shutdown screen?

Cheers,
Vancouverite

This solve the problem
==================================================================
From noynac

I was able to rid my computer of the error messages on reboot/shutdown and thought I would explain what I did. I made two changes and don't know which was the fix (if either), so I'll mention both.

My computer has two ethernet ports--one is built into the motherboard and the other is on a card. The first is attached to the internet (Roadrunner); the other is unused. I went to the Network app and unchecked roaming for the unused port and changed the drop down list to automatic configuration.

The second change involved the Login Window tool. I clicked on the "Edit Commands" button. I then deleted the messages in quotes from the end of the halt and reboot commands.

I've shutdown and rebooted numerous times last evening and this morning, and no error messages for now. I hope it stays that way.

BTW, I get the impression that this problem has multiple causes, and what works for me may not work for others. Good luck everyone.
==================================================================

---

