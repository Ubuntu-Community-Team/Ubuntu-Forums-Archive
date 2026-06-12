---
title: "Problem Installing Adobe Flash Player Firefox 3b5"
date: 2008-05-07
forum: General Help
---

### Post by unforeseen_incident on 2008-05-07
Hello everyone, im new in this neck of the woods and im having trouble getting Flash to work on my ubuntu machine with Firefox 3 beta 5.


automatic installation gives this error:
> Firefox could not install this item because "install-nti..rdf" (provided by the item) is not well-formed or does not exist. Please contact the author about this problem.

manual copy and pasting of libflashplayer.so to:
/usr/lib/mozilla/plugins
/usr/lib/mozilla-firefox/plugins
/usr/lib/firefox/plugins
/usr/lib/firefox-3.0b5/plugins

has no effect.

[PHP]about:plugins[/PHP]
shows NO installed plugins.


flash player works fine in Firefox 2 (when i uninstalled ff3)

ive done some searching and tried most things people have suggested

any ideas?

---

### Post by wrgb2 on 2008-05-07
Are you installing flashplugin-nonfree using Synaptic - this is usually the easiest way to get flash working.

---

### Post by unforeseen123 on 2008-05-08
[SIZE="7"][COLOR="Red"]SOLVED:

[/COLOR][/SIZE]

create directory:
/home/[username]/.mozilla/plugins

copy libflashplayer.so to
/home/[username]/.mozilla/plugins

restart firefox


plus, can anyone please tell me why i cant log back in? the site deletes my password from the form before it sends it and so it wont log me in!
thanks!

---

