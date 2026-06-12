---
title: "[SOLVED] no sound in flash or games"
date: 2008-02-27
forum: General Help
---

### Post by Polygon on 2008-02-27
My sound worked on my previous gutsy install

i reinstall gutsy and now for some reason, i get no sound with flash, or video games like ut2004, or videos in vlc...mplayer...

I however do get sound if i click test in system>prefs>sound and in things like exaile, pidgin, ubuntu start up sound...

ive tried installing libflash-mozplugin or whatever, ive also done asoundconf set-default-card Headset (my headphones) and neither of them have worked

any help?

---

### Post by Polygon on 2008-02-28
im thinking it was a config file issue, as i just reinstalled again, and copied all my config folders (.whatever), but left all the config files there and didnt copy those over.

also after i reinstalled, i went to prefs > sound and set all the things to my sound card, then  i did a*[I] sudo alsoundconf* list[/I] to find the available sound cards, and then a* sudo alsoundconf set-default-card DEFAULTCARD* to set the default card, and then restarted., and youtube and vlc and all that now have sound.

---

