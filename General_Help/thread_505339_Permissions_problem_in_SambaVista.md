---
title: "Permissions problem in Samba/Vista?"
date: 2007-07-20
forum: General Help
---

### Post by DaiLaughing on 2007-07-20
Edgy server accessed by Vista and XP machines.

I've had Samba working for a few months now with a range of shares for individual users or shared directories for all with various permissions.  On the whole these are mapped as three drives so that the users go for D, P and S drivers to access their data/documents, mp3s and photos.

There are two problems which might have the same cause so here they are:

1) On my machine (Vista) I have problems with certain software installs which say "Invalid drive D:" and halt.  If I create a new Vista user with no drive maps and My Documents held locally and log on as that user the installs work fine.  Not all installs are affected.

2) I use a flash drive to hold all my work files and applications (fed up up unreliable network access at work) and I sync that to my home PC as a backup using DSynchronise.  This has worked for months.  Now on running it for the first time since Vista I get told there is an access rights error on D:\Documents which is where I keep my data.

Looking at permissions in Vista they are blank (not unticked just missing) unless you got to Advanced where they show as all ticked for full control.

Samba rights have not changed so I figure it is something to do with Vista.  Just in case I have fiddled with these rights and nothing makes any difference.  On the whole user directories are rwx------ but making them rwxrwxrwx makes no difference.  I have read around but can't find any mention of this problem anywhere.

I did have one other weird problem.  I always create shortcuts to my main drives in th Quick Launch toolbar.  Did this in Vista and only some worked.  C: (Vista system drive) and D: (network Samba drive) worked but P and S did not (also networked in the same way with the same settings apart from smb.conf allowing more user access).  They just ignored me when I pressed them.

Any ideas?

---

