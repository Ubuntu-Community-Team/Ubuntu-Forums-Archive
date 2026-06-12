---
title: "upgrade to GnuCash 2.2.5"
date: 2008-04-28
forum: General Help
---

### Post by ffoeg on 2008-04-28
Hello, I'm running Ubuntu 8, and I've just installed GnuCash via the apt-get install option. This installed version 2.2.4. How do I update this to 2.2.5? The gnucash website doesn't explain this at all. I've tried to get the update via Update Manager of Ubuntu, but no luck. I would appreciate any help.
Thanks

---

### Post by rbmorse on 2008-04-28
Gnucash 2.2.5 is not yet in the repository for download and install. 

At this moment the only way to run Gnucash 2.2.5 on Ubuntu is to build it from source code (which I just did this morning. It's tedious because you have to chase down and install a fairly large number of libraries needed to build Gnucash successfully, but other than that is not particularly difficult.  Takes about an hour, including the time required to study the readme files which is required to achieve a successful build if you haven't built a package from source previously. 

I have a question, though...is there something you know to be in 2.2.5 that is not in 2.2.4 that you absolutely need to have? If not, I strongly recommend staying with 2.2.4 until the packagers get around to adding the new version to repository. Unless, of course, you want to gain some experience in building packages from source, in which case you will find gnucash to be a good learning candidate (K3B is pretty good, too).

---

### Post by ffoeg on 2008-04-28
Thank you for the information. To answer your question, no there's not anything I specifically need in 2.2.5. I would like to learn more the build process though. So I'll give it a shot sooner or later, but it's not an emergency now.
Once 2.2.5 is in the repository, would it be installed via "app-get install" Would I have to unistall the version that's presently installed? Sorry, I'm a Windows user who's trying to make the migration.
Thank you.

---

### Post by oldweasel on 2008-04-28
I'm no Linux Guru myself, but to answer your two questions:

1) Yes, that command would perform the update, another you can use to install most any update is apt-get update. You should be notified at login if there are any changes to the repositories for applications that you are using, so that's a third way ;).

2) The update will usually override the current version, leaving things intact.

Welcome to the club!

---

