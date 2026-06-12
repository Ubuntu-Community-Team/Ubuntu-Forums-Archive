---
title: "Can't boot into safe/recovery mode"
date: 2018-02-14
forum: General Help
---

### Post by cfree5119 on 2018-02-14
I installed Nvidia drivers and then subsequently blacklisted the nouveau drivers as the Nvidia drivers were not be recognized. Now upon boot, it boots to a black screen. I cannot boot to recovery mode using the shift key or esc key after the bios screen. That said, I can access the terminal (even though I can't see it). Can I reboot with a certain command line into recovery mode automatically? How can I get my screen back up?

Also, did I properly install the nvidia drivers or should I blacklist nouveau, purge nvidia, then reinstall nvidia?

---

### Post by jschissel on 2018-02-14
I'm sure this wouldn't apply but just on the off-chance, ensure you are using the correct driver.  The nvidias have different numbers appended to them and it can be confusing.  It's not necessarily like other version numbering systems where larger means newer or better.  I think it's more about this chip needs this number.  We had a laptop that was fine, the user somehow found the third party drivers tab, and thought the nvidia package with a larger number was better.

---

### Post by jschissel on 2018-02-14
oh, sorry, and to answer your question, maybe using a bootable live USB image would allow you to chroot into the installed system.  I'm sorry, I really should leave this to the pros because I don't even know how to do that without researching it again.  (knows only enough to be dangerous)

---

### Post by cfree5119 on 2018-02-15
Ya I am a complete noob to this stuff. Just trying to get back in to see the screen so I can fix. I did nvidia 390

---

