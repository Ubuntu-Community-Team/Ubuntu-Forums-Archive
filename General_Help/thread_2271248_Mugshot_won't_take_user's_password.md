---
title: "Mugshot won't take user's password"
date: 2015-03-28
forum: General Help
---

### Post by opus1 on 2015-03-28
When my son tries to add a photo for the login screen via mugshot, it asks for a password to make the change but won't accept any password entered (e.g., his password, root password, etc.). His password works when logging in, just not for this application.

Additionally, his name is grayed out so that it cannot be edited.  I thought that giving him elevated privleges through my account (the one created during installation) would solve the problem, but that has not been the case.  This is a fresh install of xubuntu 14.04.

How can he change his log in dialog picture?

---

### Post by opus1 on 2015-03-28
I just did an extra test and elevated his privleges to administrator level and that solved the problem. This is a completely unacceptable solution, though... I don't want him to have administrator privleges.  

So the question still stands: how can I fix it so that he can change his log in photo with just desktop user privleges?

It seems silly to give users this option, but then require administrator privleges to use it -- so clearly, I'm missing something here.

---

### Post by Dennis N on 2015-03-28
Name the login image **.face** and place it in your son's home directory. Note this is a hidden file. When he selects his user name, the picture should change to his. Mine is a 90x90 px png image. The most recent user's picture shows initially at the login screen.

---

### Post by opus1 on 2015-03-28
Thank you Dennis N! That will do fine for a solution -- he's a clever kid and can handle doing that. 

I narrowed the group assignment to enable the feature in mugshot down to sudo.  I don't understand that decision, but this work around will solve the problem.

I will mark this thread as solved -- hope it takes, because the last thread I marked solved didn't work.

---

