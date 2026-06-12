---
title: "The installer crashes straightaway"
date: 2007-04-19
forum: General Help
---

### Post by Lightspeed on 2007-04-19
[IMG]http://www.brokenbeta.co.uk/stuff/Misc/wubicrash.png[/IMG]

Clicking on either "Next" or "Back" on the first screen causes this. Running whatever version [this file]("http://cutlersoftware.com/ubuntusetup/latest.html") is, on a relatively typical Windows XP box.

I dunno what else to say, other than I really want to get this to work.

---

### Post by ago on 2007-04-19
Was the original folder renamed or moved or removed?

---

### Post by Lightspeed on 2007-04-19
I haven't got as far as creating a folder yet.

All I've done is type in a username and password.

---

### Post by ecology2007 on 2007-04-20
We will investigate that.
I suspect it is due do the iso MD5 file check, maybe password hashing.
Can you tell me if you allready have the current or a previous iso somewhere on your desktop or in the wubi folder ?

---

### Post by Lightspeed on 2007-04-26
Okay, now it's a different error and it happens straightaway (even before the window appears)

[IMG]http://www.brokenbeta.co.uk/stuff/Misc/wubicrash2.png[/IMG]

ecology: I have a copy of the ISO on the desktop with the installer, yes.

EDIT: By which I mean ubuntu-7.04-alternate-i386.iso

---

### Post by ebommf on 2007-05-03
The same happens to me i.e., I just double click the installer (wubi-7.04-minefield2.exe) and get that nice application error.
If it may help I on a Windows 2000 (Version 5.0 build 2195: Service Pack 4)
I would really appreciate to install ubuntu as with Wubi as I think it is a nice way to give it a try.

Cheers
Frank

---

### Post by ecology2007 on 2007-05-04
>  If it may help I on a Windows 2000 (Version 5.0 build 2195: Service Pack 4Can you try this latest minefield and tell me if you still have crash at start ?
[http://ubuntuforums.org/showthread.php?t=432808](http://ubuntuforums.org/showthread.php?t=432808)
There was in previous releases an option named 'XPstyle=on', it is now disabled but we can not test it on windows 2000 and tell if it is related to your issue..

---

### Post by ago on 2007-05-05
It might also be due to the fat discovery call

---

### Post by Lightspeed on 2007-05-05
It's working now.

However, n.b.: I was getting it with XP.

---

### Post by ago on 2007-05-05
Minefield 0.3 and 0.4 should have fixed that (there is still a debate whether it was XPStyle issue or a fat detection issue or both).

---

### Post by celsus on 2007-05-05
> **celsus said:**
> OK, I downloaded the alternate Kubuntu and minefield4.exe.  This time minefield asked me where to install.  I chose D: again; after making wubi contiguous and rebooting the grub loader terminates (with error 17) because it can't find menu.lst.  I uninstalled wubi and tried again.  Now, minefield did not ask where to install but started installing to the largest empty partition.  I uninstalled wubi again and restarted; now wubi ignored the .iso of kubuntu entirely and proceeded to try to download another copy.  I uninstalled wubi again and rebooted; now minefield crashes immediately.

After using regedit to delete the only reference to wubi (in MUICache), the installer defaults to behavior 2, i.e. it is being installed to my largest partition, regardless of whether I want it there or not.  I'm mystified as to why (and how) it offered me an options screen the first time I ran it and now, even after un-installing it, it won't.  wubi is being placed on the data partition of my new 320GB HD which hosts C: as well, I'll contig it and try to boot into Kubuntu.  If that doesn't work, I'll copy wubi to C:, contig it and try that.  I'll report my results.

---

