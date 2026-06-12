---
title: "Azureus + WebUI Command line installation?"
date: 2007-08-19
forum: General Help
---

### Post by justino on 2007-08-19
Hi All,

I've finally managed to get Ubuntu Server (7.04) installed on an old Sun Netra T1 rackmount server.  The machine has no video / keyboard / etc, but I have ssh access to it (which is a start) but since there is no video I cannot access anything through the GUI (not that I want to really since it's just going to sit behind a bookcase and do some of my downloading / file storing tasks).

I had it setup using torrentflux (which uses bit tornado) as a webui that I could access my torrents from, but it just doesn't seem to want to work well (refuses to work with torrents that are not heavily seeded for some reason).  I've found that azureus has a webui plugin but all of the guides that show how to install it don't include a way to do so without a GUI.

(The reason I want to have the webui is so that I can access it from work and monitor things - gotta keep busy somehow. :))

Does anyone know of a way to install azureus's webui plugin and configure it without a gui?

Any suggestions would be helpful. Thanks!

Justin

---

### Post by jpkotta on 2007-08-19
I've never been able to get the WebUI to work, not completely anyway.  If possible, the easiest way is probably to configure on a machine with a GUI and copy the config to the server.  

Neither Azureus nor WebUI need a GUI to install.  You can get Azureus from  the repos and installing WebUI is a matter of copying some files to ~/.azureus/plugins.

[http://www.azureuswiki.com/index.php/Console_UI](http://www.azureuswiki.com/index.php/Console_UI)

Also, you may want to try rtorrent.

---

