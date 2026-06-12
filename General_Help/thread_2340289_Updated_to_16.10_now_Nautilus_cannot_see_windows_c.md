---
title: "Updated to 16.10 now Nautilus cannot see windows computer"
date: 2016-10-17
forum: General Help
---

### Post by naiqor0-people on 2016-10-17
:confused: Just updated from 16.04 to 16.10 and now cannot see or access my windows computer on the windows network, windows network shows up in Nautilus but double clicking does nothing, just a dialog box saying "opening smb:///" but nothing happens. But windows can see Ubuntu and access the files. Have they messed up Samba again, they did when the 16.04 update came through.
Thank you
Brian

---

### Post by zajcek on 2016-10-17
Have you tried smb://ip_address or smb://computer_name?

---

### Post by naiqor0-people on 2016-10-18
Solved, did 2 more reboots and ubuntu found windows computer with no problems. It was a funny up-date. Ubuntu cleans up and reboots after update, then it had no internet access, so did a reboot and it found it. Then it found the windows network WORKSPACE after 2 more reboots.
And zajcek thank you for your time and your hint, though I had tried the smb://computer_name.

---

