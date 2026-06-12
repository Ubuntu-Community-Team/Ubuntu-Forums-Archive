---
title: "Strange rebooting..."
date: 2006-09-02
forum: General Help
---

### Post by applechewer_ on 2006-09-02
Hi everyone.

I've been using Ubuntu for a few months now, but there's one thing which is starting to annoy me a whole lot.  If I leave my PC on overnight, about 80% of the time I find the log in screen instead of my desktop when I return.

I can't work out whether the computer is rebooting or if it's just logging me out, but either way it's very frustrating, especially if I've left it downloading something.

Does anybody have any idea what might be causing this?

Thanks! :)

Jonny

---

### Post by ayoli on 2006-09-02
are you sure this is a complete reboot and not just X that crashes ? have a look to your /var/log/syslog, check the boot date/time.
Are you using compiz with xgl or aiglx ?

---

### Post by crane on 2006-09-02
Also check you screen saver settings. Make sure you do not have lock screen when screensaver starts selected.

---

### Post by christhemonkey on 2006-09-02
Are you sure its not just going to screensaver or something and then when it resumes, it resumes to login screen?


Seem to remember there being an option about this somewhere...

---

