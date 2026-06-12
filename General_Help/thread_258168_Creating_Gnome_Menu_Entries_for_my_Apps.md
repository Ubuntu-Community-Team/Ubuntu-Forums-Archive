---
title: "Creating Gnome Menu Entries for my Apps?"
date: 2006-09-15
forum: General Help
---

### Post by wkulecz on 2006-09-15
How do I create a Gnome menu entry for my applications?

The Ubuntu guide told me about the System->Preferences->Sessions to start them automatically, which would be good enough, but it started them from a different (mysterious) directory rather than the one that the executable is in (and expects).

Double clicking it in a nautilus file browser window starts it the way I need (want).

I tried Applications->Accessories->Alacarte and it acts like its created the entries, but they never show up on the menus -- even after sudo alacarte.

--wally.

---

### Post by PriceChild on 2006-09-15
Ok... 2 things.

If you want to run a command at startup from your home for example, you must also type its path:

/home/<<your username>>/<<name of exec>>

for example.

Secondly, your alacarte is probably not working because permissions are incorrect in your home directory.

I reccomend you do a

```
sudo chown <<username>>:<<username>> -R /home/<<username>>
```

---

### Post by wkulecz on 2006-09-15
Neither of these is/was the issue.  I had an absolute path in the sessions startup box.  The application started correctly, but the directory it inherits is not the one it was started from.  I don't want absolute paths in my app to find its config files.

The directory is already user.group my default login.

Recall, I tried sudo alacarte too.

--wally.

---

