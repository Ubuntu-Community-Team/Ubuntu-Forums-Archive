---
title: "Rhythmbox freezing with shoutcast (and other media questions)"
date: 2005-03-26
forum: General Help
---

### Post by pumaman on 2005-03-26
For some reason rhythmbox freezes whenever I try to open a shoutcast music stream. It gets as far as buffering and displaying the song title current on the station and then just stops. I have to force-quit it in order to open it again. Thus far on this current installation of Ubuntu I have yet to get it working, I have also reinstalled it to no avail.

Actually, I just tried to load it now and it never opened. I saw loading "Music Player" down in the tray, and then nothing happened.

Also, when trying to do anything in Totem I get error messages indicated that it could not play back the file, because an unknown error has occured. I have a few divx video's and other media content I would love to get working in linux. Do I need to download the codec? If so, how do I go about installing it? I did download the Divx codec and compliled it, but I have no idea what to do with it after that point.

Thanks for helping the newbie!

---

### Post by Buffalo Soldier on 2005-03-26
Enable the universe repository and **sudo apt-get update** and **sudo apt-get install gstreamer-plugins**. That's what I always do after a fresh install of Ubuntu.

---

### Post by pumaman on 2005-03-27
Well, that didn't seem to do it. However, thanks for the tip on enabling the universe repositories as it allowed me to get VLC for Ubuntu which I absolutely love on my Mac. Works great in Ubuntu as well!

Thanks for the tip.

---

