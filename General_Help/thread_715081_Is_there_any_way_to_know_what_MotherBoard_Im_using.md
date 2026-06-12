---
title: "Is there any way to know what MotherBoard Im using..."
date: 2008-03-04
forum: General Help
---

### Post by Fixman on 2008-03-04
without having to look manuals nor opening the computer? (I ask if theres a command or something).

---

### Post by ellgor on 2008-03-04
Hi,

Not a command as such but this, when you power up your comp at the very first hint of a screen press the PAUSE / BREAK key to stop the screen, a load of info should be displayed and usually at the very bottom will be the mobo manufacturer and the serial no. of the board, if its not on this screen repeat this procedure till you find a screen with what your looking for, hope this helps.

Regards, Ellgor.

---

### Post by Fixman on 2008-03-04
> **ellgor said:**
> Hi,

Not a command as such but this, when you power up your comp at the very first hint of a screen press the PAUSE / BREAK key to stop the screen, a load of info should be displayed and usually at the very bottom will be the mobo manufacturer and the serial no. of the board, if its not on this screen repeat this procedure till you find a screen with what your looking for, hope this helps.

Regards, Ellgor.

Thanks a lot.

---

### Post by Whiffle on 2008-03-04
Try this one:

```

sudo dmidecode -q | less

```

Hit q to exit.

---

