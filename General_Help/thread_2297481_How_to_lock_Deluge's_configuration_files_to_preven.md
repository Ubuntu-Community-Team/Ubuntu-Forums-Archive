---
title: "How to lock Deluge's configuration files to prevent their modification?"
date: 2015-10-04
forum: General Help
---

### Post by daerragh on 2015-10-04
[COLOR=#111111][FONT=Ubuntu]I'm setting up a seedbox for 3 users on Ubuntu Server 15.04. Each user runs his copy of deluged and deluge-web and has its home directory where deluge's configuration files reside. I optimized the files for speed and now I'd like to lock them to prevent them from any change (so that the users can't change config with deluge-web ui or e.g. windows deluge client).
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]What I tried is:
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I chowned the files by root (and removed world write permissions) but then they just get deleted and swapped by a new configuration file by deluged. I also gave them +i attribute with chattr so that even root cannot modify/delete the files without removing the "i" flag but then deluged just creates a new conf file: core.conf.new which can be modified by deluge-web ui.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]How do I lock the files? Is there any other way to prevent users from modifying deluge's configuration? For now, I'd like to lock core.conf and ltconfig.conf in every users directory and force deluge to use these config files but if there's any other way I'd be happy to hear it.[/FONT][/COLOR]

---

