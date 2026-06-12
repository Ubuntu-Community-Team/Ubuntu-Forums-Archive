---
title: "Ubuntu Won't Consistently Start Up Without Super GRUB CD"
date: 2007-07-02
forum: General Help
---

### Post by apolloxi on 2007-07-02
My Ubuntu 7.04 system does not always start up. Whenever I select Ubuntu to boot, it will eventually end up on a completely black, blank screen, and NOTHING will happen. The "busy light" on my computer will not blink once, but, for some reason, the "busy light" on my floppy disk drive (yeah, my desktop is that old) will freeze and stay on, although I don't know what it could possibly be doing.

So, I usually have to put in a Super GRUB Live CD to "jump start" Ubuntu. This gets tiresome, though. So, I was wondering if there was some permanent solution to this?

If it's the drive, then how do I disable it? (I want to disable it, anyway, since the eject button is broken, and since floppy disks are obsolete anyway. I went to BIOS and disabled "Removable Device - Legacy Floppy" but it still tried to boot, anyway.)

---

### Post by dfreer on 2007-07-02
Did you try changing the boot order in BIOS as well, so it checks the hard drive first before anything else?

---

### Post by apolloxi on 2007-07-02
Yeah. I put the hard drive before everything else ("IDE Hard Disk" or some such thing) but it still froze on that black screen.

Also, if it helps, I always repair/reinstall GRUB on the MBR using the Super GRUB CD before I boot Ubuntu, thinking this will solve the problem, but it never works. Still the black screen always.

---

### Post by apolloxi on 2007-07-04
Can anyone help, please?

---

### Post by apolloxi on 2007-07-04
......Anyone?

---

### Post by dfreer on 2007-07-04
Could be a corrupted install, you might want to try a reinstall if you can't find the answer.
EDIT: have you tried reinstalling GRUB to the MBR using a live CD? I don't think it would be any different from the GRUB Super CD...

Also, some BIOS have a Virus Prevention "Feature" that supposedly prevents anything from overwriting the MBR. Is your black screen occur after GRUB loads, and you select the appropriate ubuntu kernel to load, or does GRUB not even pop up?

---

### Post by smoker on 2007-07-04
i think your floppy drive is faulty, sounds like ubuntu is asking for details during boot, and waiting for a response that never comes back!

try opening the case and disconnecting the power and cable from your floppy drive, and see if it procedes to boot then,

best of luck

ps - take precautions, turn off pc, earth yourself when touching anything inside case, etc.

---

### Post by apolloxi on 2007-07-05
> Also, some BIOS have a Virus Prevention "Feature" that supposedly prevents anything from overwriting the MBR. Is your black screen occur after GRUB loads, and you select the appropriate ubuntu kernel to load, or does GRUB not even pop up?

It's always after GRUB loads, after I select for Ubuntu to boot.

>  	i think your floppy drive is faulty, sounds like ubuntu is asking for details during boot, and waiting for a response that never comes back!


Well, after seeing it happen several other times, the floppy drive light isn't ALWAYS on when the computer freezes. So, I don't know. But, I'll consider trying this.

Thanks for the suggestions, you two.   ^_^

---

