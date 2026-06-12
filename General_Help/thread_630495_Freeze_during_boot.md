---
title: "Freeze during boot"
date: 2007-12-03
forum: General Help
---

### Post by ianrobertperez on 2007-12-03
Hi,

I recently installed Gutsy (fresh install) and it's been working fine for about a week, but this morning when I turned on my computer, it froze at about 30% (I restarted about 4-5 times to make sure it wasn't a random ocurrence, because it has also been randomly freezing at bootup during the past week).  I wasn't sure how to see the text of the boot status, so I was pressing Ctrl+random keys, then Alt+random keys, and found that the Alt+Function keys showed various startup screens, and one of them ended with the following line (taken from memory, since I'm at work):

* Checking root file system...
fsck 1.40.02

There was nothing after that, so I'm assuming this is where the bootup froze.  I couldn't hear any harddisk activity either, so I'm pretty sure it's not doing anything.  I left it running so I'll report in this thread whether or not it got past this point after about 8-9 hours (after this much time I think it's safe to assume it's frozen indefinitely).

I have 3 drives in my system, so I went into fstab and commented the lines for my other 2 drives, but it didn't help.  My main drive is a 74gb 15k RPM SATA (western digital), so I can't imagine that it would take this long to run fsck on a 74gb drive, but I could be wrong.

Not sure if it's related, but I've also had random lockups during shutdown.

Any help would be greatly appreciated.  I don't want to go back to Windows! :)

---

### Post by metalheart on 2007-12-03
Have you tried to boot into safe mode? You will see all the boot messages on the screen without having to switch between virtual terminals.

---

### Post by ianrobertperez on 2007-12-03
Ah yes, I forgot to mention that.  I was able to boot into recovery mode just fine.  It even mounts all 3 of my harddisks (this was before I commented them out in fstab).

---

### Post by metalheart on 2007-12-03
And you did not experience any lock-up in safe mode?

---

### Post by ianrobertperez on 2007-12-03
I booted it into recovery mode at least twice with no problems.  Like I said before, it even mounted my other 2 drives and I could see their contents just fine.

---

### Post by metalheart on 2007-12-03
Can you start gnome in safe mode with

```
sudo /etc/init.d/gdm start
```

---

### Post by ianrobertperez on 2007-12-03
I'll try it in about 5 hours when I get home from work.  Thanks for your help thus far.

---

### Post by ianrobertperez on 2007-12-04
Well when I got home the first thing I tried was to disable fsck (I had seen this suggestion in other forums regarding similar issues with fsck).  I did this by setting the last field in fstab to 0 (they were all set to 1).  I restarted after making this change and ubuntu booted up perfectly.

However, this morning after starting up my computer again, it froze during bootup again.  I switched to the console and the last message was (again, taken from memory since I'm at work):

* Activating swap disk

This is probably related to the random boot lockups I had been having before the fsck lockup, because I restarted after this and it booted just fine.

Anyway.. I suppose my installation is back to normal, but I am still curious why fsck was freezing and why I continue to get random lockups at bootup?

Thanks for all your help by the way.

---

### Post by metalheart on 2007-12-04
I don't think disabling fsck is a good idea. If you have Ubuntu live CD, boot from it and run fsck on your partitions (you may need to unmount it first).

```
fsck /dev/sda1
```

If it runs fine, you will know your disk is OK.

---

### Post by ianrobertperez on 2007-12-04
Well if it runs fine, then isn't there a problem with fsck?  I can't leave it enabled if it freezes during bootup.  I'll run fsck with a live cd tonight and I'll let you know what happens.

---

