---
title: "Missing window decorator after upgrade (not Beryl related)"
date: 2007-04-19
forum: General Help
---

### Post by _davidh on 2007-04-19
Hey.

(This is possibly the wrong forum, just move it if that's the case.)

I upgraded from Edgy to Feisty today, and it went really smooth. However, window decorations doesn't show up anymore. This is a problem that often relates to Beryl. I don't think this is the case though, since I get the same thing when using metacity (i.e. choosing GNOME in the session window on the login screen). I've also uninstalled Beryl just in case.

If I add another user and log in with that, the window decorations show up, so there must be some setting that applies to my old user that messes things up.

Does anyone have an idea of what could be the problem here? Just tell me if you need more information.

Big thanks in advance.

---

### Post by autocrosser on 2007-04-19
Have you used Compiz in the past? Desktop Effects now uses Compiz & a old .conf could really mess it up.

---

### Post by _davidh on 2007-04-19
Hi autocrosser. Thanks for your answer.

I've used Beryl before, but I've deleted all Beryl-related directories in my home directory. Also, I haven't enabled desktop effects.

---

### Post by autocrosser on 2007-04-19
The places I'd look for any lingering beryl conf info:
.gconf .gconfd .gnome .gnome2 .gnome2_private & .gnome_private

I would just create another user & then compare what is in those files.

---

### Post by _davidh on 2007-04-20
Thanks again for your anser. I searched thorugh my home directory for "compiz" and "beryl", and deleted everyhing related, but the problem persists.

I'm thinking about making a new user and copy everything I need from the old.

---

### Post by kripkenstein on 2007-04-20
_davidh, I am having a similar problem, perhaps it is related. I filed a bug here: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107947]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107947").

I am on a *fresh* install of Feisty, no Beryl/Compiz/etc. at all. The NVidia binary driver causes metacity to not be loaded (only after 2 reboots, oddly). The simple solution is to run "metacity" from a terminal, but it needs to be done each time I log in. Also the resolution is not detected right.

I don't have this problem without the NVidia binary driver, so I suspect it is related to that. _davidh, are you using NVidia, and if so, the binary driver?

---

### Post by _davidh on 2007-04-20
Hi kripkenstein. Thanks for your answer.

Nope, I'm using the ATI binary driver. When I try to execute metacity, it says "Segmentation fault, core dumped". So maybe this is my problem -- that metacity somehow can't start. Anyone knows what metacity-related config files I could check/delete? Thanks in advance.

---

### Post by _davidh on 2007-04-20
Yay! I got it working,

I first deleted everything in ~/.gconf/apps/metacity/ except %gconf.xml and general/%gconf.xml. This step was probably not necessary.
I then deleted all themes in ~/.themes/. I then restarted X. When logging in, I got a warning that nautilus couldn't start or similar. Also, I had some default theme. I then chose another theme, logged out, logged in, and now it works :)
So, it probably had something to do with metacity trying to load some theme component that wasn't available.

Thanks everyone that tried to help. Really appreciated.

---

