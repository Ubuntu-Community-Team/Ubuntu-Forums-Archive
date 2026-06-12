---
title: "[SOLVED] Keyboard config at login."
date: 2008-02-29
forum: General Help
---

### Post by Sportingfan on 2008-02-29
Hi,

I don't know why, but suddenly my keyboard configuration changed. I could not login into ubuntu because for some reason my keyboard config had changed from azerty to qwerty. When i managed to login, i changed the keyboard config back to azerty. The probleem seemed to be solved.
Now i just had the same problem, with the difference that the keyboard was configed azerty after login.
For some reason i have another keyboard config at login.

Solution?

ty

---

### Post by banewman on 2008-02-29
If you open the control center you should be able to set the default keyboard - have you tried this?

---

### Post by brabo on 2008-02-29
hi,

i had the same issue.
you should do : gksu gedit /etc/X11/xorg.conf
then go to  Section "InputDevice"
there you need to change Option		"XkbLayout"	"US"
to whatever sort of azerty you're using. ex "be"
then, after logout (or reboot, not sure)
it should be azerty. after login you'll get a message stating the keyb layout from xorg is different , you should erm (thinking) use xorg settings.
after that, it'll be fine.

but: if you login through a shell, it'll still be qwuerty.
for that you need to change /etc/default/console setup too

grtz,
brabo.

---

### Post by Sportingfan on 2008-02-29
> **brabo said:**
> 
there you need to change Option		"XkbLayout"	"US"
to whatever sort of azerty you're using. ex "be"


That did it. Thanks.

---

