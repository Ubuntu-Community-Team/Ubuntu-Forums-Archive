---
title: "portable drive not showing full capacity.  How do I format it?"
date: 2007-11-23
forum: General Help
---

### Post by Zeenomorph on 2007-11-23
I have an 80gb usb drive.  I want to back up my system, but I had too much data on it.  I deleted what was not necessary, and only have 10gb on it now.  The issue is the computer still tells me that there are only 11gb available.  When I check it in right-click properties it tells me that 63gb are being used!  I don't have any idea where to go from here. 

I'm a total newb, so easy instructions would be helpful.  I thought that I would just format it and see what would happen, but I don't even know how to do that.  I tried to get to it in terminal, but the device name has spaces in it, I don't know how to 'cd' to it.

Thank you for any help that you can provide.

---

### Post by TidusBlade on 2007-11-23
I am sure that you probably have tried this, but did you empty the trash :P ?

---

### Post by Zeenomorph on 2007-11-23
I did.  I restarted, I mounted, and unmounted.

---

### Post by hikaricore on 2007-11-23
Be aware that in actual space your 80Gb drive only actually contains about 74.5GB of space.
This is not a fault of the hardware or the operating system.  This is the fault of drive makers marketing their drives improperly and taking advantange of their customers.

That aside have you checked the Trash?  Files deleted with the DEL key are moved to the "Trash" instead of actually being deleted.
Also with some external devices, you may need to unmount meaning right click on the device and choose Eject or Unmount, for the drive to finish the write process and show the free space properly.

---

### Post by hikaricore on 2007-11-23
I was typing while the other replies happened... lol

Open up a terminal and type:

> cd /media
ls

Find the name of your drive and type:

> cd "Drive Name"

In quotes **where Drive Name is the actual name of the device**.

Once you're in it's path, type:

> ls -la

This will show any hidden files on the drive.  Be on the lookout for any filenames that start with a "." dot that you may not have been aware of before.

---

### Post by Zeenomorph on 2007-11-23
That's the problem.  I can't.

My drives name is "Mojo Giga Storage".  I can't get to it because of the spaces (I think).  When I cd to Mojo, it's not found.  When I cd to Mojo Giga Storage, it's not found.

---

### Post by hikaricore on 2007-11-23
Right but if you follow the instructions I gave you, the spaces don' t matter..

---

### Post by Zeenomorph on 2007-11-23
You were totally right.  You da man.  And I seem to be an idiot because it looks as though the trash is not removed.  

total 24
drwxrwxrwx 1 root root 16384 2007-11-22 23:42 .
drwxr-xr-x 4 root root  4096 2007-11-23 00:02 ..
drwxrwxrwx 1 root root  4096 2007-11-22 22:58 .Trash-mojo

Is that what that means?  If so, what do I do now?

Thank you very much for taking the time to help me.

---

### Post by Zeenomorph on 2007-11-23
Got it.  If anyone else has this problem, you can open the drive and hit ctrl+h, then you can see the trash folder.  Enter it, and shift+del.  I got all of my space back by doing this.

---

### Post by hikaricore on 2007-11-23
Aye sorry, I should have mentioned that as well.  I'm just too used to terminal commands.

Glad you got it resolved and best of luck in the future.  ^_^

---

