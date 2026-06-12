---
title: "Evolution startup assistant runs at each login"
date: 2007-12-04
forum: General Help
---

### Post by grahams on 2007-12-04
For one users account every time Evolution runs the Evolution startup assistant starts. If configured the user can access email and everything works fine until they log out and login.  The next time they start evolution they have to go thru the startup assistant. Other users on the same system do have they this issue. 

I've deleted their .evolution directory but the same thing happens. Anyone know what is happening and how to fix?

Thanks in advance.

---

### Post by raul_ on 2007-12-04
> **grahams said:**
> For one users account every time Evolution runs the Evolution startup assistant starts. If configured the user can access email and everything works fine until they log out and login.  The next time they start evolution they have to go thru the startup assistant. Other users on the same system do have they this issue. 

I've deleted their .evolution directory but the same thing happens. Anyone know what is happening and how to fix?

Thanks in advance.

you get the assistant when you delete the .evolution folder because it goes looking for config files that don't exist, thus starting the assistant

---

### Post by grahams on 2007-12-04
Thanks

.evolution exists and has the same properties as other users. i.e. owned by the user, same permissions etc.

I deleted it to force it to be recreated, which is was, but it is still screwed up when recreated.

I even tried create a dummy account setting up evolution, copying to this users account and changing the ownership. Still it starts the setup assistant after each logout :(

3 other uses on this system and they are all ok.

---

### Post by grahams on 2007-12-06
Anybody?

---

