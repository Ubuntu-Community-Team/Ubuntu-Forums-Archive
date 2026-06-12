---
title: "Help needed to restore access to system resources"
date: 2007-03-07
forum: General Help
---

### Post by drpaul on 2007-03-07
I added my primary/only user to the video group [and blundered a little with the commands], and subsequently lost access to sudo.  Then on reboot none of the system administration features that require sudo to access and all access to sound have disappeared.
Hope to get some good suggestions soon.

Paul

EDIT:  I just found out that I killed my group memberships. My only group is now video.  How do I restore all the old groups?
EDIT: Booted from LiveCD and copied group- to group! Restored sudo privaleges. The only remaining delta that I've seen is the normal sound played at login for the user isn't being played.????
EDIT: That last change left the group file with the wrong permissions. Some functions didn't work [like locate]. Fixed permissions with sudo which did work. ????

---

