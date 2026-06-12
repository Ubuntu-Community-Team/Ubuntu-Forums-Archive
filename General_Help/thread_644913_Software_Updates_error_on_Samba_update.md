---
title: "Software Updates error on Samba update"
date: 2007-12-19
forum: General Help
---

### Post by portabill on 2007-12-19
Ubuntu 7.10 x86
Dell Latitude D505

This morning I allow the Software Updates to run.  Seven installed fine, but the update for Samba had an error.  Unfortunately I didn't get the first error.  On a following attempt to install the update, Update Manager said that the software index is broken and suggested that I run sudo apt-get install -f or Synaptic.  I tried both and get the error "failed to delete `/usr/lib/samba/vfs/readahead.so.dpkg-tmp': Permission denied".  I do a listing of /usr/lib/samba as root and get "?--------- ? ? ? ?                ? vfs".  This happens with Samba running and stopped.

Thanks!

---

### Post by portabill on 2007-12-20
Sorry if this is too soon to bump.

---

### Post by portabill on 2007-12-21
Not sure how it all works together.  My laptop went into its 30x startup fsck, had to correct a bunch of stuff.  Then the apt-get install -f worked.  Did the update fine.  Did apt-get install samba fine, which kept my smb.conf.  Everything seems fine now, I hope.  :)

---

