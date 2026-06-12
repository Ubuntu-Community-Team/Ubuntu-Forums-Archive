---
title: "how to change the greeter background"
date: 2019-12-08
forum: General Help
---

### Post by Skaperen on 2019-12-08
i'd like to change the greeter background.  how can i do that?

i notice that the greeter background is different for some users,  can i set a different background image for each user the greeter menu has selected?

---

### Post by vanadium on 2019-12-08
By default, the greeter picks up the desktop background of the user that is currently selected. That could be considered a privacy issue, but that is how it is setup. Thus, apparently it already does what you would like.

I am not sure if it might be possible to set a background for each user that differs from the user's desktop background. The alternative is to set a fixed background that does not depend on the selected user.

---

### Post by Skaperen on 2019-12-08
it doesn't pick up any user background on my Xubuntu 18.04 LTS.  two of the users it shows different background for have the same background when logged in.

---

### Post by Artim on 2019-12-09
Strange.  It picks up my chosen wallpaper as the greeting background (Xubu 18.04).

**Menu** --> **Settings Manager** --> **LightDm GTK + Greeter Settings** (root password required) --> **Background**.

---

### Post by Skaperen on 2019-12-09
first it prompted me for authentication by asking me for the password of the wrong user.  i see the problem, now.  it only does wallpaper, not background.  the users all have a color gradient for a background, not a wallpaper image file.

for fun, i set the color in this menu to light purple, closed the menu, and logged out to get the greeter.  it briefly showed light purple.  then it showed the wallpaper it has been showing before.  i changed the greeter menu to admin and it changed to light purple and stayed that way.  back to the LightDM setting menu.  now i can't get the wallpaper setting it previously had, back.  but it was probably overwriting it with the unknown wallpaper it still shows me when the greeter menu selects non-admin users, which is not what i get when i login.  so now one mystery is solved and another mystery is more prominent (where is this wallpaper set at).  that and how can i set a wallpaper or background in the greeter that will stay?

---

