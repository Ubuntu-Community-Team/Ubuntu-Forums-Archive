---
title: "Firefox backspace not working"
date: 2008-05-07
forum: General Help
---

### Post by wconstantine on 2008-05-07
How do I get it to work? It's supposed to go back one page when pressing the backspace button. :(

Edit: NVM. Got it working.

---

### Post by danwood76 on 2008-05-07
You can enable this in the config.

in the address bar type:
```

about:config

```
and search for
```

browser.backspace_action

```
(I think)
set this value to 0 and that should fix it for you.

---

### Post by _sAm_ on 2008-05-07
Type “about:config” in the address bar of Firefox and press Enter.
`Filter` for ‘browser.backspace_action’ and change its value to 0 (zero).

From: [http://ubuntu.wordpress.com/2006/12/21/fix-firefox-backspace-to-take-you-to-the-previous-page/](http://ubuntu.wordpress.com/2006/12/21/fix-firefox-backspace-to-take-you-to-the-previous-page/)

I just tried and it works fine.

---

### Post by hpat on 2010-11-28
> **danwood76 said:**
> You can enable this in the config.

in the address bar type:
```

about:config

```and search for
```

browser.backspace_action

```(I think)
set this value to 0 and that should fix it for you.
Thanks for the help. It has worked for me

---

