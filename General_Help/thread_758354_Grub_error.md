---
title: "Grub error"
date: 2008-04-17
forum: General Help
---

### Post by purry95 on 2008-04-17
I deleted the partition in which Ubuntu was installed because that is what the guide in PC Magazine said to do to uninstall Ubuntu, the next time I started up I was presented with a Grub Error screen. Rrror 17. What the hell do I do?

Thanks in advance.

---

### Post by Glaxed on 2008-04-17
Did you use parted or Gparted to do the partitioning?
Did you do the deletion from Ubuntu, or a LiveCD, or from your other OS?

I got error 17 when I first tried to dual-boot Ubuntu/XP, but I just went to full Ubuntu to fix the problem.

If no one else can give you a solution, try burning SuperGRUB disk. It's an amazing tool, (and I think) your last hope.
Good luck,

---

### Post by purry95 on 2008-04-17
I used the Windows Vista Partioner to delete the Ubuntu partion. I will try the superGrub thing, thanks.

---

### Post by Mchl923 on 2008-04-17
I had grub error 17 when I reinstalled ubuntu.  Grub disk let me boot into linux, but I couldn't boot without it.  Eventually I had to reinstall vista to restore MBR and then install ubuntu again.

---

### Post by angry_johnnie on 2008-04-18
Grub error 17:   "Invalid device requested"

What you have to do is insert your Windows installation disk, go into recovery mode and then run:

```
fixboot
```

and

```
fixmbr
```

I'm not sure, however, whether you have to run those in that particular order :-).

Do a forum search for more info, just to make sure.  There's been plenty of posts regarding this.

---

### Post by purry95 on 2008-04-18
Only prob is i dont have installation disks, I have a "HP Recoverey" Disk, apparently it works. But it doesn't. I am supposed to press f11 one immediate start up, I do but nothing happens, however my BIOS (f10) and shutdown (ESC) work.

---

### Post by Reg Editor on 2008-04-18
You can download the Recovery console.Search for my posts as I gave a link for it yesterday

---

### Post by angry_johnnie on 2008-04-19
If you still have your Ubuntu live cd, you could fix it from there.
That is, you can restore Windows's bootloader from within Linux.

Take a look at [this]("http://ubuntuforums.org/showpost.php?p=4691608&postcount=2") thread.


Other than that, [supergrub]("http://supergrub.forjamari.linex.org/") could probably do the trick, too.

---

