---
title: "Default GConf Config, please?"
date: 2007-05-22
forum: General Help
---

### Post by seanUSXIII on 2007-05-22
I made an earlier post, because I think I screwed up my gconf when I installed gnucash. Now my system is horribly slow. [The original post is right here](http://ubuntuforums.org/showthread.php?t=446857).  Any help here is greatly appreciated. I'd like to try to fix this without reinstalling. Can someone post their stock /etc/gconf/2/path file, please?

Thanks,
Sean

---

### Post by aysiu on 2007-05-22
You can reset it by pasting these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
mv ~/.gconf ~/.gconf.old
mv ~/.gconf.d ~/.gconf.d.old
``` You may have to log out and log back in again for the changes to take effect.

---

### Post by seanUSXIII on 2007-05-22
Thank you, I will try that when I get home. :D

---

### Post by loathsome on 2007-05-22
If that doesn't work, here's a default setup ;)

```
######################
# 1. Forced settings #
######################

# Settings forced by the local administrator
xml:readonly:/etc/gconf/gconf.xml.mandatory

# Other forced sources imagined by the local administrator
include /etc/gconf/2/local-mandatory.path


#######################
# 2. User Preferences #
#######################

# mandatory path for sabayon
include "$(HOME)/.gconf.path.mandatory"

# mandatory path for desktop-profiles
include $(ENV_MANDATORY_PATH)

# Other sources imagined by the user
include "$(HOME)/.gconf.path"

# The default storage location, ~/.gconf
# This should be the only readwrite source
xml:readwrite:$(HOME)/.gconf

# default path for sabayon
include "$(HOME)/.gconf.path.defaults"

# default path for desktop-profiles
include $(ENV_DEFAULTS_PATH)


######################
# 3. System defaults #
######################

# Other default sources imagined by the local administrator
include /etc/gconf/2/local-defaults.path

# System administrator's defaults. This source also serves as a legacy
# source for packages not using a recent dh_gconf, or for applications
# installed by hand.
xml:readonly:/etc/gconf/gconf.xml.defaults

# Debian branding, including CDD or packaged branding
xml:readonly:/var/lib/gconf/debian.defaults

# Upstream application defaults
xml:readonly:/var/lib/gconf/defaults
```

**Backup is golden**

---

### Post by seanUSXIII on 2007-05-22
Hmm.. My /etc/gconf/2/path file does not seem to have changed... When I installed gnucash it said it updated the search path. Any clue as to what that could mean? Could it have changed one of the files that /etc/gconf/2/path points to?

One other thing to consider is that I have another user account on here, known as "guestuser". Their account is also affected by this slowness, so wouldn't that rule out things wrong with my ~/.gconf ?

Also, is it possible to completely reset all of gconf? Or does the command that aysiu gave do the whole thing?

Thanks for the help,
Sean

---

### Post by seanUSXIII on 2007-05-23
I tried the above suggestions, with little if any good results. I then decided just to go ahead and reinstall Ubuntu. It doesn't take long, and I took it to a friend's house that has broadband internet. I used automatix to get all my programs set up and in about an hour it was back to its original state!

Thanks for the help!
Sean

---

