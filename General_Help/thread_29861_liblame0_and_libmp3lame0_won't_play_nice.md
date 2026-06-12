---
title: "liblame0 and libmp3lame0 won't play nice"
date: 2005-04-26
forum: General Help
---

### Post by mordarageek on 2005-04-26
I have to admit, I just switched from Gentoo about a week and a half ago, so the idea of pre-compiled packages is still kind of new to me (but they sure do install fast!).  The problem that I'm running into is that two of the programs I use most, MythTV's frontend and DVDRip seem to be caught in a dependency war.  MythTV relies on mplayer, and DVDRip really likes transcode.  Moving further down the dependency food chain, mplayer depends on liblame0 and transcode wants to use libmp3lame0.  Every time I try to install one, apt removes the other.  Is there any way to force the installation of both?  Am I stuck installing and removing packages every time I want to use a different program?

Any help would be greatly appreciated.

PS As a side note, I have a script which relies on a feature in mplayer that is broken in 1.0-pre6.  With Gentoo, it was fairly trivial to install mplayer 1.0-pre5.  I can't seem to find an option for that in Synaptic.  What are my options?  Should I just compile from source?  Thanks again.  Aside from these issues, I'm loving Ubuntu!

---

