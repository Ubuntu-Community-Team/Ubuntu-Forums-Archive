---
title: "Failed Boot; Recovery fails.. error 0xfe11.  HELP!"
date: 2007-10-25
forum: General Help
---

### Post by dmgthe2nd on 2007-10-25
Before this problem ever happened, I was using ubuntu 7.04 without any problems till I tried installing the upgrades to 7.10.  The installations failed numerous times and now when I boot my computer normally, I'm able to put my login info succesfully.  After that, it goes directly to a light blue screen.  That never changes, its just frozen there.

I then try to run in recovery mode and I get an error.  Ubuntu states:
Setting up font and keymap...
WARNING: unknown X keysym ("0xfe11")

Please help if you can!
Thanks, D.

---

### Post by The Chef on 2007-10-25
Spent this week looking at that Ubuntu version of the Blue Screen of Death too.  If you have a flash memory card reader attached to a USB port try: [http://ubuntuforums.org/showthread.php?t=591135](http://ubuntuforums.org/showthread.php?t=591135)

Hope it helps.

---

### Post by dmgthe2nd on 2007-10-25
I checked out your thread and as I was about to install the bluetooth thing, it said run dpkg --configure -a.  So I ran that and it fixed my problem.  Thanks for you help though!

---

