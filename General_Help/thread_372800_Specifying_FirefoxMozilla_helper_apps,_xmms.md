---
title: "Specifying Firefox/Mozilla helper apps, xmms"
date: 2007-02-28
forum: General Help
---

### Post by 999alfred on 2007-02-28
I am trying to get firefox/mozilla to use xmms as a helper app when playing streams from shoutcast, *.pls, and mpg3 files, *.mp3.
I downloaded xmms package and it works. But, In firefox I go to Edit->preferences->Content the apps section is empty and no way to add one. Only edit and remove and it says something about Previously downloaded file type are remebered". 
Plus, when I do try to stream form Shoutcast the "Music Player" app pops up, buut no playing.

So, how do I specify xmms for .pls and .mp3 in firefox/mozilla?

Why did they change it from the 1.7 way?

tj

---

### Post by Wartooth on 2007-02-28
I also just downloaded xmms today in order to try to use Live365.  I'd like to know how to specify it in Firefox as well, since I haven't gotten xmms to work with L365 just yet.

---

### Post by mcduck on 2007-02-28
type 'about:config' in the address bar, find the key 'browser.download.hide_plugins_without_extensions' and toggle it's value to 'false'. Now you should be able to change the app to whatever you want. (look for 'MP3 audio (streamed)')

---

