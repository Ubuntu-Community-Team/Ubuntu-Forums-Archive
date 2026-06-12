---
title: "Startup application doesn't save my changes."
date: 2014-09-16
forum: General Help
---

### Post by Matteo_Martinelli on 2014-09-16
Hi guys,
I tried to add some applications to "Startup application" but when I closed it, the application disappear.
Now, there is just one record: Indicator.

How can I fix it?
Thank you.

---

### Post by CantankRus on 2014-09-16
Is there a .desktop file for the added application in **~/.config/autostart** ?

---

### Post by Matteo_Martinelli on 2014-09-16
No there is nothing! I googled and I found that for every application should be one .desktop file. After adding one application I think the Startup application doesn't create the .desktop file.

One further information:
 1. After **ls ~/.config/ **the color of autostart folder is red with gray background (I don't know the meaning of this color)

---

### Post by CantankRus on 2014-09-16
What are your permissions for the ~/.config/autostart directory?

---

### Post by Matteo_Martinelli on 2014-09-17
After **ls -al ~/.config/**

---

### Post by CantankRus on 2014-09-17
Does that mean you have an autostart directory owned by root that links to **/usr/bin/chrome**? 
:confused:

---

### Post by Matteo_Martinelli on 2014-09-17
Yes, I simply deleted the autostart folder and create one another and all comes back to work properly. SOLVED

---

### Post by CantankRus on 2014-09-17
Yes if you delete the  ~/.config/autostart folder another will be created when you add an entry to Startup Appliations.

Ok, you can mark the thread solved by going to your first post....
Edit > Go advanced 
and change the prefix to "SOLVED"

---

### Post by Iowan on 2014-09-17
> **Matteo_Martinelli said:**
> ... SOLVED
[Marked]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") it for you. ;)

---

### Post by Matteo_Martinelli on 2014-09-17
Thank u, I didn't find how could I mark it as solved.

---

