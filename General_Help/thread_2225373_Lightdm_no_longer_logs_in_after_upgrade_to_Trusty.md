---
title: "Lightdm no longer logs in after upgrade to Trusty"
date: 2014-05-21
forum: General Help
---

### Post by jeff63 on 2014-05-21
I've just completed a somewhat fraught upgrade to Trusty (from Quantal), and I can no longer long-in via lightdm. When I try with correct credentials, the screen goes black with some text for a fraction of a second, then dumps me back to the login screen as though I'd never tried to log in. Incorrect passwords behave as expected - it just rejects them exactly as it should.

I normally use gnome classic, but this problem occurs similarly with all other environments I have installed (unity, xfce, xmonad). If I just use startx from another TTY, it starts fine (albeit obviously without any interface bars).

I've worked around this by uninstalling lightdm and installing gdm, which logs in fine. At some point, I'd like to go back to lightdm, if possible (this is the default, if I recall correctly?). I've tried reconfiguring and reinstalling a number of packages, but this hasn't helped.

As part of the upgrade procedure, I moved away from nvidia's own software to nouveau, but I don't think this is part of the issue.

I couldn't find anyone with the same symptoms using the forum search - has this been a problem for anyone else?

edit: And I totally intended to post this in the 'upgrades' forum but I guess I got moved out of it by my search.

---

### Post by mastablasta on 2014-05-21
i installed from minimal iso (netinstall). and couldn't get lightdm to work. gdm worked fine. i installed xfce and i3. in the end i made it with Slim. so if lightdm is really not working slim is kind of nice and light.

---

