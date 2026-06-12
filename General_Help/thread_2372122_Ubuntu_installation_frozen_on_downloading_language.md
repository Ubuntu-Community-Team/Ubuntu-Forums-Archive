---
title: "Ubuntu installation frozen on downloading language packs"
date: 2017-09-21
forum: General Help
---

### Post by tomsax on 2017-09-21
I'm trying to load ubuntu on HP laptop with dual boot to Windows 10. 

It has got frozen on downloading language packs.

[ATTACH=CONFIG]276801[/ATTACH]

This is the second time it has happened.  The last time only way I could think to stop things was to press power button,  I then found Windows also corrupted and had to reinstall windows with the recover USB.

Cant move curser to skip.  No response to any keys.  Have taken off internet cable but still showing as connected as in photo.

Don't want to go through the long painful process again so I don't know what I can do not to lose windows and somehow come back to the Ubuntu installation.

Really frustrating. I have had a week now of trying to install Ubuntu. Previous problems were on this thread.
[https://ubuntuforums.org/showthread.php?t=2371633](https://ubuntuforums.org/showthread.php?t=2371633)

 I've done this on 4 computers in the past but now feel like giving up on this one.

Tom

---

### Post by ajgreeny on 2017-09-21
Did you tick the boxes to install updates and third party apps whist installing the OS?
If you did and there is no connection, either wifi or cable ethernet, it may cause a delay which you are seeing.

Try installing again but do not ask to update as you install or add the third party apps.

---

### Post by ian-weisser on 2017-09-21
> **tomsax said:**
>  then found Windows also corrupted and had to reinstall windows with the recover USB.

The Ubuntu installer merely attempts to determine the filesystem on each partition.
The installer writes nothing to any Windows partition that it finds.
Be open to considering different causes of corruption...like a dying hard drive.

---

### Post by tomsax on 2017-09-22
The good news is that Windows is still working but there is no option to go to Ubuntu. 

The c drive is partitioned and this is what I see when I open Disk Management in Windows:

[ATTACH=CONFIG]276817[/ATTACH]

How can I install Ubuntu on to the Partition 5?  I imagine if I use the Ubuntu installation drive it might just split the windows partition into two but not sure.

---

### Post by tomsax on 2017-09-23
Managed to reinstall ubuntu and it seems to be working okay so good news.  I just followed the instructions on the usb driver installer and it worked!

---

