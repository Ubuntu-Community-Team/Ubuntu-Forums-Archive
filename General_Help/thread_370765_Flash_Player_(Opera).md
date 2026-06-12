---
title: "Flash Player (Opera)"
date: 2007-02-26
forum: General Help
---

### Post by Nitrofire on 2007-02-26
Ive downloaded Flash and it works in Mozilla Firefox but doesnt in Opera even though on the site it says it will give me an option to install to Opera. How can i install it to Opera?

---

### Post by michaelp on 2007-02-26
Copy "libflashplayer.so" to '/usr/lib/opera/plugins/'. Flash should now be detected when you start Opera.

You can also add Mozillas plug-in path to Opera:
'Tools > Preferences > Advanced > Content > Plug-in options... > Change path...'

---

### Post by olavjunior on 2007-02-28
Perfect!
Thanks!

---

### Post by tophue on 2008-04-28
I keep getting access denied messages when trying to copy "libflashplayer.so" Also It doesnt detect anything when I redirect the plugins to the firefox plugins folder. Any Ideas?

---

### Post by GnarusLeo on 2008-05-06
You have to be root :) the cmd should be

```
sudo cp libflashplayer.so /usr/lib/opera/plugins
```

---

