---
title: "File Will Not Delete"
date: 2006-12-28
forum: General Help
---

### Post by elcasey on 2006-12-28
I'm trying to figure out a way to "force" a file to be removed. I downloaded a DVD image, intending to burn it. Both NeroLinux and GnomeBaker refused to burn it (it was an .img file, not an ISO) so I decided to give it a pass. I dropped into terminal and did a "rm -rf <dirname>". It goes on forever.

I hit Ctrl-C, nothing happens. I close the terminal window, go to Nautilus and press Del. I try to empty the Trash, it hangs. I go back to ~/.Trash, [FONT="Courier New"]sudo rm -rf <dirname>[/FONT], it hangs.

If I move this file to /tmp and reboot, could it possibly screw up the boot sequence and cause my entire installation to hang? It's using up space, nearly 5GB worth, and I need to figure out how to remove the darn thing!

Thanks in advance!

---

### Post by fragos on 2006-12-28
A file that big may take a while to delete.  Have you checked the ownership.  Right click file icon and select Properties and then the permissions tab.  Even if you're the owner, the owner access may be set to Read only.

---

### Post by elcasey on 2006-12-28
I had let it run for quite awhile initially before deciding that the process was hung.

Strangely enough, I was also having problems reading a known good DVD, so I rebooted. I tried to delete the .img file again and it worked just fine. Edgy is weird sometimes. :-?

---

### Post by towsonu2003 on 2006-12-29
just a side note: be careful with that command... if you mistype, you might just delete your whole home directory...

---

### Post by elcasey on 2006-12-29
Heh, I'm careful not to use a "/" anywhere in there! :twisted:

---

### Post by joeashcraft on 2007-04-26
so did you find out how to force empty the trash?

(sorry for semi resurrection)

EDIT:
i found, tried, and succeed with this command
```
sudo rm -r ~/.Trash/*
```

found at this thread
[http://ubuntuforums.org/showthread.php?t=332518](http://ubuntuforums.org/showthread.php?t=332518)

---

