---
title: "Firefox Human Theme not working after update"
date: 2007-01-03
forum: General Help
---

### Post by lwr on 2007-01-03
The firefox-themes-ubuntu package says that all its themes aren't compatible with the latest update of Firefox (2.0.0.1). Can anybody tell me a work-around, or does anyone know if this is going to be fixed soon? The firefox-webdeveloper package doesn't work either, I don't think, but that hasn't worked for a long time. It's good to see the official Firefox icons back, though.
Thanks for your help

Luke

---

### Post by infinito on 2007-01-03
You should edit as root these files:
```

/usr/lib/firefox/extensions/{4a17b103-e896-4390-b049-b5f7eb9d6dfa}/install.rdf
/usr/lib/firefox/extensions/{9552e588-53f2-41ba-a0f4-7c6e4bf8d973}/install.rdf
/usr/lib/firefox/extensions/{293a8960-9d78-4a30-9539-b70591e32e17}/install.rdf
```

And change the line that says:
```
<em:maxVersion>2.0</em:maxVersion>
```

with something like:
```
<em:maxVersion>2.1</em:maxVersion>
```


This will help you 'till the package is updated properly...

---

### Post by justinjstark on 2007-01-03
Thanks, infinito.  That fixed the problem.

---

### Post by lwr on 2007-01-03
Thanks for your help infinito. Unfortunately it's not working, but if I do gksudo firefox, then it works fine. Any idea how to fix this? Thanks

---

