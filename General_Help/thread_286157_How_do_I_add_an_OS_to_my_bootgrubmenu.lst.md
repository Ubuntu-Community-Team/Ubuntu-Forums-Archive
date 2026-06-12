---
title: "How do I add an OS to my /boot/grub/menu.lst?"
date: 2006-10-27
forum: General Help
---

### Post by kernco on 2006-10-27
I've installed Ubuntu on computers with Windows before and it has automatically set up Grub so that I can boot both of them.  This time, though, that didn't happen.  I have a computer with two hard disks.  Initially, Windows XP Home was installed on one of them.  I later installed Windows XP Professional on the second one, and I just recently installed Ubuntu over Windows XP Home.  Ubuntu didn't add Windows XP Professional to the Grub menu.  I tried adding it myself like this:
```

title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```
but it doesn't work.  When I choose it, I get no error message, it just does absolutely nothing.  What do I need to do?

---

### Post by beerorkid on 2006-10-27
well maybe a df -h will tell you the proper entry for (hd1,0)
must be something like (hd2,0) or something

---

### Post by bulldog on 2006-10-27
If windows is on your second hdd you have to map your hdd's because windows like to be on the first hdd.

example:```
### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Choad on 2006-10-27
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)

from a programmers POV that looks wrong....

---

### Post by bulldog on 2006-10-27
> **Choad said:**
> map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)

from a programmers POV that looks wrong....
 Could be,but it works for me and that's what count.:D

---

### Post by kernco on 2006-10-27
Ok, my Windows parition is hdb1.  I edited the menu entry to look like this:
```

title           Microsoft Windows XP Professional
map     (hd0) (hd1)
map     (hd1) (hd0)
rootnoverify            (hd1,0)
savedefault
makeactive
chainloader     +1

```

Now I'm getting the error: NTLDR not found

---

### Post by louieb on 2006-10-27
Choad wrote  	
> map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)

from a programmers POV that looks wrong....

Yea it does look weird. As a programmer I would think you would have to move the map to a hold area in order to make the swap. 

But you don't. I have XP on my second drive and that is what my grub entry look like and it works.

---

### Post by bulldog on 2006-10-27
> **kernco said:**
> Ok, my Windows parition is hdb1.  I edited the menu entry to look like this:
```

title           Microsoft Windows XP Professional
map     (hd0) (hd1)
map     (hd1) (hd0)
rootnoverify            (hd1,0)
savedefault
makeactive
chainloader     +1

```

Now I'm getting the error: NTLDR not found

Well it should work.
Verify ntldr exist on your windows drive.

---

### Post by louieb on 2006-10-27
I am A+ certified and have been playing with PC's since before the days of DOS. But the following is just an educated guess as I have not run into your exact situation before. At best this will fix it, at worst XP is still broke.

I believe the reason NTLDR is missing is the fact before you Installed Ubuntu on the first drive you had XP Home on and was dual booting XP Home and PRO. XP was probably using the NTLDR from the first drive.
I am assuming that you have 2 eide drives connected to a flat ribbon cable.
Now my guess at the fix.      

[LIST]
[*]Note: turn off the computer when you are doing all that plugging and unplugging.
[*]Unplug the Linux drive.
[*]Change the jumpers on the XP drive to master setting and plug in as master.
[*]Try to boot. I belive at this point you should still get the NTLDR msg. If it boot to XP then my guess is wrong. You can blow the rest of this off.
[*]If it doesn't boot get out your trusty XP CD and boot to it and try fix with the recovery mode feature.   
[*]I now assume you can boot to XP.
[*]I bet you see where I am going now.
[*]Now set the jumpers back on the XP drive to slave and plug it in as slave.
[*]Pug the Linux Drive back in as master.
[*]You should now be able to dual boot.

[/LIST]

---

### Post by Choad on 2006-10-27
> **louieb said:**
> Choad wrote  	


Yea it does look weird. As a programmer I would think you would have to move the map to a hold area in order to make the swap. 

But you don't. I have XP on my second drive and that is what my grub entry look like and it works.
exactly, oh well the grub boys are 1 step ahead :D

---

