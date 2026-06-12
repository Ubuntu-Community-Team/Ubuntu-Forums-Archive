---
title: "NVU Browse button"
date: 2006-10-10
forum: General Help
---

### Post by Trippy on 2006-10-10
Hi,

Aplogies if this has been asked before but....

When I click on the 'browse' button in NVU to view my page in a browser, nothing happens. No errors no browser, nothing.

It's not life or death I know, just annoying. Is there a nice fix for this?

I have a nagging feeling there is a config file that needs to be told what browser to start...

I'm using version 1.0 of NVU running on Ubuntu 6.06 on an Athlon 64 x2.

Thanks folks!

---

### Post by nantetokuma on 2006-11-05
Hello,

I was looking for this too and I've find a solution. It's working for me, hope it will for you...

I've look in files installed by Nvu in Synaptic and i've read content of this one : /usr/lib/nvu-1.0/defaults/pref/all.js

the last lines are :
pref("network.protocol-handler.app.http", "/usr/lib/mozilla/mozilla-ext");
pref("network.protocol-handler.app.https", "/usr/lib/mozilla/mozilla-ext");
pref("network.protocol-handler.app.ftp", "/usr/lib/mozilla/mozilla-ext");
pref("network.protocol-handler.app.file", "/usr/lib/mozilla/mozilla-ext");

pref("spellchecker.enablerealtimespell", false);
pref("spellchecker.realtimespell.warning_color", "orange");
--------------------
so I made a copy of it and edit:

[INDENT][COLOR="Blue"]cd /usr/lib/nvu-1.0/defaults/pref/[/COLOR][/INDENT]
[INDENT][COLOR="Blue"]sudo cp all.js all.js.old[/COLOR][/INDENT]
[INDENT][COLOR="Blue"]sudo gedit all.js[/COLOR][/INDENT]

I've change the last lines to replace [COLOR="Blue"]/usr/lib/mozilla/mozilla-ext[/COLOR] by [COLOR="Blue"]/usr/lib/mozilla-firefox/firefox[/COLOR]
for the network.protocol-handler.app.http and https. Don't know for the moment for ftp and file. Restart Nvu, It should work fine... that's all:-D

---

### Post by Dr. C on 2006-11-09
Thanks for the info. I had that same problem and it now works fine. 

One should also make the change for the ftp and file protocols. The Nvu configuration file was pointing to a non existent file in Dapper and Edgy, looking for a non existent browser. Check your /usr/lib/mozilla/ directory. :-D

---

