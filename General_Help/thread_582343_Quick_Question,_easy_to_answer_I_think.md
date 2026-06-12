---
title: "Quick Question, easy to answer I think"
date: 2007-10-19
forum: General Help
---

### Post by AnthoMacP on 2007-10-19
I just did my fresh install of gutsy and I'm reinstalling all my commonly used apps. I reinstalled Deluge, my torrent client, but firefox doesn't recognize it as being installed and doesn't put it in the options list to open .torrent files automatically. I'm well aware that i can save the .torrent to my hd and launch it manually but i'd much rather have deluge open itself and load the torrent. Is there any way that I can either edit the command firefox uses manually or can someone direct me to the location of where the deluge client is actually installed so when i click "other" i have somewhere to tell firefox to go? Thanks.

---

### Post by oldos2er on 2007-10-19
If you used aptitude or Synaptic Package Manager to install Deluge, Synaptic can also tell you where the files in the package "go." Open Synaptic, click Status, then 'Installed.' Find the package (e.g. Deluge), click 'Properties,' then 'Installed Files.'

 Hope this helps.

---

### Post by DagMan on 2007-10-19
Isn't there a selection to open or save, and also a thing you can navigate to the program to open it with, and a checkbox for always to use the action, when firefox pops a prompt for a downloadable file?

If that doesn't work out then try maybe file->prefernaces then the content tab and the manage button.  Hopefully .torrent files will be in there but if not then try setting it as in the first paragraph and then go here to edit it again.

The only thing I'm not sure about is if deluge is a modular thing that deluge itself isn't what needs to open it or another script which it calls, but I don't have it installed to see.

Good luck

---

### Post by AnthoMacP on 2007-10-20
Thanks, that fixed it, it was listed in the Properties of the install in Synaptic :) thanks!

---

