---
title: "GNOME terminator, 10.04"
date: 2014-12-11
forum: General Help
---

### Post by david.aldrich.ntml on 2014-12-11
Hi

I have just started running GNOME terminator on Lucid.  From within a terminator session, the TAB key is not working as expected.  I checked:

> echo $TERM
xterm

Should that value be 'terminator'?

If so, where should I set it?

Best regards

David

---

### Post by Impavidus on 2014-12-11
I don't use terminator myself, but I guess it just tells the program running inside that it is xterm compatible. My xfce4-terminal also replies with xterm. You may be able to change it from the terminator settings.

Terminator is a GUI program and not part of the server release of Ubuntu. Therefore, 10.04 Lucid Lynx is unsupported, meaning both that we no longer support it and that upgrades to the server packages are no longer checked for compatibility with the desktop packages.

---

### Post by nerdtron on 2014-12-11
Running Xubuntu 14.04 here with latest Terminator from the repos.

```
~$ echo $TERM
xterm
```

> the TAB key is not working as expected.

Give us an example on when is the tab key not working as expected.

---

