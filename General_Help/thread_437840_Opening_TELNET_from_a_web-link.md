---
title: "Opening TELNET from a web-link"
date: 2007-05-09
forum: General Help
---

### Post by Mr. Brownstone on 2007-05-09
In Windows I could click a link that was prefixed with telnet:// and my default TELNET program (PuTTY) would open it.

How can I do this in Ubuntu? Firefox complains that the protocol (telnet) is not associated with any program.

Many thanks.

---

### Post by Mr. Brownstone on 2007-05-10
Has anyone done this? Thanks. :)

---

### Post by asipi on 2007-05-10
the howto is browser dependent, what browser do you use?
the "key" is external protocol handling... the easiest in opera

---

### Post by Mr. Brownstone on 2007-05-10
Thanks for the reply. I use Firefox.

---

### Post by asipi on 2007-05-10
ok for firefox it is also not too difficult...
open a new tab and type in the url address field about:config
it will bring up the configuration page of firefox

you have to create 2 new line.
on an empty space on the page right-click and choose** 'New->logical'**
the name of the new key should be: **network.protocol-handler.external.telnet**
value should be: **true**

again on an empty space on the page right-click and choose** 'New->string'** (or could be other, I use FF in my native language but my tip is string ;) )
the name of the new key should be: **network.protocol-handler.app.telnet**
value should be: **/path/to/your/favorite/telnet/application**

that's all :)
simple, isn't it?

---

### Post by Mr. Brownstone on 2007-05-15
Simple when you know how indeed. :D

Thanks a lot for that, I managed to use your advice to run a BASH script that pulled out the "telnet://" part of the address before passing the IP to gnome-terminal. (It seems that leaving it in causes problems.)

Here is the script if anyone else is interested:```
#!/bin/bash
gnome-terminal -e "telnet ${1##telnet://}"
```

---

