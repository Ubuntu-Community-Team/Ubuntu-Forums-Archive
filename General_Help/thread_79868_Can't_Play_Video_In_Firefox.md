---
title: "Can't Play Video In Firefox"
date: 2005-10-21
forum: General Help
---

### Post by jlacroix on 2005-10-21
When playing videos under Firefox, such as integrated videos from funnypart.com or holylemon.com, it only plays a few seconds of the video. It's really terrible. The old Mplayer plugin worked, I am assuming the new one is a Totem plugin. It's crap. Can I remove it and use the Mplayer plugin?

Also, 1 out of every 3 times I try to play a video it crashes Firefox. Anyone know how to fix this?

---

### Post by Nomad64 on 2005-10-21
First, you have to make sure that the mplayer plugin for firefox is installed. ```
sudo apt-get mozilla-mplayer
```
Then try to view a video, if it still doesn't work, do the following:
```
sudo mkdir /usr/lib/mozilla-firefox/totemold/
sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.so /usr/lib/mozilla-firefox/totemold/
sudo mv /usr/lib/mozilla-firefox/plugins/libtotem_mozilla.xpt /usr/lib/mozilla-firefox/totemold/
```
(Alternatively, you can just use "rm" commands to delete the files) After you move/delete the files, Firefox will no longer have the capabilities to use totem as a plugin.

Lastly, load up a video. When the "MPlayer plugin" screen appears where the video is loading, right-click on it and select "Configure" from the menu. Setup your video and audio settings. For me, I use x11 for video and ALSA for audio. You may also want to mess around with your cache size and amount of movie to cache as well, depending on your internet connection.

After all of that, refresh the window, and the video _should_ load. Although, my friend and I have found that videos from CNN.com studder...not sure why, since everything else seems to work fine.

Lastly, Firefox 1.0.7 seems to have some stability issues with Ubuntu 5.10, depending. For me, it works just fine and is rock-solid. For my roommate, however, it crashes randomly.

---

### Post by jlacroix on 2005-10-21
Fixed! Thanks so much you're my hero. :)

---

