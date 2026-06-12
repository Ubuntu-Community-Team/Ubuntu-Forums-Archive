---
title: "after nvidia driver on, unity desktop menu is gone away, still showed desktop items"
date: 2013-05-25
forum: General Help
---

### Post by sdowney717 on 2013-05-25
Simply activated the 310 driver rebooted and poof, menu gone.
Thank God I had the cinnamon desktop and could control alt del and log out and log in with Cinnamon 

So what happened?
Is there a fix you can imagine?

With unity just shows an orange colored back ground and various scattered desktop items.
nvidia card is gt620

---

### Post by grahammechanical on 2013-05-25
Experiment with another video driver. I do not use Nvidia any more. Not after trying 3 out of 5 or 6 Nvidia drivers and not getting a working desktop. Right click the desktop and select Change Desktop Background. That will load System Settings. Take it from there.

Regards.

---

### Post by Charlotte18 on 2013-05-25
Which release of Ubuntu are you using 12.04, 12.10, 13.04?

---

### Post by sdowney717 on 2013-05-26
13.04 and 64 bit

In cinnamon desktop nvidia settings shows driver working fine.

History of computer is, the drive OS had a crash error. I have /home on a separate partition. 
So I used gparted to delete OS partition
Then installed 13.04 64 bit and reused /home login and files

It was perfect working till I went to software and updates and told it to use the nvidia 310 driver.
Then reboot just got orange screen, no menu on the left side and  desktop icons were scattered on the screen.

Unity desktop can not use now.
Cinnamon desktop is working perfect.

---

### Post by Charlotte18 on 2013-05-26
I had a similar problem in updating from 12.04 to 12.10, 64 bit. I'd made a clone of 12.04 before the upgrade, so instead of trying to fix the problem, I just restored 12.04 from the image.

If I were having your problem, I would uninstall the nvidia driver and revert to nouveau, or I would add the xorg-edgers ppa and try those nvidia drivers.

---

