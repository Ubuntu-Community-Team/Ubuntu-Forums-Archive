---
title: "quit button no longer gives me a choice, automatically logs me out"
date: 2007-02-02
forum: General Help
---

### Post by Polygon on 2007-02-02
Whenever i want to keep my session locked, but want other people to login, i click the red "quit" button in the top right corner of the screen

just a couple days ago, when i click the quit button, it just automatically logs me out, no longer giving me a choice on if i want to log out, shut down, restart, hibernate, etc

i tried removing the quit button and then re-adding it to the panel.. but to no avail

any suggestions?

---

### Post by Polygon on 2007-02-03
bump...

---

### Post by Polygon on 2007-02-03
bump....

---

### Post by jrickmar on 2007-02-03
does using System-Quit work properly?

---

### Post by Polygon on 2007-02-03
no, its the same thing as putting it on your panel, it just automatically logs me out.

---

### Post by Polygon on 2007-02-07
If anyone google for this problem, this is how i fixed it:

I just deleted the following folders from my home folder

.gconf
.gconfd
.gnome
.gnome2
.gnome2_private

I knew it was a problem with gnome's configuration as the quit button worked in other logins, so i just these folders to try to reset the configuration

**_BUT:_** after you do this, when you login, your wallpaper, panels and maybe any configuration for any gnome programs will be gone. You just need to recreate your panels (right click > new panel and to re add the applets: right click > add to panel )

---

### Post by microsafe17 on 2007-02-14
Thanks for pointing me in the right direction, but you're fly-swatting with a sledgehammer there.

I was having the same problem, and there is a much simpler fix.

Alt-F2 to bring up the run window.
gconf-editor
/apps/gnome-session/options
put a check in the box for Show Splash Screen.

I don't know how this setting got updated in the first place, but I checked the box, had to restart the session once (I hit the quit button to see if it was already fixed, which of course logged me out) but the next time the button was working as it was supposed to.

Thanks again for the tips, figured I would post the exact fix for people that didn't want to lose all their configurations.

---

### Post by tetralis on 2007-06-09
Well was not enough in my case just to check the box for Show Splash Screen.

However while you are still in gconf-editor
Go back into /apps/gnome-session/options
Put a check in the box for logout_prompt

Now it's working for me :popcorn:

---

### Post by corefile on 2007-11-26
yep I had the same problem and this fixes it for me as well. I just checked the logout_prompt and that fixed it.

---

### Post by tanas on 2007-11-26
logout_prompt was enough for me as well.

(BTW, I think that what caused me the problem in the first place, was playing around with Ubuntu Tweak, without knowing exactly what I was changing.)

---

