---
title: "Xubuntu 23.04 (and 22.04) Live Persistence Partially Broken (mkusb-plug)"
date: 2023-09-15
forum: General Help
---

### Post by calinb on 2023-09-15
Background information and summary of my activity:

[LIST=1]
[*]I started out trying to make a Live USB with persistence for a "Andy's Ham Radio Linux" .iso file (based on Xubuntu 22.04). I tried several of the methods available via mkusb, installing the tools to the 22.04 live-only environment and they all failed to result in an image with persistence (live-only, sans persistence, was the result).
[*]
[*]Next I flashed Xubuntu 23.04 to another USB drive, installed the mkusb tools and used mkusb-plug to successfully make an "Andy's" live persistent system. However, many items were not persistent--notably application preferences for the bundled applications and wallpaper selections. (Thunar  View >> List View, xfce4-terminal Edit >> Preferences >> Show Unsafe Paste Dialog, and many others, including wallpaper selection.)
[*]
[*]Finally, I used the 23.04 environment and tools to create an "official" Xubuntu 23.04 live persistent system, but it suffered from incomplete persistence, just like the Andy's system in trial #2, above.
[/LIST]
In my many hours of searching the web, I've found that others have reported similar problems on several websites over the last couple of years or more. Despite my research and own attempts to debug this problem, I still have not found a solution.



Thanks for any assistance,

-Cal

---

### Post by calinb on 2023-09-15
UPDATE:

I found a work-around for this bug. (I wish I'd thought of trying it hours ago. ](*,)) I simply added a new user to the system and the new account on Xubuntu 23.04 appears to enjoy full persistence, as it should! Persistence continues to be partially broken when logged-on to the old default ("xubuntu") account. I checked the list of items in my first post (a small subset of the former persistence failures) and those items all persist through shutdowns and reboots now when logged-on to the new account. :D

I have every reason to believe that all application settings will now be persistent within the new account and the workaround should also work with my Andy's Ham Radio Linux (Xubuntu 22.04) live persistent USB memory too.

I plan to announce my finding on the Andy's Ham Radio Linux Sourceforge page and it would still be very nice if someone who understands how live-persistence works (I don't :() could address the bug. Hopefully this workaround is a clue to discovering the cause!

Cheers,

-Cal

---

### Post by calinb on 2023-09-16
UPDATE 2:

I applied the workaround for the persistence bug (adding a new user) to my 22.04 Andy's Ham Radio Linux system and, as I suspected, it worked! I also disabled the auto-launch on boot of the ubiquity installer by substituting the following code for the contents of /usr/share/ubiquity/start-ubiquity-dm (after making a backup file), which seems to speed booting to a useful desktop considerably.

```

#!/bin/sh
# startup logic of ubiquity-dm, shared between upstart job and systemd unit
exit 0

```

The ubiquity installer is still available via the applications menu (Whisker by default) or the desktop icon launcher (I copied the entire default /home/xubuntu directory to the new user /home directory), if the "run in terminal" box is checked or if the new user name is added to the /etc/sudoers.d/casper file. Either method provides a means to authenticate from the new user's desktop session. Finally, I changed the autologin user to the new user in /etc/lightdm/lightdm.conf:

```

autologin-user=<new_user_name>

```

-Cal

---

