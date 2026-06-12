---
title: "On reboot, Deluge shows all downloads at 0%"
date: 2014-01-05
forum: General Help
---

### Post by Michael_Kearney on 2014-01-05
Not 100% sure on the location to post, but here goes.

Whenever the computer reboots, all downloads show being at 0% and will begin downloading from 0% even though most are done. If I select one or all and tell it to force recheck, it doesn't respond. I can tell it to "move storage" to the location where they are, and then I can tell it to re-check and it will find them and figure out where it left off.  But if I reboot, it's as if it has forgotten where all the files are.

I had changed the directory for downloads, because I was using an external, and replaced it with an internal drive. The external drive I had mounting to an alternate location, because of Plex, which would not catalog files on USB (but that's not an issue anymore). It feels like Deluge keeps trying to look in the old location, which doesn't exist anymore. I feel like it should remember, when I tell it to "move storage" to a new location, that all my files are there.

I have tried uninstalling, purge, and reinstall deluge, but even when I do that, it does the same thing, still has all my settings and downloads listed as they were before, which I feel like shouldn't happen with purge. I'm not really sure what to do other than switch to another torrent client, which isn't a big deal really but I am just used to Deluge.

Thanks

---

### Post by nerdtron on 2014-01-05
I'm not using deluge, but most programs such as firefox have a hidden folder in your home directory, it is .mozilla or .firefox folder. Maybe deluge has a hidden folder to like .deluge or something.
It is important to delete/rename/move this folder after you do apt-get purge. This will ensure that when you reinstall the program, all setting will be reset to default.

---

### Post by monkeybrain20122 on 2014-01-05
It may be because it saves unfinished downloads to /tmp so they are gone on reboot, I have experienced the same problem with qbittorrent a while back, just changed the directory to Downloads and that fixed it. I don't have deluge so can't check, there should be some settings to choose where incomplete downloads are saved.

---

