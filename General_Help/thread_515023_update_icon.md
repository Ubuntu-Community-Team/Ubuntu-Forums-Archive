---
title: "update icon"
date: 2007-08-01
forum: General Help
---

### Post by Lary Grant on 2007-08-01
I have a dapper machine that never displays the icon indicating that an update is available.  If I start Update Manager manually, I do see the updates.

I remember thinking I fixed it a while ago, because I found some option to turn it on, but in the end it doesn't seem to have worked.

Now what?

---

### Post by Seisen on 2007-08-01
If open up Synaptic and go to Settings>Repositories and then click on the Update tab there is an option for automatic updates.

---

### Post by stchman on 2007-08-01
> **Lary Grant said:**
> I have a dapper machine that never displays the icon indicating that an update is available.  If I start Update Manager manually, I do see the updates.

I remember thinking I fixed it a while ago, because I found some option to turn it on, but in the end it doesn't seem to have worked.

Now what?

Make sure you have the notification area installed on a toolbar.

---

### Post by RedSquirrel on 2007-08-01
The program that puts the icon on your toolbar is called 'update-notifier'. Make sure it's running. (And as stchman suggested, make sure there is a notification area on your toolbar/panel.)

---

### Post by Lary Grant on 2007-08-03
How do you check if there is a notification area and fix it if not?

---

### Post by nineteeneightyone on 2007-08-09
Lary, one of the ways I fixed the same error was to delete the top panel altogether and start again. (I'm sure there's an easier way - but I couldn't find it).

1). Have a look at the top Panel (where the time is etc.) essentially you'll end up deleting it, so it's a good idea to write down what was on there.

2). Right click on the top panel, then select "Delete this Panel" - then click "OK" on the warning alert.

3). Right click on the bottom panel (the one with the trashcan in it) and select "New Panel"

4). You should now have an empty panel at the top.

5). Right click on the top panel and select "Add to this Panel" and scroll down to the section named "Utilities" and add the item called "Notification Area"

6). The Update Manager Icon should appear (if there are any updates).

Repeat step 5 to make the panel the same as it was before you deleted it. Good Luck.

---

### Post by RedSquirrel on 2007-08-09
Or maybe you could just right-click on the top panel and attempt to add a notification area somewhere. It might even tell you that you already have a notification area on that panel... (sorry, I don't have GNOME installed so I can't verify this)

---

### Post by nineteeneightyone on 2007-08-12
> **RedSquirrel said:**
> Or maybe you could just right-click on the top panel and attempt to add a notification area somewhere. It might even tell you that you already have a notification area on that panel... (sorry, I don't have GNOME installed so I can't verify this)

Yes, I had the same problem as Lary and tried this, but still couldn't get it to work - hence the fix of deleting the whole panel altogether, which seemed to fix the problem.

---

