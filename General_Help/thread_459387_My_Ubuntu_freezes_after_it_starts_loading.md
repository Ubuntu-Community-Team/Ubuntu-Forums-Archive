---
title: "My Ubuntu freezes after it starts loading"
date: 2007-05-30
forum: General Help
---

### Post by danbrinton on 2007-05-30
When Ubuntu starts to initialize, it freezes. The screen says Ubuntu at the top, and the bar shows it's about 3% finished. At the bottom it says: 
   Loading essential drivers                                  OK
   Mounting root file system                                 OK

And it just sits there and goes no further, with no error messages etc. It does this every time. It used to work fine, although it recently had a problem requiring me to run FSDK I think it was, and then it worked twice, then this happened.

Any suggestions??

Thank you very much.

---

### Post by jimbob on 2007-05-30
Edit your /boot/grub/menu.lst and remove the quiet and spalsh switches and reboot.

Perhaps we can see exactly where it is hanging up trying to do.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by danbrinton on 2007-05-30
Sorry to be such a novice, but I don't know how to do that, especially as it never loads to a working prompt or screen. (But I wouldn't know how to do it at a prompt either.)

_Thank you_- Dan

---

### Post by jimbob on 2007-05-31
OK, try this.  When your boot menu comes up does it show a selection that says recovery mode?

Use the down arrow and select this mode and hit enter.  I believe this will show each step in the boot process and you will see where it hangs.

What version number of Ubuntu are you running?  What is FSDK?  Do you mean fsck?

Do you have any other operating system(s) and/or disks on your computer?  Do they work OK?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

