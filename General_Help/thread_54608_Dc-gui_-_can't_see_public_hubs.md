---
title: "Dc-gui - can't see public hubs"
date: 2005-08-05
forum: General Help
---

### Post by Hanj on 2005-08-05
I've been trying for some time to get direct connect to work under linux, but so far no luck. First I tried using DC++ with wine, and that worked, but crashed so frequently that it wasn't usable. So now I've been trying to get Dc-gui to work, but I'm having problems.

I've filled in all my info and tried both active and passive mode, but the public hubs list is completely blank. It seems there is some problem with getting the hublist, since every time I click "Public", I get this output:

"HUBLIST: 'http://www.hublist.org/PublicHubList.config.bz2'
[http://www.hublist.org/PublicHubList.config.bz2](http://www.hublist.org/PublicHubList.config.bz2) ignore because 'bzip2' is not available"

I have the package bzip2 installed, so I can't understand why it won't find it.


PS. I tried using Dc-gui-qt too, but it wouldn't work. Every time I entered my settings it would ask me to restart the program, and when I did so the settings were all blank. Solutions to that problem would also be appreciated.

---

### Post by c4pp4 on 2005-08-08
try the thread from NeoChaosX -> message 04-01-2005, 10:41 PM [dcgui-qt options reset](http://ubuntuforums.org/showthread.php?t=21570)

---

### Post by jazzgossen on 2006-01-31
I can't see any public hubs either, and I can't delete the configuration as mentioned in the above post either. I don't have a ~/.dc folder, only ~/.dctc, and deleting that doesn't help.

When I look at the "public" tab under the "connect" tab, everything is blank. If I run dcgui from the terminal, I get the following output when clicking the "public" tab:

Processing: [www.neo-modus.com](www.neo-modus.com)
successful end: [www.neo-modus.com](www.neo-modus.com)

But nothing else happens.

Does anybody actually use dcgui?

Edit: oops, this should be in the Breezy forum.

---

### Post by joewhite on 2006-05-03
RevConnect crashes in Wine. Valknut is far too slow with a couple of hubs open. Linux DC++ doesn't allow multisource downloading and DCGui won't even download the hublist. I would like to use DCGui but I cannot find the problem. Does anyone actually have DCGui working or should I just give up? I'm afraid to admit it but this is one major thing that is tempting me to go back to Windows.

---

