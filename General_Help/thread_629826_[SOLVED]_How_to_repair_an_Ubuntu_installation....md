---
title: "[SOLVED] How to repair an Ubuntu installation..."
date: 2007-12-02
forum: General Help
---

### Post by Earthwormzim on 2007-12-02
I just recently bought a new external hd that came formatted as fat32.  So, first I decided to use Norton Partition Magic to format it to NTFS.  When I clicked "Apply Changes", it said that my system required a reboot to complete the operation.  So I clicked reboot.

Upon boot, GRUB gave "Error 17" and would not go past that...i.e., neither Windows or Ubuntu would boot.  I did a quick search on my other computer for "GRUB" and "ERROR 17", and didn't find any answers that sounded like they pertained to my problem. 

So, I just did what I could, and restored my Windows by using Acronis Backup.

So, now my Windows works fine, but my Ubuntu is still left in the cold.  I never deleted any of my Ubuntu files, and my drives are all still exactly the way I left them when I last successfully booted into Ubuntu (with the exception of the new hd).  So...what do I do to get my Ubuntu installation back up and running?

---

### Post by michaelzap on 2007-12-02
Sounds to me as if you just need to [reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by Earthwormzim on 2007-12-02
Ok, did that.  Installation of GRUB was successful...no errors, etc...and...upon reboot...
...ERROR 17 again!  It says something like "Cannot mount selected partition".

Haha!  What to do...what to do...???

---

### Post by merlinus on 2007-12-02
Can you boot from a linux live cd?

If so, enter this in a terminal window:

sudo fdisk -l

to see if your ubuntu partition shows up.

If so, then you will probably have to manually mount the partition, and then look at and perhaps edit  /boot/grub/menu.lst

---

### Post by Earthwormzim on 2007-12-02
OK, first of all...SUCCESS!  I got it to boot again, but only once.  What I did was:  on the GRUB menu, I pressed 'e' on the line that says:

```
Ubuntu 7.10, kernel 2.6.22-14-generic
```

On the next screen, the first line looks like this:

```
root  (hd0,6)
```

Now, according to the tutorial posted above on how to reinstall GRUB, the value in the parenthesis is supposed to be the same as the result that is returned by the command "find /boot/grub/stage1"...and the returned value for me was (hd0,5)...(I also happen to know that my Ubuntu is installed on my 5th partition...so I'm pretty sure that it is really (hd0,5)).

So, I pressed 'e' on the first line, and changed it to "root  (hd0,5), and then pressed 'b'.  Voila!  It booted into Ubuntu just fine.  

Then, to see if my changes were permanent, I restarted the system...and...ERROR 17 again!  So, I pressed 'e' on the first line again, and on the second screen, it still said:

```
root  (hd0,6)
```

even though I just changed it before.  Apparently editing it from here is only temporary.  So...how do it edit it so that it is not temporary?

(note:  I'm going to go ahead and try booting into Ubuntu again, and editing the grub file)

---

### Post by Earthwormzim on 2007-12-02
Ok, I edited the menu.lst file, and it worked like a charm!  Everything works fine now!  W00t!!!  Too bad I already hosed my Windows stuff when I used Acronis to restore my Windows stuff from a back-up.

But a question remains:  how did the value (the (hd0,5)) get changed in the first place (to (hd0,6))?  I never changed it!  Are GRUB and Norton Partition Magic bitter enemies?  What would cause this to happen?

---

