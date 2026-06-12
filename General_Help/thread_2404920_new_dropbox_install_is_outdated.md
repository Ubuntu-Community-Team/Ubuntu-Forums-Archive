---
title: "new dropbox install is outdated"
date: 2018-10-30
forum: General Help
---

### Post by pratik-kanjilal-p on 2018-10-30
I run Dropbox on an unencrypted ext4 drive in Lubuntu 18.04, 32-bit. A few weeks ago, Dropbox started popping up a warning, saying that it was outdated and could not be used further without an update. I purged and reinstalled from nautilus-dropbox in the repo. The popup was back. Purged again and reinstalled from the .deb on the Dropbox site. Popup back. Noticed that both are the same version: 2015.10.28. 

Does anyone else have this problem? I know that Dropbox has withdrawn support to Linux. Something to do with that? But it shouldn't just stop working.

---

### Post by Holger_Gehrke on 2018-10-30
That version - 2015.10.28 - is exactly what is offered for download on dropbox.com. And they haven't withdrawn support, they only said they would not support anything but unencrypted ext4 filesystems - citing the need to use the extended attributes as part of the file-signatures for the decision what needs syncing and what doesn't.

---

### Post by pratik-kanjilal-p on 2018-10-30
Right, conditions are met, so why does it keep telling me to update, and the update won't run? Could my system be reading it as an older version because of residual files? What's the way to delete everything?

---

### Post by castor_fou on 2018-10-30
Just checked I use version 60.4.107.

---

