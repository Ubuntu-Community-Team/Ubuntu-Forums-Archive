---
title: "Edit &quot;open file with&quot; list in Double Commander"
date: 2024-01-06
forum: General Help
---

### Post by Regenpak on 2024-01-06
I am trying to edit the "open file with" dialog (screenshot) to remove unwanted and duplicate entries but I cannot figure out where or how this is stored. The extensive settings do not have the possibility to do this nor can I find any files (like doublecmd.xml) which contain this information. Adding programs is easy but subsequently removing them seems impossible. How can I solve this?

---

### Post by Regenpak on 2024-01-07
I found that editing ~/.config/mineapps.list does not help because many programs that are associated from within Double Commander are not in there. So the question remains: where does DC store these additional file associations?

---

### Post by Regenpak on 2024-01-07
Some more digging around [revealed]("https://doublecmd.h1n.ru/viewtopic.php?p=30600#p30600") that these file associations are modified system-wide. In my case they are stored in /usr/share/applications/mimeinfo.cache. Did not see that coming. Editing the cache solved the issue. Weird that this is not done in my home directory.

---

### Post by Holger_Gehrke on 2024-01-07
You might want to take a look at ~/.local/share/applications/mimeinfo.cache, which should be the the user-specific override for /usr/share/applications/mimeinfo.cache. Both of these files should be generated from the 'MimeType=' lines in .desktop files by the program update-desktop-database. There's also a mimeapps.list in ~/.config which should list the default app for a specific mime type.

Holger

---

### Post by Regenpak on 2024-01-07
The override you mention does not exist in my Ubuntu MATE install. Maybe if it did it would have worked. The ~/.config/mimeapps.list file is ignored as I found out the hard way. In any case, editing the system-wide file solved the issue. Weird huh!

---

### Post by dragonfly41 on 2024-01-07
Have you tried Krusader which is similar to Double Commander.? Krusader is rich in features.
I have tried both and both are in my docky bar.

---

### Post by Regenpak on 2024-01-07
> **dragonfly41 said:**
> Have you tried Krusader which is similar to Double Commander?
I've heard of it but I've tailored DC to my needs. Might give it a spin though. Caja file manager rather limited and in any case not double-paned.

---

### Post by dragonfly41 on 2024-01-07
There are twp others I tried .. 4pane and Midnight Commander .. but I returned to Krusader. although note that it has a lot of KDE baggage.

---

### Post by Regenpak on 2024-01-07
Krusader doesn't solve the "open file with" edit issue. Behavior is identical to DC's. But it doesn't matter since I figured it out above. This is not DC's fault. Nor Krusader's.
<rant>
This behavior is typical of software not developed for the end user. Microsoft is even better at that which is the main reason I stick with Linux. At least most of the time eventually I can get expected results. Thanx to fora like these.
</rant>

---

### Post by dragonfly41 on 2024-01-08
Just a followup note:

Having used both Krusader and Double Commander in replying to this thread I realise that each tool offers some features that the other does not offer.  So I now use both in a cooperating dual workflow.

---

