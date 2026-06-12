---
title: "login screen won't boot, just a spinning cursor"
date: 2007-09-09
forum: General Help
---

### Post by TheOnlyEnglishRose on 2007-09-09
Yesterday I changed the login screen theme, and I guess I didn't let Ubuntu do its thing when it was shutting down, so now all I get is the swirlly cursor thing when it is booting up. I just want to revert it back to the original login in screen, or so I can make my acount auto-login, so I can bypass GDM. Then I can go to System->Administartion->Login Window

What do I need to do? I can go into the recovery console but I can't do 'startx' unless I am root. When I do it on my account I get: 'User Not authorized to use X' and it goes on about how it can't write .Xauthority

---

### Post by TheOnlyEnglishRose on 2007-09-09
update: I now can write .Xauthority, however I am still not allowed to 'startx' unless I'm root

the real prblem seems to be the fact that I screwed up GDM.

---

### Post by LoD94 on 2007-09-10
type ```
sudo -i
``` to get in as root user.. :tongue:

---

