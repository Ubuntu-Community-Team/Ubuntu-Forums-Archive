---
title: "Problems after update"
date: 2016-03-16
forum: General Help
---

### Post by gimpy63 on 2016-03-16
I am running Ubuntu 15.10. After the last update I have several problems.
1. When I go to settings/displays, I get "Could not get screen information". I am running 3 monitors, up until the last update I could go in and make changes. I put in a new monitor and found this when I went in to tweak it and got this message. I put the old monitor back on and still got the same message.
2. I have 2 printer options in settings and ever since, I can't scan with my printer. It shows the right printer in each. I can print a test page from each, but I can no longer scan.

I had neither of these problems before the last update.

---

### Post by mastablasta on 2016-03-17
1.  what is the GPU model?

2. What is the printer model?

see more here: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by gimpy63 on 2016-03-17
$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 730] (rev a1)
 The printer is a hp Envy 4500.

Sorry I should have known better, just getting frustrated.

---

### Post by mastablasta on 2016-03-21
1. do you have the correct drivers installed for NVidia? they usually have a few versions available. and sometimes it can make a difference. I couldn't get GT 730 to run at all, but I think my issue may be elsewhere, though it did involve blank screen...

2. try latest hplip drivers.

---

