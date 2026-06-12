---
title: "pulseaudio system mode broken"
date: 2019-02-26
forum: General Help
---

### Post by Skaperen on 2019-02-26
long long (can't remember when) i asked how to make audio work better and someone suggested system mode which worked great.  i can switch users and the audio started under one user can still be heard when i switch to another user.  this was under 16.04 regularly upgraded.

since then i ran into some hardware issues and needed to switch to another laptop i had of the exact same model and configuration (System 76 Kudu-Pro 16G RAM 2x 1TB disk 120GB SSD).  I tried to image copy the main HD but that failed.  instead of diagnosing why it failed i went ahead and did a full fresh install of Ubuntu 16.04.5 and worked from a USB disk backup to reconfigure many things the same as i had them before.  but pulseaudio was not working and i found error messages about some kind of authentication failure.  i turned system mode, uninstalled (purged) pulseaudio and installed it back.  it worked but it was not in system mode.  i was about to ask about that and got sidetracked converting my system, gracefully a few users at a time, over to Xfce with packages to make it work like in Xubuntu.  but i did *not* do an install of the Xubuntu system.  that's done so i tried getting system mode back on PA.  it seems to run, but switching users does not carry over playing from other users.

does anyone have any idea how to make this work, again?

i log in to multiple users that are members of the "nopasswdlogin" group (so i do not need to re-enter my password every time i switch user, which can sometimes be very rapid.  it would be nice if i can startup music somewhere and keep listening to it as i switch around.  i've been listening to music on YouTube, lately, and prefer to do all my YouTubing from the same user so i get consistent cookie results.  but i want to hear on other userids where i do coding and cloud automation work.

---

