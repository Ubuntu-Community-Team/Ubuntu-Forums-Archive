---
title: "Uh oh, corrupted GDM Splash / login"
date: 2008-02-19
forum: General Help
---

### Post by deepee111 on 2008-02-19
I really messed up this time. In an effort to customize the GDM splash a little bit, I seem to have inserted some invalid XML and pooched it. Now when Ubuntu loads, it tells me that the greeter has an error and that it will try to use another, but it seems to just keep loading the one I've corrupted.

Any help would be GREATLY appreciated, as I can't login or use my system. Thanks in advance.

---

### Post by pointone on 2008-02-19
You can boot into recovery mode and try to recover the damage you've done from the command line. I don't know what you mean by the "GDM splash", but poking around in /etc/gdm/gdm.conf may be of help if you can't repair the damage directly.

---

### Post by deepee111 on 2008-02-19
Not quite, but thanks for the tip because it lead me to the answer. 

I renamed the theme folder in /usr/share/gdm/themes (referenced in the file you mentioned) in order to create a "not found" error, and Ubuntu defaulted to another theme.

---

