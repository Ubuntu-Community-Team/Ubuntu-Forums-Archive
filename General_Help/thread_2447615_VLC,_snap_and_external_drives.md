---
title: "VLC, snap and external drives"
date: 2020-07-22
forum: General Help
---

### Post by JamButty on 2020-07-22
Is there any way to get VLC (snap version) to look at external drives? It can play from the primary HD and primary CD/DVD player but the gui won't let me navigate to my external HD. I understand snap programs in general have this issue, but some have kludges to bridge that. I have found no other articles addressing this.
thanks.

---

### Post by TheFu on 2020-07-22
[https://snapcraft.io/docs/removable-media-interface](https://snapcraft.io/docs/removable-media-interface)
**snap connect vlc:removable-media**
But that only works if the external drives are mounted to "approved" directories.  Mount them anywhere else and it doesn't work.

  # See the available options for a snap package
**snap connections <application-name> **

Or just install the non-snap version of any program causing issues.  IF there isn't one in the repos, you can use flatpak or appimages too.  Flatpaks have some constraints, but those can all be locally overridden, unlike snap constraints.  AppImages don't have any OS constraints, but the technology may fail in a few situations.

---

