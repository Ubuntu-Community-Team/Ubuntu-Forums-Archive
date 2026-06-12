---
title: "Ubuntu 8.04 Firefox fails to open aim: links"
date: 2008-06-05
forum: General Help
---

### Post by rlandrum on 2008-06-05
I'm having trouble with Firefox and Pidgin.  I migrated from 6.06 to 8.04 a few weeks ago, and since then have been trying to figure out how to get firefox to launch a new IM window (or tab) in Pidgin.  Previously, gaim used a remote control utility, but I have yet to find one for pidgin.

Suggestions?

---

### Post by rlandrum on 2008-06-05
Ah-ha!  I figured it out...  Install libpurple-bin which contains purple-url-handler.  In firefox, open Preferences -> Applications and select aim, and modify it to use /usr/bin/purple-url-handler.

I also added a protocol handler in about:config for network.protocol-handler.app.aim with the value /usr/bin/purple-url-handler.  This step may not be required.

---

### Post by dustigroove on 2008-08-25
I am running Firefox 3.0.1 under Hardy and had been banging my noggin trying to figure this out. Unfortunately the solution wasn't as simple for me as your post, for some god-forsaken reason the applications are not listing in my Firefox preferences window, but it at least gave me a clue as to where to make my changes. I just manually edited the mimeTypes.rdf file to include the following:

[PHP]  <RDF:Description RDF:about="urn:scheme:externalApplication:aim"
                   NC:prettyName="purple-url-handler"
                   NC:path="/usr/bin/purple-url-handler" />[/PHP]

Cheers

---

### Post by dustigroove on 2008-08-26
Also, feel free to mark your post as "Solved" under the "Thread Tools" drop-down! ;-)

---

