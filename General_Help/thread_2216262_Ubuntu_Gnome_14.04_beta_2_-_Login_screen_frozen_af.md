---
title: "Ubuntu Gnome 14.04 beta 2 - Login screen frozen after zoom enabled accidently"
date: 2014-04-10
forum: General Help
---

### Post by simon28 on 2014-04-10
Hi,

My release is fully updated/upgraded as of about 1 hour ago from this post.

I'm a web developer and I've been using Ubuntu in general for over 2yrs, although currently I've been using Ubuntu Gnome 14.04 for about 3 weeks now with no big issues.

However, recently i accidently clicked zoom in the universal access dropdown menu on the login screen with a spastic mouse click, i tried to hit alt+super+8 to stop it with no success, the login screen froze so i went to tty1 and restarted the system.

Amazingly (and quite stupidly i might add) the login screen was still on zoom and all i could see was the gray background with a big arrow in the middle that wouldn't move.

So (in another terminal instance) i tried going to /usr/share/gnome-shell/js/ui/ and renamed the magnifier js files hoping it would just boot and skip the usage of the magnifier altogether, however (much not to my surprise) that didn't work it just sat there hanging during boot up, so i set the files names back to their defaults and now i'm back at square one.

I have also tried (to no avail) which use to work on older versions of ubuntu but not good ol' Trusty. :)
```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
```

I have a bunch of work to do at the moment and my system is quite heavily customized, so I'm not interested in reinstalling and i would also like to figure this out in the possible event of it occurring again sometime in the future.

Any helpful assistance will be appreciated :) thanks.

edit: i also tried *rm .gnome .gnome2 .gnome3 .gconf .gconfd .metacity -rf*
in an effort to reset the settings.

---

### Post by simon28 on 2014-04-11
Close thread please, solved by removing/purging and reinstalling GDM

---

