---
title: "Ubuntu livecd and initramfs"
date: 2008-04-14
forum: General Help
---

### Post by davavanstone on 2008-04-14
Heya people, complete and utter linux noob here so bear with me.

After recently buying a new vaio with vista after about half an hour i got sick to death of it. xp was troublesome but this takes the piss lol

After talking to a mate and doing some research i decided to move to ubuntu.

I downloaded gutsy burned it to cd. Ran it live on the vaio to see what i thought and loved it think its time for a complete move to linux. Didnt wonna install to this laptop cos i dont know the warranty of it etc.

I have another laptop here that had xp and then ran backtrack briefly, it has an external cd drive but that hasnt given any problems with xp backtrack or any other booting cds. so thought i'd give it the wipe and sort the partitions out etc.

I insert the 7.10 livecd select the run or install and get  

```

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [       39292000] usb 4-4: device not accepting address 3, error -110

[     48.828000] usb 4-4: device not accepting address 4, error -110
[     59.364000] usb 4-4: device not accepting address 5, error -110


```

now i press enter and get

```

(initramfs)

```

What now? it seems whatever i type i get    /bin/sh: <COMMAND>: not found

Any ideas? Have research alot on google and cant seem to get any where.
Any help would be brilliant
Thanx

---

### Post by davavanstone on 2008-04-14
anyone lol :)

---

### Post by pointone on 2008-04-14
Try running the "Check CD for defects" option from the boot menu. While it may have worked fine on the Vaio, not all drives are compatible with all CDs. If errors are detected, try burning again at the lowest speed, and make sure you're using CDs that are known to work with your external CD drive.

---

