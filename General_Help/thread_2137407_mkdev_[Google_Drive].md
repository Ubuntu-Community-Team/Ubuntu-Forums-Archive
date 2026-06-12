---
title: "mkdev [Google_Drive]"
date: 2013-04-20
forum: General Help
---

### Post by arvevans on 2013-04-20
There seem to be several slightly different network drive tools, from NFS to Grive <https://github.com/Grive/grive> but it seems to me that the whole thing of cloud drives could be simplified for users.
[LIST]
[*]mkdev builds a device with major and minor node binarys in /dev/.....
[*]Could an extension be built for mkdev that links to handlers for various type of network connected devices, such as Google Drive, JoliCloud Drive, and possibly even connected to Lunix Repositories to make them appear as mounted drives.  /dev/sdg = Google Drive, /dev/sdr = Repository Drive, etc.
[*]This is a departure from mounting drive systems through mount, fstab, etc., but might be an interesting way for simplifying connections to external file type entities.
[*]
[/LIST]
Of course the UNIX purists will complain that this is not the way it is done, but just maybe it could be seen as an improvement in the way it is done.

Arv
_._

---

### Post by arvevans on 2013-08-07
.

---

