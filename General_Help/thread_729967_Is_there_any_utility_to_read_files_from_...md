---
title: "Is there any utility to read files from .."
date: 2008-03-20
forum: General Help
---

### Post by mvashi on 2008-03-20
Is there any utility to read and transfer files from a drive which has ubuntu installed but does not load 

Well to make matters clear as to why I am in search of such kind of uitlity is that 
On 
HDD 1 -- Has Windows XP installed ( dont care too much about it ) 
HDD 2 has Ubuntu installed 

Somehow I managed to screw up my bootloader and I could not boot to XP 
so 
used fixmbr to see if it would resolve the issue 
did not 
then I used live cd to and 

sudo grub 
find \boot\root\stage1 

hd1,0 

then I did 
 root (hd1,0) 
setup (hd1) 
quit 

sudo reboot 

then restarted the pc and message is NTLDR not found 
Reinstalled the XP 
used live cd to do that grub thing again 

restarted the pc and it straightway boots to XP 
cannot even get the menu asking for the OS to boot to
I will have to reinstall Ubuntu but before that I wish to extract some irreplacable pictures 

I hope some one can help me with that

---

### Post by ohzopants on 2008-03-20
I would try booting from the LiveCD again. Once that loads try and mount the ubuntu partition.  

If you can successfully mount the partition you will have full access to the files, you can then copy them to a usb drive or even burn a cd.

---

### Post by nick_h on 2008-03-20
> restarted the pc and it straightway boots to XP
cannot even get the menu asking for the OS to boot to
Try reinstalling grub with:
```
setup (hd0)
```

---

