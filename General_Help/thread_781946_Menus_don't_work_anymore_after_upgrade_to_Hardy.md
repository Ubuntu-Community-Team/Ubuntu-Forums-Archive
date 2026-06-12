---
title: "Menus don't work anymore after upgrade to Hardy"
date: 2008-05-04
forum: General Help
---

### Post by AndyNJ on 2008-05-04
I just upgraded to Hardy and now none of the menus in the system work. Be it the application/places/system menus, menus in programs, right-click context menus, none of them work.

Also, I think that maybe some dialog boxes aren't working too. I get a notification at the top saying that there was a crash report found, but when I click on the icon to show it, I get nothing. 

If I log into a failsafe gnome session, the menus work fine and this problem didn't exist in Gutsy for me. 

I'm a bit of a n00b still so where is a good place to start trouble shooting this? I'm assuming that it's one of the startup scripts that is crashing, but how can I view the report from the terminal since I can't seem to get to it any other way?

---

### Post by macaholic on 2008-05-04
That is quite a strange issue, do the menus work if compiz is not running or turned off? (metacity --replace will stop it)

---

### Post by AndyNJ on 2008-05-04
Yes! That made them start working again. 

So now that we know it's Compiz, what can I do to resolve it?

---

### Post by chrisccoulson on 2008-05-04
Try deleting your Compiz profile
```
mv .compiz .compiz_backup
gconftool-2 --recursive-unset /apps/compiz
```
You might need to log out and back in again

---

### Post by AndyNJ on 2008-05-04
Where do I have to CD to to get to the compiz settings?

---

### Post by chrisccoulson on 2008-05-04
You just need to be in your home folder:
```
cd ~/
```

---

### Post by AndyNJ on 2008-05-04
awesome! I'm back up and running again!

Thanks to both of you!

---

