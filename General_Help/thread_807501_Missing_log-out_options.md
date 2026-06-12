---
title: "Missing log-out options"
date: 2008-05-25
forum: General Help
---

### Post by ChameleonDave on 2008-05-25
From the K-menu or desktop menu, I can choose to log out, and then KDE gives me several options (Log out, Suspend, Hibernate, Restart, Turn Off).
I have tried to set my girlfriend's computer up exactly the same, and yet she only has "Log out".  I want her to like Linux, so it's embarrassing to tell her she has to type "sudo reboot" into Konsole.  I don't get why her computer behaves differently.

---

### Post by pixel :-) on 2008-05-25
system sttings-->advanced-->Session manager check "offer shutdown options"?

---

### Post by ChameleonDave on 2008-05-25
> **pixel :-) said:**
> system sttings-->advanced-->Session manager check "offer shutdown options"?

First thing I tried.

---

### Post by Zorael on 2008-05-26
Does she have the **gdm** and/or **xserver-xgl** packages installed? If so, nuke them and see if it helps.

---

### Post by ChameleonDave on 2008-05-26
> **Zorael said:**
> Does she have the **gdm** and/or **xserver-xgl** packages installed? If so, nuke them and see if it helps.
Thanks!  Removing xserver-xgl solved the problem.  I have no idea why that would cause a problem in the first place.

I think I'll put her on KDE 4 anyway.  She doesn't need the greater customisability of KDE 3 at this stage.

---

### Post by Zorael on 2008-05-26
Have her try both. :>

I've given KDE 4.0.4 a few tries and I always go back to 3.5.9, mostly because of small bugs, flashing and corrupted graphics, and general lack of features.

---

### Post by ChameleonDave on 2008-05-27
> **Zorael said:**
> Have her try both. :>

I've given KDE 4.0.4 a few tries and I always go back to 3.5.9, mostly because of small bugs, flashing and corrupted graphics, and general lack of features.

Yes, I myself am sticking with 3 for now for that sort of reason, but she doesn't need many features.  She just needs it to work, and be fast.  3 is slow and buggy (e.g. the shutdown thing) on her machine.  4 is working much faster, and is less confusing.  Plus, they seem to have fixed most of the display bugs now.

KDE development is currently a rare example of the cutting edge being actually better for newbies.  If 4 hadn't come out, I would have got rid of KDE completely for her, and put her on XFCE instead.

---

### Post by _sleeper on 2009-02-02
> **Zorael said:**
> Does she have the **gdm** and/or **xserver-xgl** packages installed? If so, nuke them and see if it helps.

thanx man! i've been trying to fix this for awhile without any progress.

---

