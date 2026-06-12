---
title: "top panel only partially adjusting to theme"
date: 2008-07-03
forum: General Help
---

### Post by magicmanfk on 2008-07-03
Hey guys, so, everything has been working well, but suddenly whenever I try to change themes, only part of the top panel changes, and the rest is black (I think from a previous theme). 

You can see a pic of my desktop with it here:
[http://img240.imageshack.us/img240/3453/examplexs8.png]("http://img240.imageshack.us/img240/3453/examplexs8.png")


Any ideas?

---

### Post by NEUR0M4NCER on 2008-07-03
I hesitate to ask the most obvious question... have you tried```
right-click the panel -> Properties -> Background -> None (Use System Theme)
```?

---

### Post by magicmanfk on 2008-07-03
> **NEUR0M4NCER said:**
> I hesitate to ask the most obvious question... have you tried```
right-click the panel -> Properties -> Background -> None (Use System Theme)
```?

don't worry about asking the obvious questions, but yes, I did try that. Thanks for the suggestion though. Interestingly enough, the left side and my name stay that black even if I change it to background color and choose one.

---

### Post by Doji on 2008-07-03
I see you have the "Custom" theme selected. That could be the problem. Click Customize and you should be able to change window borders and such. Or try selecting a full theme like Clearlooks and see if it works.

If that doesn't work go ahead and enter killall gnome-panel into the terminal and see if it looks right when it starts back up.

---

### Post by magicmanfk on 2008-07-04
> **Doji said:**
> I see you have the "Custom" theme selected. That could be the problem. Click Customize and you should be able to change window borders and such. Or try selecting a full theme like Clearlooks and see if it works.

If that doesn't work go ahead and enter killall gnome-panel into the terminal and see if it looks right when it starts back up.

ok, so when I do one of the full themes, it doesn't occur, which is a good sign. However, if I choose a full theme (we'll go with human), then go to the options and choose a different control theme, only a couple still show up partially black. I'll do a little more testing. I think it may be connected to one of the themes I used a while ago (SlickneS), because when I use that the panel sticks out in the same spots. Thanks for the suggestion!

---

