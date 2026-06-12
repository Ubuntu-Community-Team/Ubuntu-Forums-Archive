---
title: "[SOLVED] Thunderbird profile not shown after Gibbon upgrade"
date: 2007-10-19
forum: General Help
---

### Post by onetb on 2007-10-19
After upgrading to Gibbon last night (and this morning, did everyone take a terribly long time to do it?), I started up thunderbird only to find it asking me to please set up my profile.  I assumed that the upgrade might have overwritten my profiles.ini, since this upgrade came with Thunderbird 2.0.  I have been using Ubuntuzilla for a while to keep my Mozilla stuff up to date.

Anyways, checked the profiles.ini and it still shows that TB should be looking for my profile on the shared partition of my hd.  Here is the read:
```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/Shared/Shared Profiles/Thunderbird Profile/tbprofile

```

I have also tried changing "/media/Shared" to "/dev/hda3", but still TB prompts me to set up a new profile.  Anyone know what the issue is?
Thanks

---

### Post by kellemes on 2007-10-19
If you know where your profilefolder is.. you can also do from the commandline:
```
thunderbird - profilemanager
```
From there you can create an new profile and point it to the profilefolder of your previous install.

---

