---
title: "How to make aMSN accessible to non-admin user?"
date: 2008-06-23
forum: General Help
---

### Post by Halfling Rogue on 2008-06-23
I installed the most recent version of aMSN on my Gutsy system while logged in as the administrative user. I have another user on the system that doesn't have administrative permissions, and I want aMSN to be accessible to that user. However, aMSN only shows up when I'm logged in as the admin user, and I can't seem to find it anywhere as the non-admin user. How can I fix this?

**EDIT:** Finally just gave family admin privileges and completely uninstalled autopackage and aMSN before reinstalling.

---

### Post by cariboo on 2008-06-23
Install aMSN as a regular user. The reason only root can use the application is all the configuration files are in /root. Probably the best way to do this is to go to System-->Administration-->Synaptic Package Manger search for amsn and mark it for complete removal, then reinstall it. It will show up in your menu. You should never install software as root. The better way is  to use sudo, then you won't run into these problems.

Jim

---

### Post by Halfling Rogue on 2008-06-23
I installed it directly from the aMSN site using Autopackage (since SPM doesn't have the most recent version). I'm not sure how to uninstall it from familyroot, and it isn't working in the regular user account for some reason.

---

### Post by Halfling Rogue on 2008-06-24
Ah, actually, I think I might've been misleading. The system has two users, familyroot and family. familyroot has administrative privileges, family does not. I did install aMSN again as the family user (in the family home folder), but it won't work. It does still work (from the familyroot home folder) when I'm logged in as familyroot, though.

---

### Post by Halfling Rogue on 2008-06-24
Still isn't working. I tried putting a launcher for the familyroot version of aMSN on the family Desktop, but it still won't actually run the program if I'm logged in as the family user.

---

### Post by Halfling Rogue on 2008-06-24
Ugh. I switched family over to administrative permissions since it was just giving me too much of a headache, and uninstalled and reinstalled aMSN, and it *still* won't work! It says it's starting to open it and then it doesn't go anywhere.

---

