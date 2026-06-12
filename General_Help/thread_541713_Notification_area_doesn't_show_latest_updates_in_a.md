---
title: "Notification area doesn't show latest updates in a limited permissions user account"
date: 2007-09-03
forum: General Help
---

### Post by ekravche on 2007-09-03
The update notification no longer works for me. It use to worked back in 5.04, but when I updated to 5.10 it stopped working. Now in 7.04 the problem still persists. I'm running the notification area in a limited permissions user account. It was like this in 5.04 and it worked, but something changed. Now I can't see any software updates using that notification area in 7.04. Any ideas as to why?

Thank you in advance.

---

### Post by bonzodog on 2007-09-03
it's disabled in accounts that do not have access to the update manager - i.e, limited user accounts. A full admin level user account would be ok.

---

### Post by strabes on 2007-09-03
You can do the same thing by running:```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by ekravche on 2007-09-03
> **bonzodog said:**
> it's disabled in accounts that do not have access to the update manager - i.e, limited user accounts. A full admin level user account would be ok.

The thing is that it used to work before in 5.04, so why is not working anymore? All I want to see is update notifications in my main account, is there a way to somehow fix that?

---

### Post by ekravche on 2007-09-04
> **strabes said:**
> You can do the same thing by running:```
sudo aptitude update && sudo aptitude upgrade
```

That means that I will need to run this myself every couple of weeks. I need the notification area to tell me whether there are new updates, and whether I need to run that command to begin with... Catch my drift?

---

### Post by ekravche on 2007-09-10
When I look at the sessions under System->Sessions. Then click on the Current Session tab, I see the update-notifier program, but I can't seem to configure it. Any help regarding this would be greatly appreciated.

---

### Post by ekravche on 2007-09-11
When I run the command update-notifier from the command line I get the following error

> evgenyserver@evgeny-desktop:~$ update-notifier 

** (update-notifier:6016): WARNING **: not starting because user is not in admin group



The strangest thing is that it used to work in the past with 5.04... Oh well, I guess there is no way of making it work with the new version of ubuntu. It would be nice to see latest updates from a non admin account, since for security reasons you wouldn't want to be running your regular user in an account that has admin privileges. Just my 2 cents...

---

