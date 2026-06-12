---
title: "Bad mpd problem."
date: 2008-01-19
forum: General Help
---

### Post by Gigamo on 2008-01-19
Alright. This morning I formatted ubuntu and reinstalled. Everything is working fine, but one thing: I can't get mpd working anymore.

I installed mpd from the repositories, edited my /etc/mpd.conf to point to my music directory, and then it started. I just can't get mpd to start anymore, since when I fix the one error it spits out it will spit out another one.

The first error it gave me was that it didn't have permission to my Music directory, so i did a chown 777 on it, and it seems fine now.

Then it couldn't write to my config files, because it didn't have permission to do so (or so it said). I changed the paths in mpd.conf to ~/mpd.log, and that was fixed as well.

Next up was it saying it could not setgid for user "mpd", another Permission Denied. No problem, I changed the user to my username in mpd.conf and that error was gone aswell.

**Edit**: I tried reinstalling it once more, and instead of specifying a music directory in /etc/mpd.conf I created a symlink. However, I cannot get ncmpc to show my music now. Help appreciated.

---

