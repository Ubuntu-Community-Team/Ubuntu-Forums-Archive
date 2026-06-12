---
title: "[SOLVED] File Associations Broken/Confused URGENT"
date: 2008-06-20
forum: General Help
---

### Post by oronte on 2008-06-20
I'm in dire trouble here. I'm not sure what happened but nothing seems to open correctly. Initially nothing would open. When I right click on files I can choose which application to open them with. Some of them stick .odt and .doc for example now correctly open in Openoffice, but when I right click most files it says: "open oz.pdf (or whatever the filename is) and other files of type "plain text document" with:" and it does this for mp3, pdf, txt, jpg, flv - it seems to identify them all as plain text documents, so whatever application I choose, all of them open with that application, until I change it. Then they all open with whatever new application I choose. Once I choose the correct application those files do open, except for pdf's, Evince gives the error code: "Unhandled MIME type: &#8220;application/octet-stream&#8221;" While I can't move in the directory (use left and right) in Eye of Gnome when opening jpg. 
Everything was working just fine earlier today. All I've done today was install the update for Rhythmbox and I installed Gdesklets (which I've now uninstalled). I shut down my PC and when I started up I used Brasero for the first time to burn a DVD and upon opening it, Brasero said that it wasn't the default application for burning DVD's and would I like to make it the default, I said yes. Thereafter when I began to browse my files in Nautilus I discovered this problem (I've not done or changed anything to Nautilus or any other applications today). In Nautilus I can see previews of pdf's and jpeg's only. All other files either have a text preview or the blue diamond that applications have.
I'm using 64 bit Hardy Heron.
Please, please help!

---

### Post by robklg on 2008-06-20
I don't know what you did, but sounds ****** up :)

Maybe you need to reset your settings. Probably it's just one little setting, but it's faster this way. As long as you don't have too many things customized.

Login and open a terminal...

Then:

mv .gconf .gconf-backup; mv .gconfd .gconfd-backup

Now log out, and log back in... all such settings will be reset to default... i hope :)

---

### Post by oronte on 2008-06-20
> **robklg said:**
> I don't know what you did, but sounds ****** up :)

Maybe you need to reset your settings. Probably it's just one little setting, but it's faster this way. As long as you don't have too many things customized.

Login and open a terminal...

Then:

mv .gconf .gconf-backup; mv .gconfd .gconfd-backup

Now log out, and log back in... all such settings will be reset to default... i hope :)

While all my settings were reset, unfortunately this didn't help. Thanks anyway. The problem continues as described above. All files are still recognised as plain text. Except odt and doc which were the first ones I changed.

---

### Post by oronte on 2008-06-20
All right I managed to solve this one myself (thankfully). For anyone else who might have a similar problem:
I went to Synaptic, search for 'mime'. There were five packages that were already installed with the word mime in them. I marked all five for reinstallation and clicked on apply. I rebooted and problem solved.

---

### Post by robklg on 2008-06-21
Ok good thing...

You did put back your settings right? As you only moved .gconf en .gconfd... you can get back your settings...

---

### Post by oronte on 2008-06-21
Oh great! Thanks, didn't know that. Certainly helps. Thanks for the advice.

---

