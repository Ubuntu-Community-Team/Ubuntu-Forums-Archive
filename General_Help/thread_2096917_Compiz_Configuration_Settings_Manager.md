---
title: "Compiz Configuration Settings Manager"
date: 2012-12-21
forum: General Help
---

### Post by Fuser77 on 2012-12-21
Hi there!

I'm new to Ubuntu.

After installing the Compiz Settings Manager and playng around a little bit (I didn't do that much actually...) the apps bar disappeared from my desktop.
This happened only with my main user, which is also the administrator;  with the other users I still have access to the bar.

Please help, I don-t know how to roll back and  can't access any application, included Compiz!!!

---

### Post by JRV on 2012-12-21
Press <CTRL>-<ALT>-T to open a terminal and try these commands:

```

sudo dpkg-reconfigure compiz

```

and/or

```

unity --reset

```

---

