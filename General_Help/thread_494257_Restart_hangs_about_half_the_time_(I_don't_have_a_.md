---
title: "Restart hangs about half the time (I don't have a Dell)"
date: 2007-07-06
forum: General Help
---

### Post by timzak on 2007-07-06
I did a search on this and didn't find much luck.  It seems only Dell users are having this problem.  I don't have a Dell.  I built my own system.  The motherboard is an Asrock 4core-DualVSTA.

About half the time, a system restart from Ubuntu will hang at the Ubuntu screen with the orange progress bar (I have to hit the reset button on the case).  The other half of the time, it restarts correctly.  A system shutdown always works fine.

What can I try?

---

### Post by Ayuthia on 2007-07-06
You might try noapic.  If that doesn't work, you should take out the quiet and splash to see where it is stopping.

---

### Post by timzak on 2007-07-06
> **Ayuthia said:**
> You might try noapic.  If that doesn't work, you should take out the quiet and splash to see where it is stopping.

Thank you for the reply.  How do I go about doing those things?

---

### Post by Ayuthia on 2007-07-06
You would need to edit your /boot/grub/menu.lst file.  Look for the section called End Default Options and you will find something that looks like this:
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=624abd75-e2cd-4015-bf54-3c66c3fcb31e ro noapic nolapic splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault


You can see mine where I have noapic and nolapic.  I have already removed the quiet out of the file.  All you have to do is remove the quiet and splash and add noapic in that line.  You will also have to do this as root (sudo).

---

### Post by timzak on 2007-07-06
Thanks, that was very helpful.  Since it doesn't hang every time, I'll have to see over time if it worked or not.  I'll report back either way.

Have a great weekend!

---

### Post by timzak on 2007-07-07
Hi,

Well, that didn't take long.  I think I figured out what causes the restart to lock up.  It seems to happen if my current session has gone into standby mode.  If that happens, then when I restart, it hangs.  If my session hasn't gone into standby, then I can restart okay.

Here is what I copied down from the screen with noapic added and splash removed:

> Network Manager: <WARNING> nm_hal_deinit (): libhal shutdown failed - connection is closed

* Sending all processes the KILL signal... [OK]
* Unmounting temp filesystems...
* Unmounting temp filesystems... [OK]
* Deactivating swap... [OK]
* Unmounting local filesystems... [OK]
* Will now restart
* Will now restart
[2232.479160] Restarting system.

The preceding text stays on the screen until I hit the reset button on the case.  Does any of that mean anything to you?

It appears that the first try at unmounting temp filesystems fails, and that it goes through two tries of "Will now restart".  I have no idea what those numbers in the brackets mean at the end.  Any ideas?

---

### Post by timzak on 2007-07-08
bump...it's been a couple of days since I got a reply.  Does anyone have any ideas on how I can get a system restart to not hang?  Does the info in my previous post mean anything to any guru here?

Thanks.

---

### Post by timzak on 2007-07-10
bump...still unresolved.  Anyone have any ideas?

Does it hurt anything to manually hit the reset button when a system restart hangs?

Thanks.

---

