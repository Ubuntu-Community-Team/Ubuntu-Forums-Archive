---
title: "deja-dup-preferences: sudo / gksu / pkexec lead to different results"
date: 2016-11-03
forum: General Help
---

### Post by petwri on 2016-11-03
I am trying to set up a backup strategy to backup everything starting at / using deja dup. Therefore I need to run it as root. When running deja-dup-preferences from the terminal via sudo, I can change settings and include / exclude folders just fine. But when I try to do it from the unity launcher with either gksu or pkexec, the settings for deja dup always get overwritten, changes made are not stored, no matter what I change. It seems as if sudo and gksu / pkexec do different things. Any ideas?

---

### Post by TheFu on 2016-11-04
I don't _know_ the answer, but ... 

sudo doesn't change the HOME directory, so settings are stored **as root** in **YOUR** home directory.  I've never used gksu or pkexec, so my only advice is to check the manpages for how they deal with HOME directory changes.

BTW, I'd avoid using a GUI tool for complete system backups. Try using duplicity (the non-GUI tool on which deja dup is based).  Also be certain to not backup any special files like fifos or named pipes or devices.  There are others not to be backed up too. I haven't used either of those backup tools, so can't provide the specific options.  rdiff-backup has --exclude-special-files option that handles all those funny, not-to-be-backed-up file types. Suspect duplicity does as well.

---

### Post by jerome1232 on 2016-11-04
> **TheFu said:**
> I don't _know_ the answer, but ... 
BTW, I'd avoid using a GUI tool for complete system backups. Try using duplicity (the non-GUI tool on which deja dup is based).  Also be certain to not backup any special files like fifos or named pipes or devices.  There are others not to be backed up too. I haven't used either of those backup tools, so can't provide the specific options.  rdiff-backup has --exclude-special-files option that handles all those funny, not-to-be-backed-up file types. Suspect duplicity does as well.

I'm only seconding the opinion that you should *not* use deja-dup (which is just a gui frontend to duplicity) but rather look at scripting this with duplicity. The community wiki has some info, and a few links to more information.

[https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto)


As an aside:
Personally I see little point in backing up *everything*, I can install my system from scratch in less than an hour. I just backup up my personal files.

---

