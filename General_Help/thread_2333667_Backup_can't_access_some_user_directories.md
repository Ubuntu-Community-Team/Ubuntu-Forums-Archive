---
title: "Backup can't access some user directories"
date: 2016-08-12
forum: General Help
---

### Post by Peter_Horn on 2016-08-12
Ubuntu 16.04LTS 64bit desktop (but it also happened under 14.04LTS 32bit)
I have the standard backup settings, daily option. It's a local backup at the moment, until I get my server set up with RAID etc. Every day I get a popup that it can't back up these:
/home/peter/.cache/dconf
/home/peter/.config/mc/mcedit
/home/peter/.dbus
/home/peter/.local/share/mc/mcedit

I have ~/.dbus and ~/.cache/dconf in my "Folders to ignore list" but that doesn't seem to carry any influence. (I haven't bothered with the mcedit stuff because I'm sure that won't help.)
All relevant permissions are as per default setup.

I've seen other discussions of this issue, where the suggested fixes involve chmod'ing to add permissions till it goes away, but I am not happy with that idea. I'd much rather whatever hidden engine does the backups would respect the ignore list.

Peter

---

